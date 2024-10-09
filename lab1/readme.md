# **Lucrare de laborator nr. 1. Bazele HTTP**

### *Sarcina nr. 1. Analiza cererilor HTTP*

1. Accesați site-ul http://sandbox.usm.md/login.

![login](https://res.cloudinary.com/dko0nafa9/image/upload/v1728434363/Screenshot_1_mfp234.png)

2. Deschideți fila Network în instrumentele pentru dezvoltatori ale browserului.

![network](https://res.cloudinary.com/dko0nafa9/image/upload/v1728431311/Screenshot_2_bhftgq.png)

3. Introduceți date incorecte pentru autentificare (de exemplu, username: student, password: studentpass).

![dateincorecte](https://res.cloudinary.com/dko0nafa9/image/upload/v1728431637/Screenshot_3_ix0p9l.png)

4. Analizați cererile care au fost trimise către server.
5. Răspundeți la următoarele întrebări:
   + Ce metodă HTTP a fost utilizată pentru a trimite cererea?
      > Metoda HTTP utilizată: Metoda POST este folosită pentru autentificare, deoarece sunt trimise date confidențiale.
   + Ce anteturi au fost trimise în cerere?
      > accept: /
      > 
      >  accept-encoding: gzip, deflate
      > 
      >  accept-language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
      > 
      >  connection: keep-alive
      > 
      >  content-length: 37
      > 
      >  content-type: application/x-www-form-urlencoded; charset=UTF-8
      > 
      >  dnt: 1
      > 
      >  host: sandbox.usm.md
      > 
      >  origin: http://sandbox.usm.md
      > 
      >  referer: http://sandbox.usm.md/login/
      > 
      >  user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
      > 
      >  x-requested-with: XMLHttpRequest
   + Ce parametri au fost trimiși în cerere?
     > username=student&password=studentpass
   + Ce cod de stare a fost returnat de server?
     > Cod de stare returnat: Codul de stare 401 Unauthorized încearcănd să te autentifici cu date incorecte.
   + Ce anteturi au fost trimise în răspuns?
     > connection: keep-alive
     > 
     > content-type: text/plain;charset=UTF-8
     > 
     > date: Wed, 09 Oct 2024 00:11:54 GMT
     > 
     > server: nginx/1.24.0 (Ubuntu)
     > 
     > transfer-encoding: chunked, |
6. Repetați pașii 3-5, introducând date corecte pentru autentificare (username: admin, password: password).

![datecorecte](https://res.cloudinary.com/dko0nafa9/image/upload/v1728433279/Screenshot_4_gaj8vw.png)
   + Ce metodă HTTP a fost utilizată pentru a trimite cererea?
      > Metoda HTTP utilizată: Metoda POST este folosită pentru autentificare, deoarece sunt trimise date confidențiale.
   + Ce anteturi au fost trimise în cerere?
      > accept: /
      > 
      >  accept-encoding: gzip, deflate
      > 
      >  accept-language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7
      > 
      >  connection: keep-alive
      > 
      >  content-length: 32
      > 
      >  content-type: application/x-www-form-urlencoded; charset=UTF-8
      > 
      >  dnt: 1
      > 
      >  host: sandbox.usm.md
      > 
      >  origin: http://sandbox.usm.md
      > 
      >  referer: http://sandbox.usm.md/login/
      > 
      >  user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
      > 
      >  x-requested-with: XMLHttpRequest
   + Ce parametri au fost trimiși în cerere?
     > username=admin&password=password
   + Ce cod de stare a fost returnat de server?
     > Cod de stare returnat: Codul de stare 200 OK pentru autentificare reușită.
   + Ce anteturi au fost trimise în răspuns?
     > connection: keep-alive
     > 
     > content-type: text/plain;charset=UTF-8
     > 
     > date: Wed, 09 Oct 2024 00:11:54 GMT
     > 
     > server: nginx/1.24.0 (Ubuntu)
     > 
     > transfer-encoding: chunked

---
### *Sarcina nr. 2. Crearea cererilor HTTP*  
1. Scrieți o cerere de tip GET către server la adresa http://sandbox.com, indicând în antetul User-Agent numele și prenumele dvs.
  ```
  curl -X GET http://sandbox.com -H "User-Agent: Andrei Zama"
  ```
2. Scrieți o cerere de tip POST către server la adresa http://sandbox.com/cars, indicând în corpul cererii următorii parametri:
   + make: Toyota
   + model: Corolla
   + year: 202
```
curl -X POST http://sandbox.com/cars -d "make=Toyota&model=Corolla&year=2020"
```
3. Scrieți o cerere de tip PUT către server la adresa http://sandbox.com/cars/1, indicând în antetul User-Agent numele și prenumele dvs., în antetul Content-Type valoarea application/json, iar în corpul cererii următorii parametri:
```
{
    "make": "Toyota",
    "model": "Corolla",
    "year": 2021
}
```
```
curl -X PUT http://sandbox.com/cars/1 -H "User-Agent: Andrei Zama" -H "Content-Type: application/json" -d '{"make": "Toyota", "model": "Corolla", "year": 2021}'
```
4. Scrieți unul dintre posibilele răspunsuri ale serverului la cererea anterioară.
```
POST /cars HTTP/1.1
Host: sandbox.com
Content-Type: application/json
User-Agent: John Doe
model=Corolla&make=Toyota&year=2020
```
   + Raspunsul posibil:
     ```
      HTTP/1.1 200 OK
      Content-Type: application/json
      {"status": "success", "message": "Car updated successfully"}
     ```
   + Presupuneți situațiile în care serverul poate returna codurile de stare HTTP 200, 201, 400, 401, 403, 404, 500:

     > 200 OK: Cererea a fost procesată cu succes, iar resursa a fost returnată.
     > 
     > 201 Created: Resursa a fost creată cu succes (de exemplu, în urma unei cereri POST).
     > 
     > 400 Bad Request: Cererea are erori de sintaxă sau parametrii sunt incorecți.
     > 
     > 401 Unauthorized: Accesul la resursă este interzis din cauza lipsei autentificării sau autentificare eșuată.
     > 
     > 403 Forbidden: Accesul la resursă este interzis, chiar dacă autentificarea a fost realizată corect.
     > 
     > 404 Not Found: Resursa solicitată nu a fost găsită pe server.
     > 
     > 500 Internal Server Error: A apărut o eroare la server în timpul procesării cererii.
     >
5. Scrieți o cerere de tip DELETE la alegerea dvs. și să explicați de ce, în acest caz, este potrivit să utilizați metoda DELETE.
   ```
   curl -X DELETE http://sandbox.com/cars/1
   ```
   > Această cerere întrebuințează metoda DELETE pentru a șterge o mașină cu ID-ul 1. Metoda DELETE este potrivită în acest caz deoarece se dorește eliminarea unei resurse de pe server.

---

### *Sarcina nr. 3. Sarcina suplimentară. HTTP_Quest*

1. Trimiteți o cerere de tip POST către server la adresa http://sandbox.usm.md/quest, indicând în antetul User-Agent numele și prenumele dvs. (De exemplu, User-Agent: John Doe).
   ```
   POST /quest HTTP/1.1
   Host: sandbox.usm.md
   User-Agent: John Doe
   ```
   curl:
   ```
   curl -X POST http://sandbox.usm.md/quest -H "User-Agent: John Doe"
   ```
2. Urmați instrucțiunile de pe server, îndeplinindu-le în ordine.
3. La finalul quest-ului, vi se va afișa un cuvânt secret, pe care va trebui să-l includeți în raport.
   > secret: CjkdGkpxTV1iUVlGVw==

---
### *Intrebări de autoevaluare*

1. Ce este protocolul HTTP?
   > (Hypertext Transfer Protocol) este un protocol de comunicație care definește modul în care informațiile sunt transferate între un client (de exemplu, un browser) și un server web.
3. Pentru ce folosim antetul User-Agent?
   > Antetul User-Agent este folosit pentru a identifica aplicația client (browser-ul sau alt instrument de rețeat) către server, astfel încât serverul să poată returna informații personalizate.
5. Care este diferența dintre metodele PUT și PATCH?
   > PUT încălocuiește întreaga resursă de la server cu datele furnizate, în timp ce PATCH actualizează doar anumite porțiuni ale resursei fără a o încălocui în totalitate.

---

### *Laboratorul realizat de: Zamă Andrei*
#### *Grupa: IAFR2101RO*
[Telegram](https://t.me/twodloly)
