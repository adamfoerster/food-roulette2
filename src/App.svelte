<script lang="ts">
  import "smelte/src/tailwind.css";
  import Button from "smelte/src/components/Button";
  import Tabs from "smelte/src/components/Tabs";

  let user = { displayName: "" };

  const routes = [
    { id: 1, text: "Votar", icon: "store" },
    { id: 1, text: "Monitorar", icon: "poll" },
    { id: 1, text: "Estatísticas", icon: "trending_up" },
    { id: 1, text: "Achievements", icon: "thumb_up" }
  ];

  const login = () => {
    // service.login();
  };

  const logout = () => {
    // service.logout();
  };

  const getUser = () => {
    // return service.getUser();
  };

  const openMenu = () => {
    // bottomSheet.open(menu);
    // setTimeout(() => bottomSheet.dismiss(), 3000);
  };
</script>

<style>
  #body {
    position: fixed;
    width: 100vw;
    height: 100vh;
    box-sizing: border-box;
  }
  #content {
    height: calc(100vh - 64px);
    overflow: auto;
  }

  .example-spacer {
    max-width: calc(100% - 35px);
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }
</style>

<div id="body">
  {#if getUser()}
    <div>
      <div class="toolbar">
        <i on:click={openMenu}>reorder</i>
        <span>Olá {user.displayName}, onde vamos comer hoje?</span>
        <i on:click={logout}>exit_to_app</i>
      </div>
      <div id="content">
        <div id="inner">
          <router-outlet />
        </div>
      </div>
    </div>
  {:else}
    <div id="showLogin">
      <br />
      <div class="card">
        <p>Please login.</p>
        <Button on:click={login}>Login with Google</Button>
      </div>
    </div>
  {/if}
  <div id="menu">
    <Tabs items={routes} />
  </div>

</div>
