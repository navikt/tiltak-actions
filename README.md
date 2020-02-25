Tiltak-actions
==============================

Repo som inneholder _Github actions_ workflow-definisjoner. Definisjonene er generelle og kan kopieres inn i repoer etter behov.

# Henvendelser

## For Nav-ansatte
* Dette Git-repositoriet eies av [Team tiltak i Produktområde arbeidsgiver](https://navno.sharepoint.com/sites/intranett-prosjekter-og-utvikling/SitePages/Produktomr%C3%A5de-arbeidsgiver.aspx).
* Slack-kanaler:
  * [#arbeidsgiver-tiltak](https://nav-it.slack.com/archives/CCM9QUY3U)
  * [#arbeidsgiver-utvikling](https://nav-it.slack.com/archives/CD4MES6BB)
  * [#arbeidsgiver-general](https://nav-it.slack.com/archives/CCM649PDH)

# Workflows
Repoet definerer workflows for to hovedflyter
* Én flyt for _master_ branch, som bygger og deployer automatisk til dev-fss og prod-fss. *Merk at denne vil deploye automatisk til begge miljøer uten noen manuell bekreftelse*
* For alle andre brancher kjøres diverse byggesteg slik at applikasjonen bygges, og om ønskelig kan deployes vha kommentar på en issue som opprettes i github-repoet. Bygg-stegene blir da
  * Bygg applikasjon, lag image og opprett en issue i repoet som kan brukes for å deploye til dev-miljø _om ønskelig_.
  * Lytt etter kommentarer på issues og trigg en deploy dersom kommentaren har riktig format
  * Deploy til dev og gi tilbakemelding om OK eller feil i kommentar på issue 

Deploy av branch tillates kun dersom branchen er nyere enn master. Hvis master inneholder noe som ikke er merget inn i branchen vil deploy ikke kjøres.

# Ta i bruk
Workflow-definisjonene er generelle og kan brukes på tvers av repoer uten endring.
Forutsetter at:
* Applikasjonen bygges med Maven og deployes vha. Docker og nais
* Det finnes en `naiserator.yaml` på rot-nivå i repoet som definerer nais-spec
* Applikasjonen deployes i fss, ikke sbs
* Det finnes filer som heter `nais/dev-fss.json` og `nais/prod-fss.json` som definerer miljøspesifikke variabler

*For å ta i bruk: Kopier workflow-filene inn i en mappe som heter `.github/workflows/` i repoet ditt. Slå samtidig av eventuell byggejobb i circleCi.

