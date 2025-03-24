# First_Order_Logic
1. Bigger Than
Fakta
bigger(gajah, kuda). → Gajah lebih besar dari kuda.
bigger(kuda, keledai). → Kuda lebih besar dari keledai.
bigger(keledai, anjing). → Keledai lebih besar dari anjing.
bigger(keledai, monyet). → Keledai lebih besar dari monyet.

Aturan
is_bigger(X, Y) :- bigger(X, Y).
→ X lebih besar dari Y jika terdapat fakta bigger(X, Y).
is_bigger(X, Y) :- bigger(X, Z), is_bigger(Z, Y).
→ X lebih besar dari Y jika X lebih besar dari Z, dan Z lebih besar dari Y (hubungan transitif).

2. Silsilah Slamet
Fakta
ayah(slamet, amin). → Slamet adalah ayah dari Amin.
ayah(slamet, anang). → Slamet adalah ayah dari Anang.
ayah(amin, badu). → Amin adalah ayah dari Badu.
ayah(amin, budi). → Amin adalah ayah dari Budi.
ayah(anang, didi). → Anang adalah ayah dari Didi.
ayah(anang, dadi). → Anang adalah ayah dari Dadi.

Aturan
is_ayah(X, Y) :- ayah(X, Y).
→ X adalah ayah dari Y jika terdapat fakta ayah(X, Y).
is_anak(Y, X) :- ayah(X, Y).
→ Y adalah anak dari X jika terdapat fakta ayah(X, Y).
is_sodara(Y, Z) :- ayah(X, Y), ayah(X, Z).
→ Y dan Z adalah saudara jika memiliki ayah yang sama.
is_kakek(X, Z) :- ayah(X, Y), is_ayah(Y, Z).
→ X adalah kakek dari Z jika X adalah ayah dari Y, dan Y adalah ayah dari Z.

3. Anak Suka Permen
Fakta
Anak yang merupakan anak ibu:
anakIbu(andi).
anakIbu(budi).
anakIbu(cika).
anakIbu(dani).
anakIbu(emil).
not(anakIbu(fadil)). (Fadil bukan anak ibu.)
Anak yang suka permen:
sukaPermen(andi).
sukaPermen(budi).
sukaPermen(cika).
not(sukaPermen(dani)).
not(sukaPermen(emil)).

Aturan
siapa_saja(X):- anakIbu(X).
→ Menampilkan siapa saja yang merupakan anak ibu.
dapatPermen(X):- anakIbu(X), sukaPermen(X).
→ Anak ibu yang suka permen akan mendapat permen.
dapatUang(X):- anakIbu(X), not(sukaPermen(X)).
→ Anak ibu yang tidak suka permen akan mendapat uang.
tidakmendapatkanApaApa(X):- not(anakIbu(X)).
→ Jika seseorang bukan anak ibu, dia tidak mendapat apa-apa.

4. Silsilah Keluarga David(Lengkap)
Fakta
ayah(david, liza). → David adalah ayah Liza.
ibu(amy, liza). → Amy adalah ibu Liza.
Fakta serupa berlaku untuk individu lain.

Aturan
is_anakAyah(X, Y) :- ayah(Y, X).
→ X adalah anak dari ayah Y.
is_anakIbu(X, Y) :- ibu(Y, X).
→ X adalah anak dari ibu Y.
is_sodara(Y, Z) :- ayah(X, Y), ayah(X, Z), Y\=Z.
→ Y dan Z adalah saudara jika memiliki ayah yang sama tetapi bukan diri mereka sendiri.
is_orangtua(X, Y) :- ayah(X, Y).
is_orangtua(X, Y) :- ibu(X, Y).
→ X adalah orang tua dari Y jika X adalah ayah atau ibu dari Y.
is_kakek(X, Z) :- ayah(X, Y), is_orangtua(Y, Z).
→ X adalah kakek dari Z jika X adalah ayah dari Y, dan Y adalah orang tua dari Z.
is_nenek(X, Z) :- ibu(X, Y), is_orangtua(Y, Z).
→ X adalah nenek dari Z jika X adalah ibu dari Y, dan Y adalah orang tua dari Z.
