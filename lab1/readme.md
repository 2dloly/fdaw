# **Lucrare de laborator nr. 1. Bazele HTTP**

*Sarcina nr. 1. Analiza cererilor HTTP*

1. Accesați site-ul http://sandbox.usm.md/login.

![login](https://res.cloudinary.com/dko0nafa9/image/upload/v1728430134/Screenshot_1_gfrxuw.png)

2. Deschideți fila Network în instrumentele pentru dezvoltatori ale browserului.

![network](https://res.cloudinary.com/dko0nafa9/image/upload/v1728431311/Screenshot_2_bhftgq.png)

3. Introduceți date incorecte pentru autentificare (de exemplu, username: student, password: studentpass).

![dateincorecte](https://res.cloudinary.com/dko0nafa9/image/upload/v1728431637/Screenshot_3_ix0p9l.png)

4. Analizați cererile care au fost trimise către server.
5. Răspundeți la următoarele întrebări:
   + Ce metodă HTTP a fost utilizată pentru a trimite cererea?
      > Metoda HTTP utilizată: De obicei, metoda POST este folosită pentru autentificare, deoarece sunt trimise date confidențiale.
   + Ce anteturi au fost trimise în cerere?
      > accept: / |
        accept-encoding: gzip, deflate, |
        accept-language: ru-RU,ru;q=0.9,en-US;q=0.8,en;q=0.7, |
        connection: keep-alive, |
        content-length: 37, |
        content-type: application/x-www-form-urlencoded; charset=UTF-8, |
        dnt: 1, |
        host: sandbox.usm.md, |
        origin: http://sandbox.usm.md, |
        referer: http://sandbox.usm.md/login/, |
        user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36, |
        x-requested-with: XMLHttpRequest, |
   + Ce parametri au fost trimiși în cerere?
     > username=student&password=studentpass
   + Ce cod de stare a fost returnat de server?
     > Cod de stare returnat: Codul de stare 401 Unauthorized încearcănd să te autentifici cu date incorecte.
   + Ce anteturi au fost trimise în răspuns?
     > connection: keep-alive, | content-type: text/plain;charset=UTF-8, | date: Wed, 09 Oct 2024 00:11:54 GMT , | server: nginx/1.24.0 (Ubuntu) , | transfer-encoding: chunked, |
6. Repetați pașii 3-5, introducând date corecte pentru autentificare (username: admin, password: password).

![datecorecte](https://res.cloudinary.com/dko0nafa9/image/upload/v1728433279/Screenshot_4_gaj8vw.png)
