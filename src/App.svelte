<script>
  import Footer from "./lib/Footer.svelte";
  import ErrorPage from "./lib/ErrorPage.svelte";
  import PageArticles from "./lib/PageArticles.svelte";
  import PageProfilAuthors from "./lib/PageProfilAuthors.svelte";
  import PageProfilMembers from "./lib/PageProfilMembers.svelte";
  import Register from "./lib/Register.svelte";
  import ModifiedArticle from "./lib/ModifiedArticle.svelte";
  import SearchPage from "./lib/SearchPage.svelte";
  import PageArticle from "./lib/PageArticle.svelte";
  import Navbar from "./lib/Navbar.svelte";
  import CommentsArticlePage from "./components/CommentsArticlePage.svelte";
  import UpDown from "./components/UpDown.svelte";
  import PaginationBar from "./components/PaginationBar.svelte";


</script>
<Navbar/>
<PageArticle/>
<UpDown/>
<SearchPage/>
<PageProfilAuthors/>
<PageProfilMembers/>
<Register/>
<PageArticles/>
<ModifiedArticle/>
<PaginationBar/>
<Footer/>



<!--

 -->

<style lang="scss">
</style>
