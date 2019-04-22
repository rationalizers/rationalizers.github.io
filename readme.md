# Disclaimer

## EN:

This page's purpose is to promote critical and constructive scrutiny of
political argumentation, **not** to publish anything that is or might be unlawful,
libelous, defamatory, discriminatory or abusive toward any
individual or group; **not** to harass, abuse, threaten, or incite violence
towards any individual or group.

## FI:

Tämän sivun tarkoituksena on edistää poliittisen argumentaation kriittistä ja
rakentavaa tarkastelua, **ei** julkaista mitään mikä on tai voisi olla
laitonta, herjaavaa, halventavaa, syrjivää tai loukkaavaa minkään yksilön tai
ryhmän kannalta; **eikä** ahdistella, loukata, uhata tai kiihottaa väkivaltaa
ketään yksilöä tai ryhmää kohtaan.

# Osallistuminen sisällön editointiin

Tämä sivuston editointiin on tervetullut osallistumaan kuka tahansa, jolla on
tietoa feministisestä argumentaatiosta ja sen taustalla olevista premisseistä.

Osallistuminen on mahdollista täältä GitHubin kautta seuraavalla tavalla
(tarkemmat vaiheittaiset ohjeet alempana):

- Fork omalle GitHub-tilillesi
- Editointi omassa forkatussa repositoriossa
- Valmiista muutoksista pull request tähän repositorioon

## Mikä on Git?

