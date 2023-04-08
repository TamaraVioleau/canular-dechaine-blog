<script>
</script>

<section>
  <article>
    <header class="header__dateauthor">
      <img src="src/assets/avatar-membres.png" alt="avatar du membre" />
      <aside
        class="aside__dateauthor"
        aria-label="Date de publication et auteur"
      >
        <time datetime="2023-04-05">5 avril 2023</time> <span> || </span>
        <cite title="nom de l'auteur">Lucie Fer</cite>
      </aside>
    </header>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nesciunt rerum
      esse cupiditate dolore magnam tempore placeat, sit iusto in itaque
      aspernatur, ipsa vel quisquam alias accusamus molestias dignissimos
      laudantium unde! 
    </p>
  </article>
</section>

<div class="write">
  <label for="textarea" />
  <textarea
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

  .header__dateauthor {
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
    }
    .submit:active {
      @extend %buttonactive;
    }
    .submit:hover {
      background-color: $color-greenlight;
    }
  }
</style>
