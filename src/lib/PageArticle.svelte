<script>
  import CommentsArticlePage from "../components/CommentsArticlePage.svelte";
  // Les fonctions onMount et onDestroy nous permettent de faire des choses spécifiques à des moments précis de l'application.
  // onMount nous permet de faire quelque chose dès que l'application est prête à être utilisée
  // onDestroy nous permet de faire quelque chose quand l'application se ferme ou qu'une partie de l'application est supprimée.
  // Importe les fonctions onMount et onDestroy de la librairie Svelte
  import { onMount, onDestroy } from "svelte";

  // Initialise les variables count et isActive en utilisant les données stockées dans localStorage, ou 0 et false si ces données ne sont pas encore présentes
  let count = localStorage.getItem("heartCount") || 0;
  let isActive = localStorage.getItem("heartActive") === "true";

  // Fonction qui change l'état du coeur et met à jour le compteur de likes en fonction de l'état du coeur
  function toggleHeart() {
    if (isActive) {
      count -= 1;
    } else {
      count += 1;
    }
    isActive = !isActive;
    // Met à jour les données stockées dans localStorage avec les nouvelles valeurs de count et isActive
    localStorage.setItem("heartCount", count);
    localStorage.setItem("heartActive", isActive);
    // Met à jour le texte du compteur de likes
    document.querySelector(".heart-count").textContent = parseInt(count);
  }

  // Utilise la fonction onMount pour exécuter du code dès que l'élément HTML est prêt à être utilisé
  onMount(() => {
    // Sélectionne l'élément HTML contenant le coeur
    const heart = document.querySelector(".heart");
    // Sélectionne l'élément HTML contenant le compteur de likes
    const countEl = document.querySelector(".heart-count");
    // Met à jour le texte du compteur de likes avec la valeur actuelle de count
    countEl.textContent = count;
    // Ajoute la classe "active" à l'élément HTML contenant le coeur si isActive est true
    if (isActive) {
      heart.classList.add("active");
    }
    // Ajoute un event listener pour écouter les clics sur l'élément HTML contenant le coeur et appeler la fonction toggleHeart
    heart.addEventListener("click", toggleHeart);
  });

  // Utilise la fonction onDestroy pour exécuter du code quand l'élément HTML est supprimé
  onDestroy(() => {
    // Sélectionne l'élément HTML contenant le coeur
    const heart = document.querySelector(".heart");
    // Supprime l'event listener pour éviter des fuites de mémoire
    heart.removeEventListener("click", toggleHeart);
  });
</script>

<main>
  <article class="article">
    <img src="https://picsum.photos/900/400" alt="foto" />

    <h2>Le confinement, période propice à la créativité humoristique</h2>
    <p id="paragraph" aria-label="Texte de l'article">
      Les réseaux sociaux ont été inondés de mèmes et de blagues sur la
      livraison des colis en ce moment. Entre les retards, les colis perdus et
      les livraisons aléatoires, certains ont commencé à se demander si les
      livreurs ne seraient pas mieux en train de livrer eux-mêmes leurs propres
      colis. Et puis, nous avons tous vu le fameux message "Votre colis a été
      livré" alors que vous attendez encore patiemment sur votre porche.
      Peut-être que les livreurs ont découvert une nouvelle forme de
      téléportation ou qu'ils ont finalement réussi à contourner les lois de
      l'espace-temps. Mystère.
    </p>

    <footer class="footer__dateauthor">
      <aside
        class="aside__dateauthor"
        aria-label="Date de publication et auteur"
      >
        <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
        <cite title="nom de l'auteur">Sarah Croche</cite>
      </aside>
      <div class="heart" class:active={isActive}>
        <span class="heart-count" />
        <i class="fa-regular fa-heart" id="heart-empty" />
        <i class="fa-solid fa-heart hidden" id="heart-filled" />
      </div>
    </footer>
  </article>

  <CommentsArticlePage />
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    padding: 3rem;
    font-family: $police;
    background-color: $color-white;

    article {
      display: block;
      padding: 2rem;
      @extend %glassmorphism;

      img {
        min-width: 100%;
        width: 100%;
        max-height: 160px;
        object-fit: cover;
        @extend %glassmorphism;
      }

      h2 {
        text-align: center;
        padding: 2rem;
        font-weight: bolder;
      }
      #paragraph {
        font-family: $police;
        padding: 2rem;
        line-height: 2rem;
      }

      .footer__dateauthor {
        display: flex;
        padding: 1rem;
        margin: 1rem;
        justify-content: space-between;
        aside {
          display: flex;
          margin-right: 1rem;
          font-size: 1.3rem;
          gap: 1rem;
          time {
            font-style: italic;
          }
          cite {
            font-style: normal;
            font-weight: bold;
          }
        }
        .heart {
          display: flex;
          cursor: pointer;
          font-size: 4rem;
          color: rgb(229 62 62);
          i {
          }

          #heart-filled {
            display: none;
          }

          &.active #heart-empty {
            display: none;
          }

          &.active #heart-filled {
            display: inline-block;
          }

          .heart-count {
            margin-right: 1rem;
            font-size: 2rem;
          }
        }
      }
    }
  }
</style>
