# Rendu Web Avancé Front
## J'ai choisi pour ce module d'explorer la technologie sveltekit
### Dans un premier temps j'ai simplement fait une navbar me permettant de naviguer entre plusieurs page de mon site
Donc j'ai vite découvert que contrairement a React.js le rootage est intégré dans SvelteKit, il suffit de créer sa page au bon endroit dans le fichier routes.
Pour naviguer il suffit d'une balise `<a href="/folderName"></a>`
Donc pour créer une page il faut un fichier +page.svelte dans son dossier, et il est possible de créer un fichier +layout.svelte qui sera transmis à tous ses dossiers enfant. C'est donc le bon endroit pour créer une navbar qui sera dispo dans toute l'app.


Contexte, variable globale, thème
navbar
changement de page -> log la page quittée et la page d'arrivée
hook useEffect, lire/modifier variable globale déclenche un instruction/fonction
gestions de formulaire
rootage sur un produit : /product/1
