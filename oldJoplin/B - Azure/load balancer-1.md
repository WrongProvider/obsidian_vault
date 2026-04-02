load balancer

&nbsp;

git clone https://github.com/MicrosoftDocs/mslearn-improve-app-scalability-resiliency-with-load-balancer.git  
cd mslearn-improve-app-scalability-resiliency-with-load-balancer

&nbsp;

bash create-high-availability-vm-with-sets.sh learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e

&nbsp;

az network public-ip create --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --allocation-method Static --name myPublicIP

az network lb create --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --name myLoadBalancer --public-ip-address myPublicIP --frontend-ip-name myFrontEndPool --backend-pool-name myBackEndPool

az network lb probe create --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --lb-name myLoadBalancer --name myHealthProbe --protocol tcp --port 80 

az network lb rule create --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --lb-name myLoadBalancer --name myHTTPRule --protocol tcp --frontend-port 80 --backend-port 80 --frontend-ip-name myFrontEndPool --backend-pool-name myBackEndPool --probe-name myHealthProbe

az network nic ip-config update --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e--nic-name webNic1 --name ipconfig1 --lb-name myLoadBalancer --lb-address-pools myBackEndPool

az network nic ip-config update --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --nic-name webNic2 --name ipconfig1 --lb-name myLoadBalancer --lb-address-pools myBackEndPool

echo http://$(az network public-ip show --resource-group learn-90f7af79-67f4-42ce-9bb4-2abc19cbf29e --name myPublicIP --query ipAddress --output tsv)