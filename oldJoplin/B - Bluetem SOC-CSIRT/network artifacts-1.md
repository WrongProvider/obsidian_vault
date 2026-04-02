network artifacts

tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap

&nbsp;

![211d0f909090a83b480d1d9ee39c696e.png](../_resources/211d0f909090a83b480d1d9ee39c696e-1.png)