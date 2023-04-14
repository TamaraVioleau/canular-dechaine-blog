<script>
  import { link } from "svelte-spa-router";
  export let article_id;
  let comments = [];

  let commentContent = "";

  $: if (article_id) {
    getComments();
  }

  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;

  const getComments = async () => {
    const endpoint = `${API_BASE_URL}/items/comments?filter[articles_id][_eq]=${article_id}`;
    console.log("URL d'endpoint pour les commentaires :", endpoint); // Log de débogage
    const response = await fetch(endpoint);
    const json = await response.json();
    console.log("Réponse JSON :", json); // Log de débogage
    comments = json.data;

    // Vérifiez si 'json.data' est un tableau avant de l'affecter à 'comments'
    if (Array.isArray(json.data)) {
      comments = json.data;
    } else {
      console.error("La réponse de l'API n'est pas un tableau d'objets.");
      comments = [];
    }
  };

  const postComment = async () => {
    const response = await fetch(
      import.meta.env.VITE_URL_DIRECTUS + "/items/comments",
      {
        method: "POST",
        headers: {
          "content-type": "application/json",
          Authorization: "Bearer " + localStorage.getItem("token"),
        },
        body: JSON.stringify({
          content: commentContent,
          articles_id: article_id,
        }),
      }
    );
    const json = await response.json();
    return json.data;
  };

  const handleSubmitForm = async (event) => {
    event.preventDefault();
    const comment = await postComment();
    comments.push(comment);
    comments = [...comments];
    commentContent = "";
  };
</script>

<section>
  {#each comments as comment}
    <article>
      <header>
        <img src="src\assets\avatar-membres.png" alt="avatar du membre" />
        <aside
          class="aside__dateauthor"
          aria-label="Date de publication et auteur"
        >
          <time datetime="2023-04-05">
          {new Date(comment.date_created).toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric"
          })}</time
          >
          <span aria-hidden="true"> || </span>
          <cite title="nom de l'auteur">Lucie Fer</cite>
        </aside>
      </header>
      <p>
        {comment.content}
      </p>
    </article>
  {/each}
</section>

<div class="write">
  <form on:submit={handleSubmitForm}>
    <label for="textarea" />
    <textarea
      bind:value={commentContent}
      name="textarea"
      id="textarea"
      spellcheck="true"
      placeholder="Ecrire ici pour commenter l'article"
    />
    <button>
      <input
        class="submit"
        type="submit"
        name="submit"
        value="Envoyer"
        spellcheck="true"
        aria-label="Envoyer article"
      />
    </button>
  </form>
</div>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  section {
    display: block;
    @extend %glassmorphism;
    margin: 3rem;
    padding: 2rem;
    align-self: center;
    @media screen and (min-width: 770px) {
      padding-inline: 17vw;
    }
    @media screen and (min-width: 1024px) {
      display: flex;
      justify-content: center;
      flex-direction: column;
      max-width: 910px;
      min-width: 910px;
      padding-inline: 15vw;
    }
    @media screen and (min-width: 1440px) {
      padding-inline: 10vw;
    }
  }

  header {
    display: flex;
    padding: 1rem;
    margin: 1rem;
    align-items: center;
    img {
      max-width: 50px;
      margin-right: 2rem;
      border-radius: 100%;
      outline: 2px solid white;
      box-shadow: 0 2px 10px 0 rgb(31 38 135 / 45%);
    }
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
  p {
    @extend %p;
    padding: 1rem;
    margin: 1rem;
  }

  .write {
    display: flex;
    justify-content: center;
    flex-direction: column;
    @extend %glassmorphism;
    margin: 3rem;
    padding: 2rem;
    @media screen and (min-width: 1024px) {
      max-width: 910px;
      min-width: 910px;
      align-self: center;
    }
  }

  #textarea {
    display: block;
    height: 15rem;
    width: 95%;
    margin: 2rem auto;
    resize: vertical;
    min-height: 100px;
    border-radius: 5px;
    border: 1px solid #ccc;
    padding: 2rem;
    @extend %p;
  }

  button {
    display: flex;
    justify-content: center;
    background: transparent;
    border: none;
    max-width: 100%;
    .submit {
      @extend %button;
      min-width: 220px;
      box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
    }
    .submit:active {
      @extend %buttonactive;
    }
    .submit:hover {
      background-color: $color-greenlight;
    }
  }
</style>
