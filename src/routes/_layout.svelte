<script>
    import Nav from "../components/Nav.svelte";
    import Loader from "../components/Loader.svelte";

    export let segment;

    //This ensures the loading screen doesn't reappear when switching pages...
    let loaded = false;

</script>


<style>
    main {
        position: relative;
        max-width: 80em;
        padding: 2em;
        margin: 0 auto;
        margin-top: 30px;
        box-sizing: border-box;
    }

    .loading-cover {
        position: fixed;
        width: 100%;
        height: 100%;
        z-index: 100;
        background-color: #003795;
        color: #fff;
    }

    .content {
        position: relative;
        max-width: 30em;
        padding: 2em;
        text-align: center;

        position: absolute;
        left: 50%;
        top: 50%;
        width: calc(100vw - 4em);
        max-height: calc(100vh - 4em);
        overflow: hidden;
        transform: translate(-50%,-50%);
    }

    h1 {
        font-weight: bold !important;
        font-size: 50px;
    }

    .logo {
        padding: 0px;
        height: 140px;
    }

    .loading-cover {
        font-size: 21px;
        text-align: center;
    }

    :global(fadeout) {
        -webkit-animation: fadein 0.6s 3s;
           -moz-animation: fadein 0.6s 3s;
            -ms-animation: fadein 0.6s 3s;
             -o-animation: fadein 0.6s 3s;
                animation: fadein 0.6s 3s;
    }

    @keyframes fadein {
        from { opacity: 1; }
        to   { opacity: 0; }
    }

    @-webkit-keyframes fadein {
        from { opacity: 1; }
        to   { opacity: 0; }
    }

    @-ms-keyframes fadein {
        from { opacity: 1; }
        to   { opacity: 0; }
    }

    .loader {
        max-width: 110px;
        margin: auto auto !important;
    }
</style>

{#if !loaded}
    <div id="cover" class="loading-cover">
        <div class="content">
            <img class="logo" src="svg/logo.svg" alt="">
            <h1>Meros</h1>
            <div class="loader">
                <Loader style="padding: 30px"/>
            </div>
            <p>Loading Blockchain...</p>
        </div>
        <script>
            setTimeout(() => {
                loaded = true;

                if (typeof(document.getElementById("cover").remove) == "function") {
                    document.getElementById("cover").remove()
                } else {
                    document.getElementById("cover").outerHTML = "";
                }

            }, 4000);
        </script>
    </div>
{/if}

<div>
    <Nav {segment}/>

    <main>
        <slot>
        </slot>
    </main>
</div>
