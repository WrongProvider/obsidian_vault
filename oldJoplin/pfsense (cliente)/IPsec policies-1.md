IPsec configuration

FILIAL - Anhanguera - AmericaNet

key exchange - IKEv1

phase 1

encryption algorithm - 3DES  

HASH - SHA256

DHgroup - 14 (2048 bit)

key-life = 28800

##esses valores abaixo estão em branco, ou seja, ta no padrão.

re-key-margin = 25920

rand-time = 2880 (no sophos fica em porcentagem, no pfsense esse valor é subtraido pelo re-key-margin)

(DPD) dead peer detection = habilitado