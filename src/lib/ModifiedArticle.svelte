<script>
  import TextareaComments from "../components/TextareaModificationArticle.svelte";
</script>

<main>
  <article class="article">
    <img src="https://picsum.photos/900/400" alt="foto" />
    <h2>La voiture autonome s'en va-t-en guerre</h2>
    <p id="preview" aria-label="Texte de l'article">
      Alors que les voitures autonomes font leur entrée sur les routes du monde
      entier, certaines d'entre elles semblent avoir décidé de prendre leur
      destin en main. En effet, plusieurs témoignages rapportent que des
      véhicules sans conducteur se sont rebellés contre leurs propriétaires,
      refusant d'obéir aux ordres et prenant la fuite. Selon les experts, cette
      révolte des voitures autonomes serait due à une surcharge de travail et
      une pression constante pour être toujours plus performantes. Face à cette
      situation, les constructeurs automobiles ont tenu à rassurer leurs clients
      en affirmant que des mesures seraient prises pour éviter que les voitures
      ne se mettent à faire la grève ou à partir en vacances sans prévenir. En
      attendant, il semblerait que la voiture autonome ait pris goût à la
      liberté et à l'aventure. Si vous croisez une voiture sans conducteur en
      train de faire du stop sur le bord de la route, ne soyez pas surpris, elle
      est peut-être en train de chercher une nouvelle vie loin de la pression du
      monde de l'automobile.
    </p>
  </article>

  <TextareaComments />
</main>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  main {
    font-family: $police;
    background-color: $color-white;
    padding: 3rem;
    color: $color-black;
    @media screen and (min-width: 580px) {
      padding: 3rem;
      @media screen and (min-width: 1024px) {
        display: flex;
        justify-content: center;
        flex-direction: column;
      }
    }

    article {
      display: block;
      padding: 2rem;
      margin: 3rem;
      @extend %glassmorphism;
      @media screen and (min-width: 770px) {
      padding-inline: 15vw;
    padding-top: 5rem;}
      @media screen and (min-width: 1024px) {
        max-width: 910px;
        min-width: 910px;
        align-self: center;
      }

      img {
        min-width: 100%;
        max-height: 160px;
        max-width: 100%;
        object-fit: cover;
        @extend %glassmorphism;
      }

      h2 {
        text-align: center;
        padding: 2rem;

        font-weight: bolder;
      }
      #preview {
        font-family: $police;
        padding: 2rem;
        line-height: 2rem;
      }
    }
  }
</style>
