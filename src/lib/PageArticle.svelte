<script>
  import { link } from "svelte-spa-router";
  import CommentsArticlePage from "../components/CommentsArticlePage.svelte";
  
  export let params = {};
  const article_id = params.article_id;

  const getArticle = async (id) => {
    const endpoint = `${import.meta.env.VITE_URL_DIRECTUS}/items/articles/${id}?fields=*,users_id.*,date_created`;
    const response = await fetch(endpoint);
    const json = await response.json();
    return json.data;
  };

  let count = parseInt(localStorage.getItem("heartCount")) || 0;
  let isActive = localStorage.getItem("heartActive") === "true";

  function toggleHeart() {
    if (isActive) {
      count -= 1;
    } else {
      count += 1;
    }
    isActive = !isActive;
    localStorage.setItem("heartCount", count);
    localStorage.setItem("heartActive", isActive);
  }
</script>


<main>
  <article>
    {#await getArticle(article_id)}
      <p>En chargement. Je cherche les données sur l'api...</p>
    {:then article}
      <!-- doit apparaitre seulement pour les auteurs -->
      <a aria-label="Éditer l'article" use:link
      href={`/modification/${article.id}`}
        ><i class="fa-solid fa-pen-to-square" /></a
      >
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
          aria-label="Date de publication">
          {new Date(article.date_created).toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric"
          })}
        </time> <span aria-hidden="true"> || </span>

          <cite title="{article.users_id.pseudo}" aria-label="Auteur"
            >{article.users_id.pseudo}</cite
          >
        </aside>
      </footer>
      {/await}
      <div class="heart" class:active={isActive} on:click={toggleHeart}>
        <span class="heart-count">{count}</span>
        <i class="fa-regular fa-heart" id="heart-empty" />
        <i class="fa-solid fa-heart hidden" id="heart-filled" />
      </div>
  </article>

  <CommentsArticlePage {article_id}/>
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
