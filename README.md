# Rendu Web Avancé Front
## J'ai choisi pour ce module d'explorer la technologie sveltekit
### Dans un premier temps j'ai simplement fait une navbar me permettant de naviguer entre plusieurs page de mon site
Donc j'ai vite découvert que contrairement a React.js le rootage est intégré dans SvelteKit, il suffit de créer sa page au bon endroit dans le fichier routes.
Pour naviguer il suffit d'une balise `<a href="/folderName"></a>`
Donc pour créer une page il faut un fichier +page.svelte dans son dossier, et il est possible de créer un fichier +layout.svelte qui sera transmis à tous ses dossiers enfant. C'est donc le bon endroit pour créer une navbar qui sera dispo dans toute l'app. Donc je créé mon +layout.svelte à la racine de mon app, j'importe mon css, je créé ma navbar et il ne faut pas oublier la balise `<slot />` qui indique ou ira le code de la page.
```html
<script lang="ts">
    import "../global.css";

</script>

<div class="bg-base-300 min-h-full">
    <div class="navbar bg-base-100 px-6">
        <div class="flex-1">
            <a href="/" class="font-bold text-xl">Home </a>
            <a href="/catPick" class="font-bold text-xl">Pic pick</a>
            <a href="/settings" class="font-bold text-xl">Settings</a>
        </div>
        
    </div>
    <slot />
</div>
<style type="text/css">

</style>
```



Contexte, variable globale, thème
navbar
changement de page -> log la page quittée et la page d'arrivée
hook useEffect, lire/modifier variable globale déclenche un instruction/fonction
gestions de formulaire
rootage sur un produit : /product/1
