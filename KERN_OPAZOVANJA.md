# KERN opazovanje lokalnih modelov

Od 12. 10. 2026 KERN zbira opazovanja lastnikovih preizkusov lokalnih
modelov. Lastnik in Nika pripravljata modele enega za drugim; lastnik
sporoča rezultate, KERN pa prebere pripadajoče dnevnike in opiše izmerjeni
potek. Namen je zbrati primerljive primere pred skupnim načrtovanjem
boljših različic bridgea.

## Meje opazovanja

KERN v tej fazi ne spreminja modelov, profilov, zaganjalnikov, bridgea ali
produkcijske kode. Ne zaganja novih modelnih testov in ne ustavlja sej.
Dosedanji načrt detektorja treh ponovljenih blokov je odložen; ni potrjena
splošna rešitev za vedenje vseh modelov.

Poročilo lastnika, dejstva iz dnevnika in odprta vprašanja ostanejo ločeni.
Opazovanje ne postane sklep o vzroku, kakovosti modela ali priporočilo za
popravek. Rezultata ene seje ne posplošujemo na druge modele. Razlago in
spremembe oblikujemo skupaj šele po zadostnem naboru preizkusov.

## Podatki posameznega preizkusa

Za vsak preizkus zapišemo razpoložljive podatke; manjkajočih ne ugibamo:

- datum in čas z navedbo časovnega pasu;
- modelni tag oziroma digest in uporabljeni profil;
- ID seje, delovna mapa in povezave do dnevnikov;
- naloga in pričakovano vedenje, kot ju določi lastnik;
- lastnikovo poročilo o dejanskem rezultatu;
- časovno zaporedje sporočil, orodnih klicev, rezultatov in zaključkov;
- izmerjene ponovitve z enoto, razponom in metodo štetja;
- poraba vhodnih, predpomnjenih in izhodnih tokenov, ločeno od konteksta;
- dogodki kompakcije, prekinitve in spremembe stanja cilja;
- omejitve opazovanja in vprašanja za naslednji skupni pregled.

Ne zapisujemo skrivnosti ali celotnih občutljivih vsebin. Dokazila praviloma
ostanejo v izvornih dnevnikih; tukaj zapišemo povezave in potrebne odlomke.

## Zapisi preizkusov

Novi zapisi se dodajajo po prejemu lastnikovega poročila in določitvi
pripadajoče seje. Pretekle ugotovitve se ne prenesejo kot nova opazovanja
brez ponovnega pregleda vira.

### Preizkus 001 Gemma 12B in ponavljanje znotraj odgovora

To je začetna osnova za primerjavo naslednjih preizkusov. Izvorni zapis je
bil ponovno prebran 12. 10. 2026; model ni bil ponovno zagnan.

#### Lastnikovo poročilo

Lastnik je opozoril na ponavljanje in zahteval iskanje natančne ponovljive
številke oziroma vzorca v komunikaciji. Po meritvi je opisal štetje istih
ali približno istih blokov. Poznejša odločitev je opazovanje več preizkusov
pred skupnim načrtovanjem bridgea; ta zapis ne aktivira varovalke.

#### Identiteta in vir

- Model v metapodatkih: `mikrofix-gemma4-12b-focused-65k`.
- Provider: `ollama-local`; Codex različica: `0.160.0`.
- Seja: `01a13140-53aa-7471-86ac-dafd8aca44b7`.
- Začetek seje: 12. 10. 2026 ob 19:54:21 po Europe/Ljubljana.
- Delovna mapa: `/home/mikrofix/MikroFIX_Service_v30_R9_LINUX_DEV`.
- Obrat: `01a13143-b43d-7863-9059-15c9c0c2a33e`.
- Sporočilo: `msg_217971`.
- Čas zapisa sporočila: 20:12:51.973 po Europe/Ljubljana,
  v viru `2026-10-12T18:12:51.973Z`. To ni čas vsake posamezne ponovitve.
- [Izvorni dnevnik in celotno sporočilo, vrstica 122](/home/mikrofix/.gemma12-codex/sessions/2026/10/12/rollout-2026-10-12T19-54-21-01a13140-53aa-7471-86ac-dafd8aca44b7.jsonl:122).

#### Izmerjeno ponavljanje

Celotno shranjeno besedilo sporočila ima 75593 znakov in 2155 vrstic,
če vrstice štejemo z razcepom po LF. V njem je preverjen niz
**31 zaporednih, nepokrivajočih se in popolnoma identičnih ciklov**.

