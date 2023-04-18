<script>
 import { onMount } from "svelte";
  const API_BASE_URL = import.meta.env.VITE_URL_DIRECTUS;


  //Récupération du nombre de commentaires
  let userData = {};
  let commentsCount = "";

  const getAuthorCommentsCount = async (authorId) => {
    try {
      const response = await fetch(`${API_BASE_URL}/items/comments?filter[users_id][_eq]=${authorId}`);
      if (response.ok) {
        const json = await response.json();
        return json.data.length;
      } else {
        console.error("Failed to fetch author's articles");
        return 0;
      }
    } catch (error) {
      console.error(error);
      return 0;
    }
  };

  onMount(async () => {
    const token = window.localStorage.getItem("token");

    if (!token) {
      // Redirigez l'utilisateur vers la page de connexion si nécessaire
    } else {
      try {
        const response = await fetch(`${API_BASE_URL}/users/me`, {
          headers: {
            Authorization: `Bearer ${token}`,
          },
        });

        if (response.ok) {
          userData = await response.json();
          userData = userData.data;

          // Récupère le nombre d'articles écrits par l'auteur connecté
          commentsCount = await getAuthorCommentsCount(userData.id);
        } else {
          console.error("Failed to fetch user data");
        }
      } catch (error) {
        console.error(error);
      }
    }
  });
</script>

<wrapper class="wrapper__right">
  <section class="section__statistics" aria-labelledby="statistiques">
    <article class="article__statistics">
      <h3 id="statistiques">Statistiques :</h3>
      <ol>
        <li>
          <h4>Tous mes commentaires :</h4>
          <p>{commentsCount} commentaires</p>
        </li>
        <li>
          <h4>Tous mes likes :</h4>
          <p>XX likes</p>
        </li>
      </ol>
    </article>
  </section>
</wrapper>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  .wrapper__right {
    min-width: 390px;
    .section__statistics {
      @extend %glassmorphism;
      @extend %paddingprofilregister;
      margin-top: 2rem;
      @media screen and (min-width: 580px) {
        padding: 3.5rem;
      }
      @media screen and (min-width: 1024px) {
        margin-top: 0;
        min-height: 607px;
      }
      @media screen and (min-width: 1440px) {
        min-height: 526px;
      }

      .article__statistics {
        background-color: $color-white;
        padding: 1.5rem;
        max-width: 500px;
        margin: auto;
        h3 {
          font-size: 2rem;
          font-weight: bolder;
          margin-bottom: 2rem;
        }
        ol {
          list-style: disc;
          margin-left: 4rem;
          li {
            margin-bottom: 1rem;
            h4 {
              font-weight: bold;
              margin-bottom: 1rem;
            }
          }
        }
      }
    }
  }
</style>
