<script>
import {err_msg, clear_error, log_in} from "./network.ts";
let uname = "";
let pword = "";
</script>

<link rel="stylesheet" href="/styles.css">
<div class="background">
  {#if err_msg != null}
    <div>{err_msg}<button on:click={clear_error}>Ok</button></div>
  {/if}
  <form class="login-form">
    <h1>Log in to The S1ap</h1>
    <input type="text" placeholder="Username" required bind:value={uname}>
    <input type="password" placeholder="Password" required bind:value={pword}>
    <button type="submit" on:click={() => log_in(uname, pword)}>Log in</button>
    <div class="signup-link">
      Don't have an account? <a href="/signup">Sign up</a>
    </div>
  </form>
</div>
