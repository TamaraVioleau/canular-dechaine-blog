<script>
  import { link } from "svelte-spa-router";
</script>

<main>
  <article>
    <h3>A propos de nous</h3>
    <p class="paragraph" aria-label="introduction à propos de nous">
      Le <strong>Canular déchainé</strong> est un blog humoristique et satirique,
      créé dans le cadre d'un projet de fin de formation chez O'Clock, une formation
      de développeur web et web mobile full stack de six mois. La fin de formation
      a lieu le 24 avril 2023. Le contenu de ce site est constitué de fausses informations,
      à ne pas prendre au premier degré, et vise à sensibiliser les internautes sur
      l'importance de vérifier la véracité des informations et de les analyser avec
      esprit critique.
    </p>

    <p class="paragraph" aria-label="équipe fondatrice">
      L'équipe fondatrice du Canular Déchaîné est composée de Sébastien,
      Frédéric et Tamara, trois passionnés d'actualité et d'humour, qui
      souhaitent offrir une approche légère et décalée de l'information.
    </p>

    <h4>Rôles des membres de l'équipe</h4>
    <p class="paragraph" aria-label="Tamara">
      <strong>Tamara : Product Manager / Product Owner</strong>
      Tamara est responsable de la gestion globale du projet pour s’assurer que les
      objectifs sont atteints. Elle planifie les étapes nécessaires en coordonnant
      les équipes.
    </p>
    <p class="paragraph" aria-label="Sébastien">
      <strong>Sébastien : Lead Dev Front</strong>
      Sébastien supervise la partie front-end. Il effectue les choix techniques sur
      la partie front et assure une expérience utilisateur optimale.
    </p>

    <p class="paragraph" aria-label="Frédérick">
      <strong>Frédéric : Lead Dev Back</strong>
      Fred supervise la partie back-end. Il effectue les choix techniques sur la
      partie back et assure la bonne communication entre les différentes parties
      du projet.
    </p>
    <p class="paragraph" aria-label="Equipe">
      <strong>Équipe entière : Git Master </strong>L'équipe maîtrise l'outil GIT
      et vient en aide en cas de souci avec celui-ci. L'équipe est également la
      seule autorisée à intervenir sur la branche master.
    </p>
    <p class="paragraph" aria-label="Equipe">
      <strong>Équipe entière : Référent techno</strong> L'équipe s'informe et se
      documente sur les technologies utilisées, leur sémantique et leur utilisation.
      Les informations sont ensuite restituées au groupe pour assurer une cohérence
      technique et une qualité optimale du projet.
    </p>

    <h4>Accessibilité du Canular Déchaîné</h4>
    <p class="paragraph" aria-label="Equipe">
      Au Canular Déchaîné, nous accordons une grande importance à
      l'accessibilité de notre site pour tous les utilisateurs. Nous sommes
      conscients que nos lecteurs ont des besoins divers et des spécificités
      personnelles, notamment les handicaps. C'est pourquoi nous nous sommes
      engagés à respecter l<strong>
        es normes d'accessibilité a11y et RGAA 4.1 (Référentiel Général
        d'Amélioration de l'Accessibilité)
      </strong> pour offrir une expérience utilisateur inclusive et adaptée à chacun.
    </p>
    <p class="paragraph" aria-label="Equipe">
      Voici quelques-uns des points clés de notre engagement en matière
      d'accessibilité :
    </p>

    <ul>
      <li class="titre-li"><strong>Handicaps moteurs :</strong></li>
      <ul>
        <li>Utilisation de lecteurs d'écran facilitée par les aria-label.</li>
        <li>Contenus aérés et espacés.</li>
        <li>
          Zones cliquables larges et espacées pour faciliter la navigation.
        </li>
        <li>
          Limitation des contenus dynamiques qui demandent beaucoup de
          mouvements de souris (menus déroulants).
        </li>
        <li>
          Proposition d'auto-complétion et de raccourcis pour effectuer des
          actions.
        </li>
        <li>Actions réalisables au clavier.</li>
      </ul>
      <li class="titre-li"><strong>Dyslexie :</strong></li>
      <ul>
        <li>
          Utilisation de polices sans empattement telles qu'Arial, Tahoma ou
          Verdana.
        </li>
        <li>Alignement du texte à gauche et non justifié.</li>
        <li>
          Éviction des contenus importants écrits en majuscules, italique ou
          souligné, pour faciliter la lecture.
        </li>
        <li>
          Mise en place de l'autocorrection et de suggestions pour aider les
          utilisateurs à s'exprimer à l'écrit.
        </li>
      </ul>
      <li class="titre-li"><strong>Troubles de l'attention :</strong></li>
      <ul>
        <li>
          Limitation des animations ou possibilité pour l'utilisateur de les
          contrôler.
        </li>
      </ul>
      <li class="titre-li"><strong>Déficiences auditives :</strong></li>
      <ul>
        <li>
          Mise à disposition de sous-titres pour les contenus audiovisuels.
        </li>
      </ul>
      <li class="titre-li"><strong>Responsivité :</strong></li>
      <ul>
        <li>
          Adaptation du site pour une lecture optimale sur tous les types
          d'appareils (ordinateurs, tablettes, smartphones), pour répondre aux
          habitudes de lecture variées de notre public.
        </li>
      </ul>
    </ul>

    <h4>Mot de la fin</h4>
    <p class="paragraph" aria-label="but du canular déchainé">
      L'équipe du Canular Déchaîné travaille à créer des articles humoristiques
      qui parodient l'actualité et divertissent les lecteurs, tout en les
      faisant réfléchir sur les aspects sérieux de l'information. Le Canular
      Déchaîné s'adresse à un public large et diversifié, et s'efforce de rendre
      le site accessible à tous, en prenant en compte les spécificités diverses
      et personnelles de chaque utilisateur, notamment les handicaps.
    </p>
    <p class="paragraph" aria-label="mot de la fin">
      N'hésitez pas à nous contacter pour toute question ou suggestion, et
      n'oubliez pas de vous inscrire pour profiter de fonctionnalités
      supplémentaires, telles que la possibilité de commenter des articles et de
      sauvegarder des articles dans vos favoris. Nous vous souhaitons une bonne
      lecture et de nombreux fous rires !
    </p>

    <footer>
      <aside aria-label="Date de publication et auteur">
        <time datetime="24/04/2023" aria-label="Date de publication">
          {new Date().toLocaleDateString("fr-FR", {
            day: "numeric",
            month: "numeric",
            year: "numeric",
          })}
        </time> <span aria-hidden="true"> || </span>

        <cite title="Canular Déchainé" aria-label="Auteur"
          >Canular Déchainé</cite
        >
      </aside>
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
      h3 {
        @extend %h3;
      }
      h4 {
        @extend %h4;
      }
      .paragraph {
        font-family: $police;
        padding: 1rem 2rem;
        @extend %p;
      }
      ul {
        li {
          font-family: $police;
          padding: 0 2rem;
          @extend %p;
        }
        .titre-li {
          list-style-type: decimal;
          padding-top: 2rem;
        }
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
    }
  }
  strong {
    font-weight: bolder;
  }
</style>
