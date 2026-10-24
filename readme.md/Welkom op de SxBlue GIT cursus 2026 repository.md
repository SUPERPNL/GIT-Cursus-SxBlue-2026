# Welkom op de SxBlue GIT cursus 2026 repository

In deze repository komen de cursus bestanden te staan. Als handigheidje staat de printbare GIT cheatsheet er al alvast in. 
De bedoeling van deze repository is om samen te leren hoe GIT werkt en hoe grotere bedrijven omgaan met version control. 

De beheerder van deze repository is Wouter Kitsz (wkitsz@sxblue.nl). 

## De start
### Installeren van GIT
*MacOs* <br>
Typ git in je Terminal. 
macOS toont dan automatisch een pop-up om de Xcode Command Line Tools te installeren, waar een basisversie van Git in zit.

*Windows*<br>
Ga naar https://git-scm.com/install/windows en download git en installeer. 

### Authenticatie<br>
We moeten een ssh key opzetten voor authenticatie met GIT. Dit doe je als volgt:

*MacOS:*<br>
1. Maak een ssh key aan<br>
Open een terminal en tik: <br>
ssh-keygen -t ed25519 -C "je-email"<br>
Vervang "je-email" door het e-mailadres van je GitHub-account. Het is alleen een label in de sleutel en wordt niet gecontroleerd.
Druk op Enter om de standaardlocatie te accepteren.
Daarna kun je een passphrase instellen (aanbevolen, en met --apple-use-keychain hoef je hem later niet steeds in te typen).

2. Voeg de sleutel toe aan de SSH-agent en de macOS-keychain<br>
ssh-add --apple-use-keychain ~/.ssh/id_ed25519

3. Voeg de publieke sleutel toe aan GitHub
Kopieer de publieke sleutel naar je klembord:<br>
pbcopy < ~/.ssh/id_ed25519.pub
Ga daarna naar GitHub → Settings → SSH and GPG keys → New SSH key. Geef de sleutel een naam (bijvoorbeeld “MacBook M1”), plak de sleutel in het veld en klik op Add SSH key.

4. Test de verbinding<br>
ssh -T git@github.com<br>
Bij de eerste keer vraagt SSH of je de authenticiteit van github.com vertrouwt. Typ yes.
Een geslaagde verbinding geeft:

**Hi <gebruikersnaam>! You've successfully authenticated, but GitHub does not provide shell access.
Dit is geen fout, maar de bevestiging dat het werkt.**

*Windows*<br>
Vereisten
* Windows 10 (versie 1809 of nieuwer) of Windows 11
* Git for Windows geïnstalleerd (https://git-scm.com/download/win)
* Een GitHub-account
* PowerShell (standaard aanwezig in Windows)

1. Controleer of de OpenSSH Client aanwezig is<br>
Open PowerShell en voer uit:<br>
ssh -V<br>
Krijg je een versienummer (bijvoorbeeld OpenSSH_for_Windows_9.x)? Ga door naar stap 2.
Krijg je een foutmelding? Installeer de OpenSSH Client:
Via Instellingen → Apps → Optionele functies → Functie toevoegen → OpenSSH Client, 

2. Maak een nieuwe sleutel aan<br>
ssh-keygen -t ed25519 -C "jouw-email@voorbeeld.nl"<br>
Vervang het e-mailadres door dat van je GitHub-account (het is alleen een label).
Bij de vraag Enter file in which to save the key druk je op Enter om de standaardlocatie te gebruiken:<br>
C:\Users\<jouwnaam>\.ssh\id_ed25519 <br>
Stel bij Enter passphrase een passphrase in (aanbevolen) of laat het leeg en druk op Enter.
Er zijn nu twee bestanden aangemaakt:  
 - id_ed25519	| Privésleutel. Deel deze nooit met iemand.
- id_ed25519.pub	| Publieke sleutel. Deze voeg je toe aan GitHub.  
4. Start de ssh-agent en voeg de sleutel toe
De ssh-agent onthoudt je sleutel (en passphrase) zodat je die niet bij elke push hoeft in te voeren.

4a. Zet de service eenmalig aan (PowerShell als administrator: rechtermuisknop op Windows PowerShell → Als administrator uitvoeren):  
Get-Service ssh-agent | Set-Service -StartupType Automatic.  
Start-Service ssh-agent  

4b. Voeg de sleutel toe (in een gewone PowerShell):  
ssh-add $env:USERPROFILE\.ssh\id_ed25519  
Controleer of de sleutel geladen is:  
ssh-add -l  

5. Voeg de publieke sleutel toe aan GitHub  
- Kopieer de publieke sleutel naar het klembord:  
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard. 

- Voeg hem toe op GitHub:  
Ga naar GitHub en klik rechtsboven op je profielfoto → Settings  
Kies in het linkermenu SSH and GPG keys  
Klik op New SSH key  
Vul bij Title een herkenbare naam in (bijvoorbeeld Windows laptop)  
Laat Key type op Authentication Key staan  
Plak de sleutel in het veld Key (Ctrl+V)  
Klik op Add SSH key en bevestig eventueel met je GitHub-wachtwoord  

6. Test de verbinding  
ssh -T git@github.com  
Bij de eerste keer vraagt SSH of je de authenticiteit van github.com vertrouwt. Typ yes.  
Een geslaagde verbinding geeft:  

**Hi <gebruikersnaam>! You've successfully authenticated, but GitHub does not provide shell access.
Dit is geen fout, maar de bevestiging dat het werkt.**


Initialiseer een repository
git init
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/wkitsz/GIT-Cursus-SxBlue-2026.git
git push -u origin main





