<script>
  import { onMount } from "svelte";

  let scrollTop = 0;

  onMount(() => {
    window.addEventListener("scroll", handleScroll);
  });

  function handleScroll(event) {
    scrollTop = event.target.scrollingElement.scrollTop;
  }

  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  function scrollToBottom() {
    window.scrollTo({ top: document.body.scrollHeight, behavior: "smooth" });
  }
</script>

<button on:click={scrollToTop}><i class="fi fi-sr-caret-circle-up"></i></button>
<button on:click={scrollToBottom}><i class="fi fi-sr-caret-circle-down"></i></button>

<style lang="scss">
  @import "../utils/extends";
  @import "../utils/mixins";
  @import "../utils/variables";

  button {
  display: flex;
  align-items: center; // Centrer verticalement
  justify-content: center; // Centrer horizontalement
  z-index: 900000;
  position: fixed;
  right: 2rem;
  width: 5rem;
  height: 5rem;
  font-size: 1.5rem;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 50%;
  color: #666;
  cursor: pointer;
  transition: all 0.3s ease-in-out;

  &:hover {
    transform: translateY(-5px);
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  }

  &:focus {
    outline: none;
  }

  &:first-of-type {
    bottom: 8rem;
  }

  &:last-of-type {
    bottom: 2rem;
  }

  i{
    font-size: 3rem;
    top: 0.8rem;
    position: absolute;
  }
}

</style>
