<script>
import {browser} from '$app/environment';

let socket;

let uname = "KingJellyfish";
let pword = "12345";

let err_msg = null;

function log_in() {
    if (browser) {
        socket = new WebSocket("ws://localhost:2345")
        socket.addEventListener("open", (event) => {
            socket.send(JSON.stringify({"command": "login", "uname": uname, "passwd": pword}));
        });
        socket.addEventListener("message", (event) => {
            let obj = JSON.parse(event.data);
            
            if (obj["command"] == "login" && obj["status"] == FORBIDDEN) {
                err_msg = "Incorrect username or password! Try again.";
            } else if (obj["status"] != 200) {
                err_msg = "Command '" + obj["command"] + "' failed with error code " + obj["status"];
            } else {
                console.log(obj);
            }
        });
    }
}

function clear_error() {
    err_msg = null;
}
</script>

<p>test</p>
<a href="/home">test</a>
{#if err_msg != null}
<div>{err_msg}<button on:click={clear_error}>Ok</button></div>
{/if}
<button on:click={log_in}>Log in</button>