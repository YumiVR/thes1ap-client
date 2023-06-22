<script>
import {test_fn} from "./network.ts";

</script>

{#if err_msg != null}
<div>{err_msg}<button on:click={clear_error}>Ok</button></div>
{/if}
<link rel="stylesheet" href="/styles.css">
<div class="background">
  <form class="login-form">
    <h1>Log in to The S1ap</h1>
    <input type="text" placeholder="Username" required bind:value={uname}>
    <input type="password" placeholder="Password" required bind:value={pword}>
    <button type="submit" on:click={test_fn}>Log in</button>
    <div class="signup-link">
      Don't have an account? <a href="/home">Sign up</a>
    </div>
  </form>
</div>
