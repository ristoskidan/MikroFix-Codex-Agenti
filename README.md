# MikroFIX — strokovni agenti Codex

To je samostojen Git repozitorij s fizičnimi datotekami v
`/home/mikrofix/Codex_Agenti`, zunaj razvojnega projekta. Tu so edini aktivni
operativni beležniki strokovnih agentov Codex in skupna soba. Lokalni coderji,
njihovi profili, zaganjalniki in zgodovinska orodja ostanejo v
`/home/mikrofix/MikroFIX_Service_v30_R9_LINUX_DEV/docs/local_agents/` ter
projektnem `CODER.md`. Poslovni kanon je fizično v tem repozitoriju,
v [`docs/kanon/00_KAZALO.md`](docs/kanon/00_KAZALO.md). V razvojnem
projektu ni njegove kopije ali simbolne povezave. Stara agentska orodja,
ki uporabljajo prejšnjo pot, še niso prilagojena; njihova prilagoditev
je ločeno opravilo. Zagonski navodili `AGENTS.md` in `CODER.md` ostajata
na obstoječem mestu.

## Odgovornosti

- **Lastnik** določa poslovna pravila, obseg dela in odloča o sprejemu sprememb.
- **Sidro** skrbi za kanon, stanje Gita in aktivne naloge; njegov delovni zapis
  je [`SIDRO.md`](SIDRO.md).
- **Nika** skrbi za profile lokalnih modelov, zaganjalnike in njihova navodila;
  njen delovni zapis je [`NIKA.md`](NIKA.md).
- **Piksi** skrbi za sistem vizualnih identitet, njihovo razmejitev in
  oblikovalska pravila; njegov delovni zapis je [`PIKSI.md`](PIKSI.md).
- **Svit** skrbi za javno spletno prisotnost `MikroFix`, gostovanje, varen
  postopek objave in tehnično delovanje spletnih poti; njegov delovni zapis je
  [`SVIT.md`](SVIT.md).
- **Prizma** opravlja neodvisne pravno-tehnične revizije skladnosti, ločuje
  zakonske zahteve od internih kontrol ter vodi sled ugotovitev in dokazov;
  njen delovni zapis je [`PRIZMA.md`](PRIZMA.md).
- **KERN** preverja lokalne jezikovne modele za Python coding naloge; njegov
  delovni zapis je [`KERN.md`](KERN.md).

Vsak skrbnik spreminja svoje operativne zapise in vire, ki mu jih lastnik
izrecno dodeli. Potrebno spremembo na področju drugega skrbnika mu preda z
razlogom in predlogom, ne poseže pa sam v njegove profilne datoteke.
Pred testiranjem in pred daljšim opravilom, pri katerem bo treba čakati, agent
lastniku pove namen in okvir pričakovanega čakanja. To je obvestilo, ne prošnja
za dodatno odobritev. Po koncu sporoči dejanski izid.

## Aktivni potek

Lastnik določi cilj in poslovne odločitve. Sidro uskladi cilj s kanonom in Git
stanjem, Nika, Piksi, Svit, Prizma oziroma KERN pa se vključijo, kadar cilj posega v
njihovo strokovno področje. Coder izvede en smiselno zaključen sklop, rezultat
se pregleda, odobren commit in push pa opravi Git-agent. Aktivna naloga se
izmenjuje v `/home/mikrofix/Desktop/aktivna naloga.md`; ukaz za aktivacijo cilja
ni del njene vsebine.

Skupni pogovor lastnika in vseh strokovnih agentov poteka v [`SOBA.md`](SOBA.md).
Soba je namenjena predajam, vprašanjem in usklajevanju; ne nadomešča kanona,
aktivne naloge, lastnikove odobritve ali operativnega zapisa posamezne vloge.

## Tehnični viri

Projektni `docs/local_agents/PRAVILNIK_VERIGE.md` ter mape `roles/`,
`supervisor/` in `dnevnik/` opisujejo prejšnjo nadzorovano verigo in ostajajo
zgodovinsko oziroma tehnično gradivo. Projektna mapa `pravila/` vsebuje
generirane izvlečke aktivnega kanona. `WORKSPACE.md` in `LEKCIJE.md` nista
dodatni odločevalski odgovornosti.
