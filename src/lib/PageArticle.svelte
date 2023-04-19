<script>
  import { link, push } from "svelte-spa-router";

  // Importe le composant CommentsArticlePage depuis le fichier CommentsArticlePage.svelte.
  import CommentsArticlePage from "../components/CommentsArticlePage.svelte";

  // Récupère les paramètres passés au composant et extrait l'ID de l'article.
  export let params = {};
  const article_id = params.article_id;

  // Fonction asynchrone getArticle pour récupérer un article en fonction de son ID.
  const getArticle = async (id) => {
    const endpoint = `${
      import.meta.env.VITE_URL_DIRECTUS
    }/items/articles/${id}?fields=*,users_id.*,date_created`;
    const response = await fetch(endpoint);
    const json = await response.json();
    return json.data;
  };

  // LIKES //
  let count = parseInt(localStorage.getItem("heartCount")) || 0;
  let isActive = localStorage.getItem("heartActive") === "true";

  // Fonction toggleHeart pour gérer l'état du bouton "J'aime" et le compteur de likes.
  function toggleHeart() {
    // Si le bouton "J'aime" est actif, décrémente le compteur de likes.
    if (isActive) {
      count -= 1;
    } else {
      // Sinon, incrémente le compteur de likes.
      count += 1;
    }
    // Inverse l'état du bouton "J'aime".
    isActive = !isActive;

    // Stocke le compteur de likes et l'état du bouton "J'aime" dans le localStorage.
    localStorage.setItem("heartCount", count);
    localStorage.setItem("heartActive", isActive);
  }

  // Fonction asynchrone getCurrentUserRole pour récupérer le rôle de l'utilisateur actuellement connecté.
  const getCurrentUserRole = async () => {
    const token = window.localStorage.getItem("token");
    if (!token) {
      return null;
    }
    const response = await fetch(
      `${import.meta.env.VITE_URL_DIRECTUS}/users/me`,
      {
        headers: {
          Authorization: `Bearer ${token}`,
        },
      }
    );
    const json = await response.json();
    return json.data.role;
  };

  // Fonction asynchrone getUserRole pour appeler l'API et obtenir le rôle de l'utilisateur connecté.
  const getUserRole = async () => {
    const role = await getCurrentUserRole();
    if (
      role === "645cbe7e-cdf9-409c-bc58-863ce065dfbb" ||
      role === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5"
    ) {
      return role;
    }
    return null;
  };

  let roleID = null;

  // Fonction handleStorageChange pour mettre à jour la variable "roleID" lorsque l'utilisateur connecté change.
  const handleStorageChange = (event) => {
    if (event.key === "token") {
      getUserRole().then((role) => {
        roleID = role;
      });
    }
  };
  // Ajoute un écouteur d'événements "storage" sur la fenêtre pour détecter les changements du token.
  window.addEventListener("storage", handleStorageChange);


  // Fonction appelée lorsque l'utilisateur clique sur l'icône de modification
  const handleEditClick = () => {
    // Redirige l'utilisateur vers la page de modification correspondante
    push(`/modification/${article_id}`);
  };
</script>

<main>
  <article>

    <!-- Attente de la récupération de l'article -->
    {#await getArticle(article_id)} 

    <!-- Affiche un message pendant le chargement des données -->
      <p>En chargement. Je cherche les données sur l'api...</p>

    <!-- Une fois les données récupérées, affiche l'article -->
    {:then article}

      <!-- doit apparaitre seulement pour les auteurs -->
      {#await getUserRole()}
        <p>Chargement...</p>
      {:then role}

      <!-- Si l'utilisateur a un rôle (auteur ou admin) -->
        {#if role}
        <!-- Affiche l'icône de modification -->
          <span class="edit-icon"
            ><a aria-label="Éditer l'article" on:click={handleEditClick}
              ><i class="fa-solid fa-pen-to-square" /></a
            ></span
          >
        {/if}
      {:catch error}
        <p>Erreur : {error.message}</p>
      {/await}
      <img
        src={import.meta.env.VITE_URL_DIRECTUS + "/assets/" + article.image}
        alt={article.alt}
      />

      <h3>{article.title}</h3>
      <p id="paragraph" aria-label="Texte de l'article">
        {article.content}
      </p>

      <footer>
        <aside aria-label="Date de publication et auteur">
          <time
            datetime={article.date_created}
            aria-label="Date de publication"
          >
            {new Date(article.date_created).toLocaleDateString("fr-FR", {
              day: "numeric",
              month: "numeric",
              year: "numeric",
            })}
          </time> <span aria-hidden="true"> || </span>

          <cite title={article.users_id.pseudo} aria-label="Auteur"
            >{article.users_id.pseudo}</cite
          >
        </aside>
      </footer>{/await}
    <div class="heart" class:active={isActive} on:click={toggleHeart}>
      <span class="heart-count">{count}</span>
      <i class="fa-regular fa-heart" id="heart-empty" />
      <i class="fa-solid fa-heart hidden" id="heart-filled" />
    </div>
  </article>

  <CommentsArticlePage {article_id} />
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    padding: 3rem;
    font-family: $police;
    background-color: $color-white;
    color: $color-black;
    @media screen and (min-width: 580px) {
      padding: 3rem;
    }
    display: flex;
    justify-content: center;
    flex-direction: column;
    article {
      display: block;
      padding: 2rem;
      margin: 3rem;
      @extend %glassmorphism;
      @media screen and (min-width: 770px) {
        padding-inline: 17vw;
        padding-top: 5rem;
      }
      @media screen and (min-width: 1024px) {
        padding-inline: 15vw;
        max-width: 910px;
        min-width: 910px;
        align-self: center;
      }
      @media screen and (min-width: 1440px) {
        padding-inline: 10vw;
      }
      a {
        text-decoration: none;
        color: $color-black;
        .fa-pen-to-square {
          cursor: pointer;
          position: absolute;
          right: 0;
          top: 3px;
          margin: 3rem;
          padding: 1rem;
          font-size: 3rem;
          border-radius: 100%;
          z-index: 1;
          background-color: rgba(255, 255, 255, 0.7);
          transition: opacity 0.2s ease-in-out;
          @media screen and (min-width: 770px) {
            top: 0;
            background-color: transparent;
          }
        }
      }
      img {
        min-width: 100%;
        width: 100%;
        max-height: 160px;
        object-fit: cover;
        @extend %glassmorphism;
      }

      h3 {
        @extend %h3;
      }
      #paragraph {
        font-family: $police;
        padding: 2rem;
        @extend %p;
      }

      footer {
        display: flex;
        flex-wrap: wrap;
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
      }

      footer > *:nth-child(1),
      footer > *:nth-child(2) {
        width: 100%;
      }
      .heart {
        display: flex;
        cursor: pointer;
        font-size: 4rem;
        justify-content: right;
        margin-top: 2rem;
        color: rgb(229 62 62);
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
</style>