[Git](https://git-scm.com/) on
[hajautettu versionhallintaohjelmisto](https://fi.wikipedia.org/wiki/Hajautettu_versionhallintajärjestelmä),
jota käytetään laajasti ohjelmistokehityksessä.
Sen avulla on helppo noutaa, muokata ja yhdistää tiedostoja ja tiedostoihin
tehtyjä muutoksia eri lähteiden välillä.
Tämän ohella Git toimii varmuuskopiointina, undo-historiana ja yhteistyöalustana.
Sen avulla tiedostojen eri versioita, työvaiheita tai erilaisia
ratkaisuvaihtoehtoja on helppo ja tehokas vertailla ja yhdistellä sekä
tarvittaessa palauttaa.

## Git-ohjelmiston asentaminen

Käyttääksesi GitHubia tarvitset Git- ja OpenSSH-ohjelmistot (sekä
luonnollisesti ne ohjelmistot, joista nämä ovat riippuvaisia, kuten
OpenSSL-kirjaston).

### Git-ohjelmiston asentaminen Linux-ympäristössä

Linux-ympäristössä saat tarvittavat ohjelmat kätevimmin asennettua
Linux-jakelusi omalla paketinhallintajärjestelmällä, kuten apt (Debian) tai dnf
(Fedora).

Esimerkiksi Debian-Linuxissa tämä tapahtuu seuraavalla komennolla:

~~~
sudo apt install git openssh-client
~~~

Paketinhallintajärjestelmä pitää huolen siitä, että riippuvuudet tulee
täytettyä eli että myös tarvittavat muut ohjelmistot (kuten OpenSSL)
asennetaan.

Seuraavalla komennolla voit tarkistaa, että ko. ohjelmat ovat käyttämässäsi
järjestelmässä asennettuina[^which]:

~~~
which git ssh ssh-keygen
~~~

[^which]: which-komento etsii parametrina saamiensa komentojen tiedostopolut ja tulostaa ne. Ellei järjestelmässä ole sen parametrina saamaa komentoa, se ei tulosta ko. komennon osalta mitään vaan asettaa paluuarvoksi "1".

### Git-ohjelmiston asentaminen Windows-ympäristössä

Lataa Git-ohjelmisto sivulta <https://git-scm.com/download/win>.

![Git-ohjelmiston lataaminen ja asentaminen.](/images/posts/wingit-install-run.png "Ruutukaappaus tiedoston latauksesta")

- Valitse heti latauksen jälkeen "**Run**".
- Vastaa kysymykseen "Do you want to run this software" myöntävästi.
- Hyväksy GNU:n lisenssi.
- Valitse asennushakemisto ja Start menu -hakemisto  (jätä oletukset).
- Valitse seuraavat asennusoptiot[^aoptiot]:
    - "**Use Git from Windows Command Prompt**"
    - "**Use the OpenSSL library**"
    - "**Checkout Windows-style, commit Unix-style line endings**"
    - "**Use Windows' default console window**"
    - "**Enable file system caching**"
- Ja paina lopuksi"**Install**".

[^aoptiot]: Git on toki mahdollista saada toimimaan muillakin konfiguraatioilla, mutta ainakin näillä optioilla sen pitäisi toimia.

Näiden vaiheiden jälkeen asennusohjelman pitäisi ilmoittaa, että Git-ohjelmisto
on onnistuneesti asennettu.

## SSH-avainparin luominen

### Avainparin luominen Linux-ympäristössä

Generoi SSH-avainpari seuraavilla komennoilla:

~~~
test -d ~/.ssh||mkdir ~/.ssh
ssh-keygen -t rsa -b 2048 -f ~/.ssh/github-key
~~~

Halutessasi voit antaa avaimelle salasanan, mutta se ei ole
välttämätöntä[^passu].

[^passu]: Yksityisten avainten salasanojen tarpeellisuudesta ks. esim. <https://www.qubes-os.org/doc/split-gpg/> "the so-often-used passphrases on private keys are pretty meaningless because the attacker can easily set up a simple backdoor which would wait until the user enters the passphrase and steal the key then". 

### Avainparin luominen Windows-ympäristössä

Graafinen ohjelma Git GUI ei anna riittävän laajoja vaihtoehtoja, joten
SSH-avainpari täytyy generoida komentoriviltä.

Käynnistä siis Start-valikon kautta Git Bash:

![Git Bashin käynnistäminen Start-valikon kautta.](/images/posts/wingit-start-git-bash.png "Kuva Start-valikosta")

Generoi SSH-avainpari antamalla Git Bashissa seuraavat komennot:

~~~
test -d ~/.ssh||mkdir ~/.ssh
ssh-keygen.exe -t rsa -b 2048 -f ~/.ssh/github-key
~~~

Jos haluat suojata avaimen salasanalla, voit tehdä niin.

## GitHub-tilin luominen (ellei sinulla jo ole tiliä)

Mene GitHubin [etusivulle](https://github.com/), ja luo oma tili (Sign up for
GitHub). Jos törmäät ongelmiin tilin luomisessa, löydät ohjeita
[täältä](https://help.github.com/en).

## Fork rationalizers.github.io

GitHub-tilin luomisen jälkeen mene
[rationalizers.github.io-repositorioon](https://github.com/rationalizers/rationalizers.github.io)
ja klikkaa oikeasta yläkulmasta Fork-painiketta (tämä toiminto kloonaa
repositorion omalla tililläsi listatuksi repositorioksi), jota voit vapaasti
muokata (tekemäsi muokkauksia voit ehdottaa lisättäväksi päärepositorioon pull
request -toiminolla).

## GitHubin käyttöönotto

Kirjaudu GitHub-tilillesi, mene tilin asetuksiin (oikean yläkulman ikoni, ja
Settings), sen jälkeen kohtaan SSH and GPG keys ja klikkaa New SSH key. Anna
avaimelle nimi (Title) ja kopioi julkinen avain (tiedoston github-key.pub
sisältö) tekstikenttään (Key).

Lisättyäsi avaimen kopioi seuraava teksti tiedostoon ~/.ssh/config:

~~~
Host github
HostName github.com
ForwardX11 no
PasswordAuthentication no
IdentityFile ~/.ssh/github-key
Port 22
User git
~~~

Kokeile asetusten toimivuus komennolla

~~~
ssh github
~~~

Jos komento antaa tulosteen, joka sisältää "You've successfully
authenticated", asetuksesi toimivat, ja voit kloonata repositorion komennolla

~~~
cd [hakemisto, johon haluat kloonata repositorion]
git clone github:USER/rationalizers.github.io
~~~

(tässä merkkijonolla USER tarkoitetaan GitHub-käyttäjätunnustasi).

Lopuksi on hyvä vielä kertoa Gitille, millä nimellä teet muutoksia ja mikä on
sähköpostiosoitteesi:

~~~
git config --global user.name "Oma Nimesi"
git config --global user.email sähköposti@osoitteesi
git config --global user.signingkey pgpid
~~~

*HUOM: Nämä tiedot näkyvät julkisesti GitHubissa, joten jos haluat osallistua
sisällön muokkaamiseen anonyyminä, laita tässä kohdassa omaksi nimeksesi
haluamasi nimimerkki ja sähköpostiosoitteeksi jokin anonyymi
sähköpostiosoitteesi.* Jos et halua allekirjoittaa commiteja PGP:llä, voit
kirjoittaa pgpid:n kohdalle esim. "none".

Jos käytät Gitiä myös muuhun, saatat haluta antaa tämän repositorion asetukset
seuraavilla komennoilla:

~~~
cd rationalizers.github.io # siirry repositorion paikalliseen kopioon
git config user.name "Nimimerkki"
git config user.email nimimerkkin@sposti
git config user.signingkey pgpid
~~~

jolloin kyseiset asetukset tulevat käyttöön vain tämän repositorion tässä
paikallisessa kopiossa ja globaalit asetuksesi säilyvät entisellään.

Lisäksi kannattaa jo tässä vaiheessa lisätä päärepositorio (johon muilla kuin
rationalizers-tilin haltijoilla on vain lukuoikeus) seuraavalla komennolla:

~~~
git remote add upstream https://github.com/rationalizers/rationalizers.github.io.git
~~~

## GitHubin peruskäyttö

Tyypillinen kaava Gitin käytössä on ensin kloonata repositorio omalle koneelle
paikalliseksi kopioksi ja sen jälkeen työstää repositorion sisältöä seuraavaa
kaavaa toistaen:

1. muiden tekemien muokkausten lataaminen palvelimelta (git pull)
1. omien muokkausten tekeminen repositorioon
1. muokkausten lisääminen valmistelualueelle (git add)
1. pysyvän muutoksen tekeminen (git commit)
1. omien pysyvien muutosten tallentaminen palvelimelle (git push)

Git on todella monipuolinen ohjelmisto, ja näissä ohjeissa on
tarkoituksenmukaista käydä läpi vain sen kaikkein perustavimmat toiminnot sekä
GitHubin peruskäyttö.
Hyvät ja kattavat (osittain suomennetut) ohjeet Gitin käyttöön yleisesti
löydät osoitteesta <https://git-scm.com/book/fi/v1/Gitin-perusteet>.
Graafisista Git-ohjelmistoista ks. <https://git-scm.com/download/gui/windows>.

## Osallistuminen rationalizers.github.io-repositorion editointiin

### Issue

Jos löydät repositorion sisällöstä virheen tai haluat muuten kommentoida
sisältöä, voit tehdä sen Issue-toiminnon kautta:

1. klikkaa
  [päärepositorion](https://github.com/rationalizers/rationalizers.github.io)
  Issues-välilehteä tai avaa Issues suoraan
  [tästä linkistä](https://github.com/rationalizers/rationalizers.github.io/issues),
2. klikkaa "Submit new issue" ja kirjoita kommenttisi käyttöliittymän ohjeita
  seuraten.

### Pull request

Pull request -toiminnolla voit ehdottaa oman "forkatun" repositoriosi
muutoksia lisättäväksi päärepositorioon.

1. Klikkaa oman tilisi alle forkatussa repositoriossa "New pull request".
2. Valitse vasemmalle (base) päärepositorio (ellei jo ole) ja oikealle (head)
oma forkattu repositoriosi.
3. Kirjoita viesti, jossa kuvailet tekemäsi muutokset.
4. Klikkaa "Create pull request".

### Tavanomainen "work flow"

Oletetaan, että olet "forkannut" päärepositorion oman GitHub-tilisi alle ja
kloonannut tuon forkatun repositorion koneellesi paikalliseksi kopioksi.
Haluat jatkaa sisällön muokkaamista.

1. Ensimmäiseksi on hyvä varmistaa, että paikallinen kopiosi sisältää
päärepositorion viimeisimmät muutokset

```{#upstreampull .sh}
git checkout master
git pull upstream master
```

2. Ellei git kerro, että "Already up-to-date", päivitä nämä muutokset myös
omaan forkattuun repositorioosi

```{#forkpush .sh}
git push origin master
```

3. Tee haluamasi muutokset mieleiselläsi tekstieditorilla.

4. Lisää muokkauksesi valmistelualueelle

```{#git-add .sh}
git add [muokkaamasi tiedostot]
```

5. Tee pysyvä muutos eli commit

```{#git-commit .sh}
git commit -m '[muokkauksen vapaamuotoinen kuvaus]'
```

tai vaihtoehtoisesti voit kirjoittaa commit-viestin järjestelmäsi
oletuseditorilla, jolloin edellisen komennon sijaan

```{#git-commit-editor .sh}
git commit
```

(commit lisätään heti sen jälkeen, kun olet tallentanut tekstin ja sulkenut
editorin).

6. Tallenna muutokset GitHubiin omaan forkattuun repositorioosi eli push

```{#git-push .sh}
git push origin master
```

Tämän jälkeen voit ehdottaa omaan "forkattuun" repositorioosi tekemiäsi
muutoksia lisättäväksi päärepositorioon, kuten yllä kohdassa [Pull
request](#pull-request).
