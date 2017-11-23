# Private notes Github

## Source control
Merge conflict ontstaat wanneer op meerdere workstations in zelfde file wordt gewerkt. Github bepaald niet wat "juist" is, maar detecteert de verschillen/conflicts.
Github kenmerkt dan. de aangepaste secties codes.

### Setup
1. Install Github op je computer
2. Op github.com nieuwe repository aanmaken
3. Clone aangemaakte repo

### Setup - init vanaf local in vscode
1. git init
1. maak repo aan op github.com, vink "init" niet aan!
1. git remote add origin "repo.url.git"
1. git push...

#### Commandline commands voor Github
##### CD
Change Directory
##### LS
Listing files in directory 
##### GIT CLONE <URL>
Clonet de zojuist aangemaakte Repo
##### GIT STATUS
Laat zien wat verschilt ivm Repo
##### GIT ADD
Voegt files toe aan GIT. bijv. GIT ADD index.html
1. GIT ADD -A voegt alles toe
##### GIT COMMIT - m "tekst commit"
Locking in Repo
##### GIT PUSH
Alles van workstation naar repo op github syncen.
##### GIT PULL
Haalt alles van repo op github op naar workstation (lokaal)

### Voorbeeld hoe met meerdere workstations werken
1. Clone repo op PC A
1. Clone repo op PC B
1. Maak een extra file op PC A, bijv. index.html
1. Maak een extra file op PC B, bijv. index2.html
1. Op PC A. check met GIT STATUS wat is toegevoegd en voeg toe met GIT ADD (op pc A is index.html toegevoegd)
1. Commit de wijziging naar Git (GIT COMMIT -m "tekstbericht met info over commet") en Sync dit naar github.com met GIT PUSH
1. Op PC B. dmv GIT PULL alle files ophalen
1. op PC B. index.html wijzigen en met GIT STATUS checken wat is added/modified/deleted. Hier staat dat index2.html toegevoegd moet worden (dmv GIT ADD) en index.html is aangepast.
1. Commit de veranderingen : GIT COMMIT -m "bladiebla"
1. Op PC A. kan je nu GIT PULL doen en krijg je added index2.html en gewijzigde index.html

### Workflow
1. Start met GIT PULL. zodat je alle bijgewerkte files hebt met de meest recente code.
1. Maak je wijzigingen. doe je ding..
1. alles toevoegen: GIT ADD - A
1. alles commiten naar git: GIT COMMIT -m "mijn toevogingen"

### Merge conflicts
Merge conflicts ontstaan wanneer dezelde regels code worden gewijzigd op meerdere workstations. Deze conflicten moeten opgelost worden en vervolgens gecommit worden.
Deze melding verschijnt bij het ophalen van nieuwe code (GIT PULL)
Na het handmatig oplossing van het conflict (juiste code laten staan) met GIT ADD -A alles toevoegen aan GIT en vervolgens commiten dmv GIT COMMIT -m "bericht".

### Foutmeldingen:
1. You have unmerged files: Vergeten om files toe te voegen voordat je commit.
1. Commit gemaakt zonder message zorgt voor extra terminal tekst (FULL SCREEN MESSAGE venster). hier uitkomen door <esc>:wq.

### GIT Version Control in VS Code
CMD+SHIFT+P laat de command pallete zien met alle funties in VS Code. Ook de Gitfuncties.
1. Op github.com een repo aanmaken. De URL (clone button) is nodig in VSC
1. In VSC gebruik functie "Clone Git repository" van het startscherm
   1. Vul de Repo URL in
   1. Geef het pad aan waar het lokaal opgeslagen kan worden. bijv: /Users/Jeffrey/Desktop/Test
   1. Melding "Open repo". Klik ja.
1. Wijzig een stukje code ter test. Ga naar de Git tab. Hier verschijnt een indicator welke wijzigen er zijn gedaan en wordt er aangegeven welke changes zijn gemaakt. M= modified, A= added, D= deleted. Dit wordt ook gekenmerkt in kleur, naast de regelgeving.
  1. Wanneer je klikt op een specifieke change. laat het exact zien wat er is gewijzgd ivm de GIT-versie. Linkerkant is de GIT versie en aan de rechterkant wordt de lokale versie getoond.

### Git branches in VS Code
Via command branche add branche. Vervolgens via gebruikelijke manier pushen naar origin. Dit kan ook via de cloud-icon dat in de statusbalk verschijnt.

### Sources:
https://www.youtube.com/watch?v=VOwyH2-VCVY
https://www.youtube.com/watch?v=0fKg7e37bQE&t=131s 

### Testen:
http://try.github.io/

### Tips
#### Undo last commit-functie
#### Local gelijk trekken met wat in github staat
https://stackoverflow.com/questions/1628088/reset-local-repository-branch-to-be-just-like-remote-repository-head

Setting your branch to exactly match the remote branch can be done in two steps:
git fetch origin
git reset --hard origin/master
If you want to save your current branch's state before doing this (just in case), you can do:
git commit -a -m "Saving my work, just in case"
git branch my-saved-work
Now your work is saved on the branch "my-saved-work" in case you decide you want it back (or want to look at it later or diff it against your updated branch).
Note that the first example assumes that the remote repo's name is "origin" and that the branch named "master" in the remote repo matches the currently checked-out branch in your local repo.
BTW, this situation that you're in looks an awful lot like a common case where a push has been done into the currently checked out branch of a non-bare repository. Did you recently push into your local repo? If not, then no worries -- something else must have caused these files to unexpectedly end up modified. Otherwise, you should be aware that it's not recommended to push into a non-bare repository (and not into the currently checked-out branch, in particular).
