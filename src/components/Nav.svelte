<script>
    import Loader from "../components/Loader.svelte"
    import ProgressBar from "../components/ProgressBar.svelte"

    import { tweened } from "svelte/motion";
    import { cubicOut } from "svelte/easing";

    const progress = tweened(0, {
        duration: 400,
        easing: cubicOut,
    });

    export let segment;
    let syncing = false;

    function osTriggerMin() {
        alert("Min trigger");
    }
    function osTriggerResize() {
        alert("Resize trigger");
    }
    function osTriggerExit() {
        alert("Exit trigger");
    }

    function fakeSync(){
        syncing = !syncing;

        setTimeout(() => {
            progress.set(0.1);
        }, 1000);

        setTimeout(() => {
            progress.set(0.3);
        }, 3000);

        setTimeout(() => {
            progress.set(0.5);
        }, 5000);

        setTimeout(() => {
            progress.set(0.7);
        }, 7000);

        setTimeout(() => {
            progress.set(0.9);
        }, 8000);

        setTimeout(() => {
            progress.set(1);
        }, 9050);

        setTimeout(() => {
            syncing = false;
            progress.set(0);
        }, 10000);
    }
</script>

<style>
    nav {
        padding: 20px;
        height: 83px;
        max-height: 83px;
        background-color: #003795;
        color: #fff;
    }

    * {
        font-weight: bolder !important;
    }

    img {
        padding: 6px;
        height: 70%;
    }

    .windowButton {
        display: flex;
        flex: row;
        position: fixed;
        top: 0;
        right: 0;
        z-index: 10;
    }

    .os_button {
        padding: 10px;
        height: 20px;
        width: 36px;
        transition: 0.5s;
        cursor: pointer;
    }

    .os_button:hover {
        background-color: #0f50c0;
    }

    .nav_buttons {
        top: -1px;
    }

    a {
        text-decoration: none;
    }

    ul {
        position: fixed;
        margin: 0;
        padding: 0;
        margin-left: 109px;
        top: 106px;
        z-index: 30;
    }

    ul::after {
        content: "";
        display: block;
        clear: both;
    }

    li {
        display: flex;
        flex-direction: row;
        height: 40px;
        width: 170px;
        background: #FFFFFF;
        box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.25);
        border-radius: 1px;
        float: left;
        margin-right: 20px;
    }

    li p {
        padding: 9px;
        margin: 0px;
    }
    .icon {
        padding: 0px 10px;
    }

    .footer {
        position: fixed;
        display: flex;
        flex-direction: row;
        background-color: #003795;
        height: 50px;
        width: 100%;
        bottom: 0px;
        color: #fff;
        font-size: 14px;
        z-index: 30;
    }

    .sync {
        border: solid #fff 2px;
        border-radius: 30px;
        max-height: 21px;
        margin-left: 30px;
        margin-top: 10px;
        padding: 13px;
        background-color: #003795;
        transition: 0.3s;
        box-shadow: none;
    }

    .sync:hover {
        background-color: #205cc4;
    }

    .sync p {
        padding: 0px;
        margin: 0px;
        color: #fff;
        top: -10px;
        position: relative;
    }

    .container {
        display: flex;
        flex-direction: row;
        margin-left: 30px;
        width: 100%;
    }

    .container h3 {
        margin-top: 15px;
    }

    .loader {
        margin-top: 16px;
    }
</style>

<nav>
    <img src="svg/logo_text.svg" alt="">
</nav>

<div class="windowButton">
    <div on:click={osTriggerMin} class="os_button">
        <img class="icon" src="svg/os_min.svg" alt="">
    </div>

    <div on:click={osTriggerResize} class="os_button">
        <img class="icon" src="svg/os_resize.svg" alt="">
    </div>

    <div on:click={osTriggerExit} class="os_button">
        <img class="icon" src="svg/os_exit.svg" alt="">
    </div>
</div>

<div class="nav_buttons">
    <ul>
        <a href=".">
            <li>
                <img src="svg/nav_home.svg" alt="">
                <p>
                    Overview
                </p>
            </li>
        </a>
        <a href="data">
            <li>
                <img src="svg/nav_data.svg" alt="">
                <p>
                    Data
                </p>
            </li>
        </a>
        <a href="peers">
            <li>
                <img src="svg/nav_peers.svg" alt="">
                <p>
                    Peers
                </p>
            </li>
        </a>
        <a href="settings">
            <li>
                <img src="svg/nav_settings.svg" alt="">
                <p>
                    Settings
                </p>
            </li>
        </a>
    </ul>
</div>

<div class="footer">
    <div class="container">
        <h3>Blockchain</h3>
        {#if syncing}
            <div class="loader">
                <Loader small=true />
            </div>
            <ProgressBar Progress={progress}></ProgressBar>
        {:else}
            <button class="sync" on:click={fakeSync}>
                <p> Sync Progress </p>
            </button>
        {/if}
    </div>
</div>
