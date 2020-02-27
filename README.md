# objetivo

Este é um exemplo de acesso entre duas stacks diferentes, onde os serviços em `meuprojeto2` consomem serviço existente na stack `meuprojeto1`


# comandos

```
cd meuprojeto1
docker-compose up -d
cd ../meuprojeto2
docker-compose up
```

Nos logs aparecerão o resultado do comando ping, mostrando resposta da rede do meuprojeto1, e o teste de acesso a API meuservico1 com o comando curl semelhante a:


```
Starting meuprojeto2_ping_1_e52cf69a11c4          ... done
Attaching to meuprojeto2_ping_1_e52cf69a11c4, meuprojeto2_testeacesso_1_8c7f33f8e89a
testeacesso_1_8c7f33f8e89a |   % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
ping_1_e52cf69a11c4 | ping nomedoservico1 every 10 sec
ping_1_e52cf69a11c4 | PING nomedoservico1 (10.111.4.2): 56 data bytes
ping_1_e52cf69a11c4 | 64 bytes from 10.111.4.2: seq=0 ttl=64 time=0.082 ms
ping_1_e52cf69a11c4 | 
ping_1_e52cf69a11c4 | --- nomedoservico1 ping statistics ---
ping_1_e52cf69a11c4 | 1 packets transmitted, 1 packets received, 0% packet loss
ping_1_e52cf69a11c4 | round-trip min/avg/max = 0.082/0.082/0.082 ms
testeacesso_1_8c7f33f8e89a |                                  Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0*   Trying 10.111.4.2:5050...
testeacesso_1_8c7f33f8e89a | * TCP_NODELAY set
testeacesso_1_8c7f33f8e89a | * Connected to nomedoservico1 (10.111.4.2) port 5050 (#0)
testeacesso_1_8c7f33f8e89a | > GET /test/1 HTTP/1.1
testeacesso_1_8c7f33f8e89a | > Host: nomedoservico1:5050
testeacesso_1_8c7f33f8e89a | > User-Agent: curl/7.68.0-DEV
testeacesso_1_8c7f33f8e89a | > Accept: */*
testeacesso_1_8c7f33f8e89a | > 
testeacesso_1_8c7f33f8e89a | * Mark bundle as not supporting multiuse
testeacesso_1_8c7f33f8e89a | < HTTP/1.1 200 OK
testeacesso_1_8c7f33f8e89a | < content-type: text/plain;charset=UTF-8
testeacesso_1_8c7f33f8e89a | < content-length: 63
testeacesso_1_8c7f33f8e89a | < 
testeacesso_1_8c7f33f8e89a | /:path1/:path2 - Hello to test/1 ! Host:3bfbb35ec6b2/10.111.4.2{ [63 bytes data]
100    63  100    63    0     0    516      0 --:--:-- --:--:-- --:--:--   516
testeacesso_1_8c7f33f8e89a | * Connection #0 to host nomedoservico1 left intact
meuprojeto2_testeacesso_1_8c7f33f8e89a exited with code 0
```
