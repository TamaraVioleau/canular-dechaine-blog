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
      laudantium unde! Lorem ipsum dolor sit, amet consectetur adipisicing elit.
      Possimus aut sequi magni tempore qui earum. Ad facere deleniti molestias
      aliquid quod eius veritatis voluptate, deserunt accusamus, fugiat veniam
      inventore tempora.
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
  <div class="buttons">
    <input
      class="submit"
      type="submit"
      name="submit"
      value="Envoyer"
      spellcheck="false"
      aria-label="Envoyer article"
    />
  </div>
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
      padding-inline: 15vw;
    }
    @media screen and (min-width: 1024px) {
      display: flex;
      justify-content: center;
      flex-direction: column;
      max-width: 910px;
      min-width: 910px;
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
    line-height: 2rem;
    padding: 1rem;
    text-align: left;
    margin: 1rem;
  }

  .write {
    display: block;
    @extend %glassmorphism;
    margin: 3rem;
    padding: 2rem;

    @media screen and (min-width: 1024px) {
      display: flex;
      align-self: center;
      justify-content: center;
      flex-direction: column;
      max-width: 910px;
      min-width: 910px;
    }
  }

  #textarea {
    display: block;
    height: 15rem;
    width: 95%;
    margin: 2rem auto;
    resize: vertical;
    font-size: 1.6rem;
    min-height: 100px;
    border-radius: 5px;
    border: 1px solid #ccc;
    padding: 2rem;
  }

  .buttons {
    display: flex;
    justify-content: center;
    .submit {
      @extend %button;
      min-width: 220px;
    }
    .submit:active {
      @extend %buttonactive;
    }
  }
</style>
