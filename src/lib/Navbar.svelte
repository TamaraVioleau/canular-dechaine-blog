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
            <i class="fa fa-search" />
          </button>
        </form>
      </div>

      <div class="navigation__login">
        <!-- Ajout du chemin de la page dans action -->
        <form action="" id="formlogin">
          <button type="submit" id="buttonlogin">Login</button>
          <img
            src="src\assets\avatar-default.png"
            alt="avatar par défaut"
            id="avatar"
          />
        </form>
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
        #formsearch {
          #search {
          }
          #buttonsearch {
            i {
            }
          }
        }
      }
      .navigation__login {
        #formlogin {
          #buttonlogin {
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
