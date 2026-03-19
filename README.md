##Refleksion

Vi valgte fra start at opdele figma dokumentet i forskellige komponenter, for at få et overblik over hvordan vi nemmest kunne kode det komponentbaseret. Det gjorde meget gavn, da det også blev meget nemmere at dele det op blandt os.

Derefter gik vi i gang med at kode de forskellige komponenter, og tog dem et efter et. Det gjorde det nemt at smide det ind på deres respektive page til sidst.

Vi valgte at kigge på responsiviteten som det sidste, da vi selv skulle finde ud af hvordan det skulle se ud. Det gik relativt nemt for, men der kom et par benspænd på enkelte komponenter, især hvor `grid-row` og `grid-column` var blevet brugt.

Desuden kigger vi også først på rigtigt at implementere tokens til sidst, hvilket en anden gang klart vil være noget af det første som vil blive sat op, da det skabte lidt problemer ifølge med at skulle gennemgå alt og ændre allerede opsatte `font-sizes` fx.

Alt i alt har det været en spændende og udfordrende opgave, hvor vi skulle sammensætte alt det vi har lært på temaet.
###Teknikker og principper

Vi har gjort brug af `--flow-space` i flere af vores komponenter. Det har hjulpet med at gøre stylingen mere uniform og nemmere at styre.

.flow > _ + _ {
margin-block-start: var(--flow-space, 1em);
}

Vi gjorde brug af `@container` queries i vores component, som ikke kun gjorde det muligt at bruge responsivt, men også at kunne bruge samme component flere steder, selvom stylingen skulle være lidt anderledes. Dette kan ses i sektionen `Our Team`, hvor vi brugte samme komponent som bruges på selve team siden.

@container (width < 420px) {
.card {
.imgContainer {
display: grid;

         .Image {
           grid-row: 1;
           grid-column: 1;
           border-radius: 25px;
           overflow: clip;
         }
         .jobTitle {
           background-color: var(--color-ui-primary);
           color: var(--color-on-ui-primary);
           padding: 0.2rem 1.2rem;
           border-radius: 25px;
           text-align: center;
           grid-row: 1;
           grid-column: 1;
           align-self: end;
           justify-self: end;
           margin: 15px;
         }
       }

( et udklip)

Til vores overordnede layout har vi brugt følgende css

body {
display: grid;
grid-template-columns:
[full-start] 1fr [content-start] minmax(0, 75rem)
[content-end] 1fr [full-end];
}

header,
footer,
main,
section {
display: grid;
grid-template-columns: subgrid;
grid-column: full;

> :not(&) {
> grid-column: content;
> }
> }

Den fungerer ved at lave et grid med 3 kolonner, hvor den midterste kolonne indeholder det content vi har på siden, samtidigt med at baggrundsfarverne stadigvæk kan fylde hele viewportens bredde. Hvis man så ønsker noget indhold skal gå helt ud til kanterne, kan man give den “grid-column: full;”.

###Defensive CSS

Vi har gjort brug af `flex-wrap` hvor det giver mening i forhold til responsivitet.

###Progressive enhancement

Vi har brugt @supports på vores “login” knap i navbaren, så vi at den ser ordentlig ud, uanset om brugerens browser understøtter anchor-name eller ej.

###Organisering af css

Vores globale css består af vores overordnede grid, der går igen på alle siderne. Derudover har vi også vores fonts, samt font-sizes hvor vi har brugt vores tokens. Ellers er vores css meget komponentbaseret, selvfølgelig bortset fra farver mm. som vi har fra tokens.

Set tilbage kunne vi godt have haft flere ting i vores globale css, eksempelvis indeholder alle sektionerne en titel, et “eyebrow” og en beskrivelse, det har vi stylet hver gang vi har lavet et komponent, men det havde selvfølgelig givet mening at samle det som klasser i den globale css i stedet for.

Venlig Hilsen,
Anthon og Mathias
