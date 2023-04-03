<script>
</script>

<nav>
  <img src="src\assets\logo-site.png" alt="logo site" id="logo"/>

  <div class="nav__navigation">
    <header>
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
    </header>

    <div class="gridlinks">
      <ul>
        <li>Actualités</li>
        <li>Economie</li>
        <li>Sciences</li>
        <li>Ecologie</li>
        <li>Santé</li>
        <li>Culture</li>
        <li>Tourisme</li>
        <li>Animaux</li>
        <li>People</li>
        <li>Astrologie</li>
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
    align-items: center;
    color: #312140;
    background-color: #f8f8f8;
    border-radius: 0;

    height: auto;
    padding: 3rem;
    font-family:  Calibri, sans-serif;
    #logo{
      height:200px;
    }
    header {
      display: flex;
      justify-content: right;
      .navigation__search {
        margin-right: 3rem;
        display: flex;
        align-items: center;
        #formsearch {
          border: 1px solid #312140;
          height: 3rem;
          display: flex;
          #search {
            border: none;
          }
          #buttonsearch {
            border: none;
            width: 3rem;
            background: rgba(136, 217, 143, 0.23);
            border-left:1px solid #312140;
            i {
            }
          }
        }
      }
      .navigation__login {
        display: flex;
        align-items: center;
        #login {
          display: flex;
          align-items: center;
          #buttonlogin {
padding: 1rem 10rem;
            border-radius: 10px;
            border: none;
            background: rgba(136, 217, 143, 0.23);
            font-weight: bolder;
          }
          #avatar {
            height: 50px;

          }
        }
      }
    }
    .gridlinks {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      grid-auto-flow: dense;
      grid-gap: 1rem;
      justify-items: center;
      align-items: center;
      margin-top: 5rem;
      ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        li {
          background-color: #eee;
          background-color: #eee;
          border-radius: 10px;
          padding: 1rem;
          text-align: center;
          font-size: 1.2rem;
          font-weight: bold;
          margin: 0.5rem;
          min-width: 150px;
        }
      }
    }
  }
</style>
