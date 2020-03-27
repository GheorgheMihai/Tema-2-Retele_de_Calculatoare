# Tema-2-Retele_de_Calculatoare (din Laborator)


## Exerciții HTTP

### DNS-over-HTTPS

Modulul `doh.py` definește o funcție care utilizează serviciul de DNS-over-HTTPS
de la Cloudflare pentru a afla adresa IP a unui domeniu.

![Adresa DNS pentru fmi.unibuc.ro](https://user-images.githubusercontent.com/48345929/77791050-9d89f900-706e-11ea-97ce-3f7e7fee4592.png)

### Servirea cererilor de tip `GET` prin Flask

Am rulat Flask în container, și am deschis pagina în browser.

![Pagina primită în browser](https://user-images.githubusercontent.com/48345929/77791178-db871d00-706e-11ea-8956-f9bdbc560f0b.png)
![Mesajele de pe server](https://user-images.githubusercontent.com/48345929/77791183-dd50e080-706e-11ea-90af-93a901aeb31d.png)

### Cereri de tip `POST`

Am modificat server-ul să ridice la pătrat numărul primit ca JSON prin POST.

![Cerere `POST` prin `curl`](https://user-images.githubusercontent.com/48345929/77791186-df1aa400-706e-11ea-8ab8-1b9cdb2729c8.png)
![Ridicarea la pătrat pe rețea](https://user-images.githubusercontent.com/48345929/77791188-dfb33a80-706e-11ea-9bfe-b0c808efc9b6.png)

### `httpbin`

Am scris un script de Python care face cereri HTTP cu diferite verbe.

![Cereri diverse la httpbin](https://user-images.githubusercontent.com/48345929/77791283-01acbd00-706f-11ea-88f5-25aff12a9552.png)

## Exerciții UDP

### Server și client pe aceeași mașină

Am rulat client-ul și server-ul de UDP pe același calculator.

![Server și client care comunică peste UDP](https://user-images.githubusercontent.com/48345929/77791835-0160f180-7070-11ea-834a-c08a301e4a69.png)

### Server și client în containere diferite

Am modificat client-ul și server-ul ca să poată rula fiecare din container-ul lui.

![Server și client în containere diferite](https://user-images.githubusercontent.com/48345929/77791843-032ab500-7070-11ea-8e9e-8c5d54891265.png)

### Comunicare UDP vizualizată prin `tcpdump`

![Un mesaj transmis înainte și înapoi prin UDP](https://user-images.githubusercontent.com/48345929/77791845-045be200-7070-11ea-8d11-a4d237b8b2ff.png)

### Accesez server-ul de UDP din container de pe host

Am modificat `docker-compose.yml` ca să pot accesa port-ul `10000` de pe
host.

![Un mesaj transmis de pe host pe container și înapoi](https://user-images.githubusercontent.com/48345929/77791849-058d0f00-7070-11ea-9c1b-6829940edc8c.png)

## Exerciții TCP

Exercițiile 1-3 au mers la UDP.

### Mesaj transmis prin TCP

![Transmiterea unui mesaj de la client la server prin TCP](https://user-images.githubusercontent.com/48345929/77793119-38380700-7072-11ea-8e7c-4bcedcd20416.png)

### 3-way Handshake

Am modificat client-ul să transmită un singur byte, și server-ul să accepte un singur byte și să nu-l retransmită.
Mai jos sunt pachete schimbate între client și server.

```
IP 172.21.0.2.59128 > 172.21.0.3.10000: Flags [S], seq 2472923734, win 64240, options [mss 1460,sackOK,TS val 3722954303 ecr 0,nop,wscale 7], length 0
IP 172.21.0.3.10000 > 172.21.0.2.59128: Flags [S.], seq 3967639458, ack 2472923735, win 65160, options [mss 1460,sackOK,TS val 4044896210 ecr 3722954303,nop,wscale 7], length 0
IP 172.21.0.2.59128 > 172.21.0.3.10000: Flags [.], ack 3967639459, win 502, options [nop,nop,TS val 3722954303 ecr 4044896210], length 0
IP 172.21.0.2.59128 > 172.21.0.3.10000: Flags [P.], seq 2472923735:2472923736, ack 3967639459, win 502, options [nop,nop,TS val 3722955304 ecr 4044896210], length 1
IP 172.21.0.3.10000 > 172.21.0.2.59128: Flags [.], ack 2472923736, win 510, options [nop,nop,TS val 4044897211 ecr 3722955304], length 0
IP 172.21.0.2.59128 > 172.21.0.3.10000: Flags [F.], seq 2472923736, ack 3967639459, win 502, options [nop,nop,TS val 3722955304 ecr 4044897211], length 0
IP 172.21.0.3.10000 > 172.21.0.2.59128: Flags [.], ack 2472923737, win 510, options [nop,nop,TS val 4044897251 ecr 3722955304], length 0
IP 172.21.0.3.10000 > 172.21.0.2.59128: Flags [F.], seq 3967639459, ack 2472923737, win 510, options [nop,nop,TS val 4044898212 ecr 3722955304], length 0
IP 172.21.0.2.59128 > 172.21.0.3.10000: Flags [.], ack 3967639460, win 502, options [nop,nop,TS val 3722956305 ecr 4044898212], length 0
```
