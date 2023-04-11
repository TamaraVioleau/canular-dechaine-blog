<script>
  import { link } from "svelte-spa-router";
      // JS pour le menu burger
      let searchLinksVisible = false;
  const handleClick = () => {
    searchLinksVisible = !searchLinksVisible;
  };
 //Lorsque l'utilisateur est connecté
  const isLogged = window.localStorage.getItem("token") != null;
  const logins = [
    {
      iconlog: isLogged
        ? "fa-solid fa-right-from-bracket"
        : "fa-solid fa-right-to-bracket",
      iconprofil: isLogged ? "iconprofil" : "",
      text: isLogged ? "Se déconnecter" : "Se connecter",
      url: "/connexion",
    },
  ];

  //Récupération des catégories de la BDD
  let categories = [];

  const getCategories = async () => {
    const endpoint = import.meta.env.VITE_URL_DIRECTUS + "/items/categories";
    const response = await fetch(endpoint);
    const json = await response.json();

    // Récupération des données et incrémentation dans le tableau
    categories = json.data;
  };
  getCategories();
</script>

<nav>
  <a use:link href="/"
    ><img src="src\assets\logo-site.png" alt="logo site" id="logo" /></a
  >

  <div class="nav__navigation">
    <div class="searchlogin">
      <div class="navigation__search">
        <!-- Ajout du chemin de la page dans action -->
        <form action="" id="formsearch">
          <input type="text" placeholder="Search.." name="search" id="search" />
          <button type="submit" id="buttonsearch">
            <i class="fa-solid fa-magnifying-glass" />
          </button>
        </form>
      </div>

      {#each logins as login}<div class="navigation__login">
          <a use:link href={login.url} id="login">
            <button type="submit" id="buttonlogin">
              <span id="logtext">{login.text}</span></button
            >
            <i id="iconlog" class={login.iconlog} />
          </a>
        </div>
        <div id="iconprofil" class={login.iconprofil} />
      {/each}

      <!-- ici le bouton du menu responsive -->
      <div id="menuicon" on:click={handleClick}>
        <i class="fa-solid fa-bars" id="menu" />
      </div>

      <div class="searchandlinks" class:visible={searchLinksVisible}>
        {#each logins as login}<div class="navigation__login--mobile">
            <a use:link href={login.url} id="login--mobile">
              <button type="submit" id="buttonlogin--mobile">
                <span id="logtext--mobile">{login.text}</span></button
              >
              <i id="iconlog" class={login.iconlog} />
            </a>
          </div>
        {/each}

        <div class="navigation__search" id="navigation__mobile">
          <!-- Ajout du chemin de la page dans action -->
          <form action="" id="formsearch">
            <input
              type="text"
              placeholder="Search.."
              name="search"
              id="search"
            />
            <button type="submit" id="buttonsearch">
              <i class="fa-solid fa-magnifying-glass" />
            </button>
          </form>
        </div>
        <ul>
          {#each categories as category}
          <li>
            <a use:link href={`/articles/${category.id}`}>{category.name}</a>
          </li>
          {/each}
        </ul>
      </div>
      <!-- ici fini le bouton du menu responsive -->
    </div>

    <div class="gridlinks">
      <ul>
        {#each categories as category}
          <li>
            <a use:link href={`/articles/${category.id}`}>{category.name}</a>
          </li>
        {/each}
      </ul>
    </div>
  </div>
</nav>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";
  nav {
    @extend %glassmorphism;
    z-index: 10000000;
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: $color-black;
    background-color: $color-white;
    border-radius: 0;
    height: auto;
    padding: 3rem;
    font-family: $police;
    #logo {
      height: 100px;
      margin-right: 1rem;
      @media screen and (min-width: 770px) {
        height: 200px;
      }
    }

    .nav__navigation {
      .searchlogin {
        display: flex;
        justify-content: right;
        height: 50px;
        .navigation__search {
          display: none;
          @media screen and (min-width: 770px) {
            margin-right: 3rem;
            display: flex;
            align-items: center;
            height: 100%;
          }
          #formsearch {
            border: 1px solid $color-black;
            height: auto;
            display: flex;
            border-radius: 5px;
            input {
              border-radius: 5px;
            }
            #search {
              border: none;
              padding: 1.5rem;
            }
            #buttonsearch {
              border: none;
              width: 4.5rem;
              background: $color-greenlight;
              border-left: 1px solid $color-black;
              i {
              }
            }
          }
        }
        .navigation__login {
          display: none;
          @media screen and (min-width: 580px) {
            display: flex;
            #login {
              display: flex;
              align-items: center;
              width: auto;
              height: 100%;
              justify-content: right;
              gap: 2rem;
              padding: 0 3rem;
              border: 1px solid white;
              border-radius: 5px;
              text-decoration: none;
              box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
              font-size: 3rem;

              #buttonlogin {
                border-radius: 10px;
                border: none;
                font-weight: bolder;
                height: 100%;
                background: none;
                font-size: 1.8rem;
                cursor: pointer;
                display: none;
                @media screen and (min-width: 1024px) {
                  display: block;
                }
                #logtext {
                }
              }
              #iconlog {
                height: 3.5rem;
                color: $color-black;
                display: flex;
                align-items: center;
              }
            }
          }
        }

        .iconprofil {
          display: flex;
          align-items: center;
          width: auto;
          height: 100%;
          justify-content: right;
          gap: 2rem;
          padding: 0 3rem;
          border: 1px solid white;
          border-radius: 5px;
          text-decoration: none;
          box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
          color: $color-black;
          margin-left: 3rem;
          font-size: 3rem;
        }
        .iconprofil::before {
          content: "\f406";
          font-family: "FontAwesome";
        }

        #menu {
          font-size: 5rem;
          cursor: pointer;
          margin-left: 3rem;
          @media screen and (min-width: 770px) {
            display: none;
          }
        }
      }
    }
    .gridlinks {
      display: none;
      @media screen and (min-width: 770px) {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
        grid-auto-flow: dense;
        justify-items: center;
        align-items: center;
        margin-top: 5rem;
      }
      ul {
        @media screen and (min-width: 770px) {
          list-style: none;
          padding: 0;
          margin: 0;
          display: flex;
          flex-wrap: wrap;
          justify-content: center;
          text-align: center;
         }
        li {
          @media screen and (min-width: 770px) {
            border-radius: 10px;
            padding: 1rem;
            margin: 0.5rem;
            min-width: 110px;
            font-size: 2rem;
            a {
              text-decoration: none;
              position: relative;
              color: $color-black;
              &:after {
                content: "";
                position: absolute;
                left: 0;
                bottom: -5px;
                width: 100%;
                height: 2px;
                background-color: $color-greenlight;
                transform: scaleX(0); /* Masque le soulignement au départ */
                transition: transform 0.2s ease-in-out; /* Transition fluide */
                transform-origin: left; /* Modifie l'orientation du soulignement ici gauche à droite */
              }
              &:hover:after {
                transform: scaleX(1); /* Affiche le soulignement au survol */
              }
            }
          }
        }
      }
    }
  }

  //ICI COMMENCE LE SASS DU MENU HAMBURGER
  .searchandlinks {
    font-size: 2rem;
    position: absolute;
    width: 100%;
    top: 16rem;
    right: 0rem;
    background-color: $color-white;
    padding: 3rem;
    display: none;

    .navigation__login--mobile {
      margin: 2rem;
      #login--mobile {
        display: flex;
        align-items: center;
        justify-content: center;
        width: auto;
        height: 100%;
        gap: 2rem;
        padding: 2rem;
        border: 1px solid white;
        border-radius: 5px;
        text-decoration: none;
        box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
        font-size: 3rem;
        @media screen and (min-width: 580px) {
          display: none;
        }
        #buttonlogin--mobile {
          border-radius: 10px;
          border: none;
          font-weight: bolder;
          height: 100%;
          background: none;
          font-size: 1.8rem;
          cursor: pointer;
        }
        #logtext--mobile {
          display: block;
        }
        #iconlog {
          height: 3.5rem;
          color: $color-black;
          display: flex;
          align-items: center;
        }
      }
    }

    #navigation__mobile {
      display: flex;
      justify-content: center;
      
    }
    ul {
      li {
        padding: 2rem;
        a {
          text-decoration: none;
          position: relative;
          color: $color-black;
          &:after {
            content: "";
            position: absolute;
            left: 0;
            bottom: -5px;
            width: 100%;
            height: 2px;
            background-color: $color-greenlight;
            transform: scaleX(0); /* Masque le soulignement au départ */
            transition: transform 0.2s ease-in-out; /* Transition fluide */
            transform-origin: left; /* Modifie l'orientation du soulignement ici gauche à droite */
          }
          &:hover:after {
            transform: scaleX(1); /* Affiche le soulignement au survol */
          }
        }
      }
    }
  }
  .searchandlinks.visible {
    display: block;

    @media screen and (min-width: 770px) {
      display: none;
    }
  }
</style>
