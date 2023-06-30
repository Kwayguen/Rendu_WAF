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
### J'ai ensuite fait un exemple d'appel API
Le principe est simple, avec un bouton j'appelle une API qui me fournit une liste de 10 images, et je permets avec un bouton par image de les afficher.
Je créé donc le répertoire de la route de ma page pour le call API, la page ressemble à ça:
```html
<body>
  <main>
    <h1>Pick Cats Pics Page</h1>
    <section>
      <PicPicker />
    </section>
  </main>
</body>
```
Donc simplement un titre puis j'appelle le composant 'PicPicker'
```typescript
let picList:{src: string, alt: string}[] = [];
const randomPics = async () => {
  let res = await fetch("https://api.thecatapi.com/v1/images/search?limit=10");
  let randPic = await res.json();
  picList = randPic.map((p:any) => {
    return {src: p.url, alt: p.id}
  });
}

const selectPic = (newSrc: string, newAlt: string) => {
    src = newSrc;
    alt = newAlt;
};
```
Donc je commence par l'appel API avec un fetch puis je map le résultat dans une liste.
```html
<div class="head">
<h2>Image picker </h2>
<button class="button" on:click={randomPics}>Get Pics</button>
</div>
<div class="buttons">
    {#each picList as { src, alt}}
        <button on:click={() => selectPic(src, alt)} >{alt}</button>
    {/each}
</div>

<Picture {src} {alt} />
```
Ensuite j'affiche un bouton par élément de la liste, chaque bouton affiche une image dans le component placeholder => ```<Picture />``` qui est un component qui gère l'affichage d'une image.
C'est tout pour le call API.
<br>
### Variables d'état
Dans react.js, pour utiliser une variable on doit passer par la fonction useState, pour accèder à l'état de la variable.<br>
Pour la modifier il faut passer par une fonction qui va aller modifier l'état de la variable.
```typescript 
const [count, setCount] = useState(0);
setCount(count + 1);
```
SvelteKit priorise la réactivité et une simple déclaration de variable permet de pouvoir la modifier en code et l'affichage sera directement mis à jour.
```typescript
const variable = true;
variable = false;
```
Cette différence s'explique par le fait que react.js utilise une approche de rendu virtuel (Virtual DOM), où les modifications de l'interface utilisateur sont d'abord appliquées à une représentation virtuelle de l'arbre DOM, puis diffusées vers le navigateur; SvelteKit lui adopte une approche de rendu compilé, où le code source est transformé en JavaScript optimisé lors de la compilation et directement exécuté dans le navigateur.


<br>Finir changement de theme, mettre un useeffect sur le new theme et faire une action, puis tout expliquer et comparer a react <br> 
Contexte, variable globale, thème
navbar
changement de page -> log la page quittée et la page d'arrivée
hook useEffect, lire/modifier variable globale déclenche un instruction/fonction
gestions de formulaire
rootage sur un produit : /product/1
