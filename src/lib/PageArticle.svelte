<script>
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
    document.querySelector(".heart-count").textContent = count;
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
    <img src="https://picsum.photos/200" alt="foto" />

    <h2>TITRE ARTICLE</h2>
    <p id="paragraph" aria-label="Texte de l'article">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed ultricies
      nisl eget eros dapibus, vitae mattis tortor ultricies. Nunc malesuada
      scelerisque tempus. Donec fringilla metus vitae tellus porta, sit amet
      dignissim magna eleifend. Vestibulum pellentesque mi at eros vulputate
      hendrerit. Maecenas at elit ligula. Integer sollicitudin tellus quis elit
      lacinia semper. Fusce ac mattis mi. Maecenas consequat sapien sit amet
      ullamcorper efficitur. Nullam facilisis odio augue, nec mattis odio
      malesuada et. Suspendisse eget ante ut massa malesuada maximus. Nullam
      porta semper convallis. Sed mattis urna metus, quis pharetra dui molestie
      at. Vivamus vel varius dui. Fusce vitae commodo neque. Pellentesque eu
      lectus tortor. Integer et tempor purus. Vivamus facilisis euismod mi
      porttitor tincidunt. Nullam auctor libero sit amet mi bibendum pulvinar in
      sed ante. Nulla ornare enim ut odio lobortis, quis molestie mauris
      aliquet. Duis faucibus eros neque, ac suscipit felis lacinia et. Integer
      pretium nulla et nisl vehicula scelerisque. In hac habitasse platea
      dictumst. Maecenas efficitur urna efficitur, tempus nibh id, bibendum
      dolor. Quisque gravida et turpis sit amet fringilla. Nam sodales leo ut
      suscipit blandit. Praesent nec venenatis nisl, et condimentum nunc. Fusce
      eu dictum nisl. Quisque nisi lectus, dictum sit amet risus non, tincidunt
      ullamcorper nulla. Ut euismod quis libero in auctor. Cras in aliquet
      lacus. Cras molestie neque sed dui accumsan iaculis. Nunc non leo in neque
      lobortis pharetra at a lacus. Curabitur scelerisque, nunc eu consequat
      sodales, nulla tellus auctor nibh, sed mollis ante turpis eu ipsum.
      Aliquam molestie, dolor ut blandit sodales, augue leo mattis enim, non
      ultricies nisl massa quis neque. Quisque tincidunt rhoncus quam, sit amet
      congue dui malesuada non. Duis ornare sit amet neque in venenatis. Sed
      arcu quam, gravida id aliquam et, dictum vel nunc. Donec posuere felis
      velit. Nam non massa molestie, volutpat turpis et, congue nibh. Mauris a
      dignissim lacus. Sed pretium ac risus luctus eleifend. Sed lobortis felis
      eros, venenatis ullamcorper massa tristique in. Nunc condimentum enim nec
      nibh euismod efficitur. Pellentesque nulla lorem, ultrices nec lectus at,
      blandit elementum augue. Vivamus mi urna, semper vel commodo quis,
      tristique et mauris. Proin et gravida orci, sagittis maximus nibh. Ut quis
      dui lectus. Vestibulum ut mi erat. Aliquam vulputate lectus nec vestibulum
      dapibus. Donec scelerisque augue id tellus tincidunt, at lacinia risus
      varius. Morbi faucibus, ante sed consectetur cursus, odio erat facilisis
      nisi, at suscipit nisi sem sed ligula. Orci varius natoque penatibus et
      magnis dis parturient montes, nascetur ridiculus mus. Phasellus neque
      diam, vehicula ut nulla a, vulputate laoreet nisl. Sed egestas venenatis
      diam, volutpat finibus ligula porttitor quis. Suspendisse et lectus
      ullamcorper, ultricies ante id, interdum mauris. Aliquam eleifend
      malesuada egestas. Maecenas sagittis ante eget tellus fermentum, ut
      convallis enim gravida. Fusce semper laoreet fermentum. Praesent turpis
      velit, egestas quis velit quis, varius tincidunt orci. Nunc facilisis elit
      a nisl semper blandit. Suspendisse pellentesque accumsan porta. Cras
      blandit arcu vel urna posuere, ac tempor lorem interdum. Donec magna
      libero, scelerisque eu massa vitae, dapibus scelerisque lacus. Fusce
      sodales maximus auctor. Etiam est leo, sodales id ipsum.
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
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    padding: 3rem;
    font-family: $police;

    article {
      display: block;
      padding: 00.625rem;
      @extend %glassmorphism;

      img {
        min-width: 100%;
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
          }
        }
      }
    }
  }
</style>
