<script>
  import { onMount } from "svelte";
  import PageProfilAuthors from "../lib/PageProfilAuthors.svelte";
  import ErrorPage from "../lib/ErrorPage.svelte";

  let hasAccess = false;

onMount(async () => {
  const role = await getUserRole();
  if (role === "645cbe7e-cdf9-409c-bc58-863ce065dfbb" || role === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5") {
    hasAccess = true;
  }
});

// Renvoie le rôle de l'utilisateur actuellement connecté
const getCurrentUserRole = async () => {
  const token = window.localStorage.getItem("token");
  if (!token) {
    return null;
  }

  const response = await fetch(`${import.meta.env.VITE_URL_DIRECTUS}/users/me`, {
    headers: {
      Authorization: `Bearer ${token}`
    }
  });
  const json = await response.json();
  return json.data.role;
};

// Appelle l'API pour obtenir le rôle de l'utilisateur connecté
const getUserRole = async () => {
  const role = await getCurrentUserRole();
  if (role === "645cbe7e-cdf9-409c-bc58-863ce065dfbb" || role === "e2a5bde2-09ab-44e4-8669-c9dc34c157e5") {
    return role;
  }
  return null;
};
</script>


{#if hasAccess}
  <PageProfilAuthors />
{:else}
  <p><ErrorPage /></p>
{/if}
