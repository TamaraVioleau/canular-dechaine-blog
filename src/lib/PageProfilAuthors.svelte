<script>
</script>

<main>
  <!-- dans action mettre le nom de la page (ex: /profil)  -->
  <form action="" method="post" id="informations" name="informations">
    <section class="section__informations">
      <header>
        <img src="src\assets\avatar-authors.png" alt="avatar authors default" />
        <article class="article__pseudostatut">
          <h1>Jean Bonbeur</h1>
          <h2>Auteur</h2>
        </article>
      </header>

      <article>
        <label for="Nom">Nom : </label>
        <input type="text" name="Nom" id="Nom" />

        <label for="Prénom">Prénom : </label>
        <input type="text" name="Prénom" id="Prénom" />

        <label for="Lieu">Lieu : </label>
        <input type="text" name="Lieu" id="Lieu" />

        <label for="Date d'enregistrement">Date d'enregistrement : </label>
        <input
          type="text"
          name="Date d'enregistrement"
          id="Date d'enregistrement"
        />

        <label for="E-mail">E-mail : </label>
        <input type="text" name="E-mail" id="E-mail" />

        <label for="Mot de passe">Mot de passe : </label>
        <input type="text" name="Mot de passe" id="Mot de passe" />
      </article>
    </section>

    <section class="section__statistics">
      <article>
        <h3>Statistiques :</h3>
        <ol>
          <li>
            <h4>Tous mes articles :</h4>
            XX articles
          </li>
        </ol>
      </article>
    </section>

    <section class="section__writearticle">
      <article>
        <h3>Ecrire un article :</h3>
        <label for="category"> Catégorie :</label>
        <select id="category" name="category" required>
          <option value="0">Catégorie</option>
          <option value="1">Catégorie </option>
          <option value="2">Catégorie</option>
          <option value="3">Catégorie</option>
          <option value="4">Catégorie</option>
        </select>

        <label for="Lieu">Lieu : </label>
        <input type="text" name="Lieu" id="lieu" />

        <label for="Image" id="import">Avatar : </label>

        <input
          type="file"
          name="Image"
          id="image"
          accept="image/png, image/jpeg, image/WebpImage"
          title="Importer une image"
          aria-label="Importer une image"
        />

      </article>
    </section>

    <div class="buttons">
      <input
        class="submit"
        type="submit"
        name="submit"
        value="Enregistrer"
        spellcheck="false"
      />
      <input class="reset" type="reset" name="reset" value="Réinitialiser" />
    </div>
  </form>
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    font-family: Tahoma;
    background-color: #f8f8f8;
    padding: 2.3rem;
    form {
      .section__informations {
        @extend %glassmorphism;
        padding: 1.5rem;

        header {
          display: flex;
          justify-content: center;
          align-items: center;

          line-height: 3rem;

          img {
            height: 75px;
          }
          .article__pseudostatut {
            text-align: center;
            background: none;

            h1 {
              font-size: 3rem;
              font-weight: bolder;
            }
            h2 {
              font-size: 2.4rem;
            }
          }
        }

        article {
          margin-top: 2rem;
          background-color: #f8f8f8;
          padding: 1.5rem;
          display: flex;
          flex-direction: column;
          label {
            padding: 1rem 0;
            font-weight: bolder;
          }
          input {
            padding: 1rem 0;
            background: rgba(136, 217, 143, 0.23);
            border: 1px solid white;
            border-radius: 5px;
          }
          .buttons {
            display: flex;
            justify-content: center;
            margin-top: 2.3rem;
            gap: 1.5rem;
          }
        }
      }

      .section__statistics {
        @extend %glassmorphism;
        padding: 1.5rem;
        margin-top: 2.3rem;
        article {
          background-color: #f8f8f8;
          padding: 1.5rem;
          h3 {
            font-size: 2rem;
            font-weight: bolder;
            margin-bottom: 2rem;
          }
          ol {
            list-style: disc;
            margin-left: 4rem;
            li {
              h4 {
                font-weight: bold;
                margin-bottom: 1rem;
              }
            }
          }
        }
      }

      .section__writearticle {
        @extend %glassmorphism;
        padding: 1.5rem;
        margin-top: 2.3rem;
        article {
          background-color: #f8f8f8;
          padding: 1.5rem;

          margin-top: 2rem;
          background-color: #f8f8f8;
          padding: 1.5rem;
          display: flex;
          flex-direction: column;
          h3 {
            font-size: 2rem;
            font-weight: bolder;
            margin-bottom: 2rem;
          }
          label {
            padding: 1rem 0;
            font-weight: bolder;
          }
          select {
            width: 100%;
            padding: 1rem;
            font-size: 1.5rem;
            select option {
              background-color: red;
            }
          }
          input {
            padding: 1rem;
            background: rgb(136 217 143 / 23%);
            border: 1px solid white;
            border-radius: 5px;
          }

          input[type="file"]{
            font-size: 1.5rem;
          }


          #image {
            border: none;
            background: none;
            padding: 1rem 0;
          }
        }
      }

      .buttons {
        @extend %glassmorphism;
        margin-top: 2.3rem;
        display: flex;
        justify-content: center;
        padding: 2rem;
        input {
          padding: 1rem;
          margin: 1rem;
          background: rgb(136 217 143 / 23%);
          border: 1px solid white;
          border-radius: 5px;
          font-size: 1.5rem;
        }

      }
    }
  }
</style>
