<script>
</script>

<nav>
  <a href="/"
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

      <div class="navigation__login">
        <a href="/" id="login">
          <button type="submit" id="buttonlogin">Login</button>
          <img
            src="src\assets\avatar-default.png"
            alt="avatar par défaut"
            id="avatar"
          />
        </a>
      </div>

      <i class="fa-solid fa-bars" id="menu" />
    </div>

    <div class="gridlinks">
      <ul>
        <li><a href="/">Economie</a></li>
        <li><a href="/">Sciences</a></li>
        <li><a href="/">Ecologie</a></li>
        <li><a href="/">Santé</a></li>
        <li><a href="/">Culture</a></li>
        <li><a href="/">Tourisme</a></li>
        <li><a href="/">Animaux</a></li>
        <li><a href="/">People</a></li>
        <li><a href="/">Astrologie</a></li>
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
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #312140;
    background-color: #f8f8f8;
    border-radius: 0;
    height: auto;
    padding: 3rem;
    font-family: Tahoma;
    #logo {
      height: 200px;
      margin-right: 1rem;
    }

    .nav__navigation {
      .searchlogin {
        display: flex;
        justify-content: right;
        height: 50px;
        .navigation__search {
          margin-right: 3rem;
          display: flex;
          align-items: center;
          height: 100%;
          #formsearch {
            border: 1px solid #312140;
            height: auto;
            display: flex;
            #search {
              border: none;
              padding: 1.5rem;
            }
            #buttonsearch {
              border: none;
              width: 4.5rem;
              background: rgba(136, 217, 143, 0.23);
              border-left: 1px solid #312140;
              i {
              }
            }
          }
        }
        .navigation__login {
          #login {
            display: flex;
            align-items: center;
            width: auto;
            height: 100%;
            justify-content: right;
            gap: 2rem;
            padding: 0 3rem;
            background: rgb(136 217 143 / 70%);
            border: 1px solid white;
            border-radius: 5px;
            text-decoration: none;
            box-shadow: 0 2px 5px 0 rgba(31, 38, 135, 0.45);
            #buttonlogin {
              border-radius: 10px;
              border: none;
              font-weight: bolder;
              height: 100%;
              background: none;
              font-size: 1.8rem;
              cursor: pointer;
            }
            #avatar {
              height: 35px;
            }
          }
        }
        @media screen and (max-width: 770px) {
          #menu {
          font-size: 5rem;
          cursor: pointer;
          }
        }
      }
    }
    .gridlinks {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      grid-auto-flow: dense;
      justify-items: center;
      align-items: center;
      margin-top: 5rem;
      ul {
        @media screen and (min-width: 770px) {
          list-style: none;
          padding: 0;
          margin: 0;
          display: flex;
          flex-wrap: wrap;
          justify-content: center;
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
              color: #312140;
              &:after {
                content: "";
                position: absolute;
                left: 0;
                bottom: -5px;
                width: 100%;
                height: 2px;
                background-color: rgba(136, 217, 143, 0.23);
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
</style>
