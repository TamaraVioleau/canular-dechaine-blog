<script>
</script>

<nav>
  <img src="src\assets\logo-site.png" alt="logo site" />

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

    <div class="grid">
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
  nav {
    display: flex;
    height: 200px;
    padding: 3rem;
    header {
      display: flex;
      justify-content: right;
      .navigation__search {
        margin-right: 3rem;
        display: flex;
        align-items: center;
        #formsearch {
          border: 1px solid black;
          height: 3rem;
          display: flex;
          #search {
            border: none;
          }
          #buttonsearch {
            border: none;
            width: 3rem;
            i {
            }
          }
        }
      }
      .navigation__login {
        display: flex;
        align-items: center;
        background-color: green($color: #000000);
        #login {
          display: flex;
          align-items: center;
          #buttonlogin {
            height: 3rem;
            border: none;
            background: none;
          }
          #avatar {
            height: 50px;
          }
        }
      }
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      grid-auto-flow: dense;
      grid-gap: 1rem;
      justify-items: center;
      align-items: center;
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
