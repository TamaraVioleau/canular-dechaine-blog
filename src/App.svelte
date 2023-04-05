<script>
  import Homepage from "./lib/HomePage.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import Footer from "./lib/Footer.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import Navbar from "./lib/Navbar.svelte";
</script>

<Navbar/>

  <Register />
<PageProfilAuthors />
<PageProfilMembers /> 

<!-- <Homepage />
<ModifiedArticle />
<PageArticles />

<SearchPage />
  
 -->
<Footer />
<style lang="scss">
</style>
