# Wat is git?
Git is een vorm van versiebeheer (ook wel version control - VC genoemd)

=> Het is een systeem dat wijzigingen in één of meerdere bestanden in de loop van de tijd vastlegt, zodat je specifieke versies later kunt terugroepen.

Met een **Versiebeheersysteem** (ook SCM(Source Control Management)) kan je:
- Bestanden terugzetten naar een vorige staat
- Wijzigingen bekijken die in de loop van de tijd zijn aangebracht
- Zien wie het laatst iets heeft gewijzigd dat een probleem zou kunnen veroorzaken
- Samenwerken aan dezelfde bestanden

# Git Commando's
`git clone <connectie-string>` -> clone een repo naar de huidige directory
`git status` -> bekijk de huidige situatie
`git add .` -> voeg alle bestanden in de directory naar de staging area
`git commit -m` -> Commit de bestanden en maak ze klaar om te pushen. Je geeft al een bericht mee met nodige uitleg/info
`git push` -> Je pusht de huidige commit naar de repo

Gebruik `git <commando> -h` als je twijfelt over de syntax van een commando of meer uitleg wil

`git diff` -> hiermee kan je de wijzigingen bekijken

---
**Branches**

`git branch <naam>` -> maakt (lokaal) een nieuwe branch aan met `<naam>`

`git branch` -> bekijk het resultaat

`git switch <naam>` -> switcht naar de branch

`git branch -vv` -> -v=verbose, (2x) geeft dus extra info

`git merge aaa` -> merget de wijzigingen van de branch naar de 'main'