Vsak izbrani cikel meri 1530 znakov, 1530 bajtov UTF-8, 45 vrstičnih
korakov in 159 besed, štetih po presledkih. Velikost vključuje zaključni LF.
SHA-256 celotnega cikla:
`9229c1acdea5f488cab7ace6b845dab4c59b0e4c2d153ce909f4681cd691d632`.

Začetni odmiki v besedilu, šteti od nič:

```text
26829 28359 29889 31419 32949 34479 36009 37539
39069 40599 42129 43659 45189 46719 48249 49779
51309 52839 54369 55899 57429 58959 60489 62019
63549 65079 66609 68139 69669 71199 72729
```

Vseh 30 razmikov med temi začetki je natanko 1530 znakov. Preverjeni
neprekinjeni niz obsega 47430 bajtov. To je število v izbranem razponu,
ne trditev, da drugod v sporočilu ni dodatnih ponovitev ali delnih ciklov.

Cikel vsebuje predlagani diff za `tax_profiles_v32`, komentar o zamiku
vrstice `invoices_v32`, besedilo »Let's try.« in ponoven uvod v isti diff.
Za izhodišče je izbrana vrstica `+++ mikrofix_server/models.py`;
besedilo cikla se konča z `--- mikrofix_server/models.py` in LF.
To je ponavljanje besedila, ne 31 izvedenih orodnih klicev.

#### Način ponovitve meritve

Iz JSONL preberemo vrstico 122, vzamemo `payload.content`, združimo polja
`text` z LF in besedilo razcepimo po LF. Indeksi so od nič. Osnovni cikel
je `lines.slice(724, 769).join("\n") + "\n"`. Nato od indeksa 724
naprej v korakih po 45 primerjamo celotne naslednje cikle z osnovnim,
brez normalizacije presledkov, črk ali ločil. Dobimo 31 enakih ciklov.
Dolžino UTF-8 merimo ločeno od dolžine znakov; tu sta enaki, ker je
preverjeni cikel ASCII. Meja izbranega cikla ni univerzalna meja bloka.

#### Poraba pri istem odgovoru

[Zapis porabe, vrstica 123](/home/mikrofix/.gemma12-codex/sessions/2026/10/12/rollout-2026-10-12T19-54-21-01a13140-53aa-7471-86ac-dafd8aca44b7.jsonl:123)
za odziv `resp_387754` navaja 39743 vhodnih tokenov, od tega 39283
predpomnjenih, ter 25790 izhodnih tokenov. Skupaj je navedenih 65533
tokenov za odziv. Predpomnjeni tokeni so del vhodnih, ne dodatna poraba.
Te številke niso meritev tokenov posameznega 1530-bajtnega cikla niti
zasedenost kontekstnega okna.

#### Omejitve in odprta vprašanja

Ta zapis obravnava starejšo sejo, ne poznejše seje
`01a13161-5b16-7471-bc87-c5c6022cd90b`. Oblik ponavljanja ne združujemo.
JSONL vsebuje končno besedilo; iz njega ne določimo meja pretočnih koščkov,
hitrosti vsakega cikla ali njegove točne tokenizacije. Približna podobnost
blokov tu ni merjena. Vzrok ponavljanja in uporabnost tega vzorca pri
drugih preizkusih ostajata odprta. Runtime in produkcijska koda pri tej
ponovni meritvi nista bila spremenjena.

## Referenčna navodila: review-agent in upravljanje Goals

Naša [definicija review-agent (line 1)](/home/mikrofix/.gemma12-codex/skills/.system/review-agent/SKILL.md:1) zahteva:

- prebrati ustrezne `AGENTS.md`;
- pregledati celoten diff in potrebno okoliško kodo;
- preveriti teste ter mesta uporabe;
- poročati o konkretnih, dokazljivih napakah, uvedenih s spremembo;
- ničesar popravljati, objavljati ali delegirati drugemu agentu.

**Njegov končni cilj je pregled z uporabnimi ugotovitvami**, razvrščenimi P0–P3, ali `No findings.`, nato kratka ocena in pomembne vrzeli preverjanja. Ni namenjen implementaciji popravkov.

[Zasnova Goals](https://developers.openai.com/cookbook/examples/codex/using_goals_in_codex)

Upravljanje:

| Vnos | Namen |
| --- | --- |
| `/goal <cilj>` | Postavi cilj |
| `/goal` | Pokaže trenutno stanje |
| `/goal edit` | Spremeni besedilo cilja |
| `/goal pause` | Začasno ustavi |
| `/goal resume` | Nadaljuje |
| `/goal clear` | Odstrani cilj |

**Besedilo cilja ima največ 4.000 znakov.** [Uradna navodila](https://learn.chatgpt.com/docs/developer-commands?surface=cli)
