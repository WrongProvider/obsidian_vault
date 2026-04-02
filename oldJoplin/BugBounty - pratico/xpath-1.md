xpath

pelo o que eu entendi é bem igual ao SQLi 

os caras montam uma query via XML e essa query por não ter parametrizacao ela fica vulneravel a ataques como 1==1

```
Username: blah' or 1=1 or 'a'='a
Password: blah

FindUserXPath becomes //Employee[UserName/text()='blah' or 1=1 or
        'a'='a' And Password/text()='blah']

Logically this is equivalent to:
        //Employee[(UserName/text()='blah' or 1=1) or
        ('a'='a' And Password/text()='blah')] 
```

/html/body/div\[2\]

https://owasp.org/www-community/attacks/XPATH_Injection