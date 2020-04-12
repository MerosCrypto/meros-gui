<script>
    export let small = false;
</script>

<style>
    .loader, .loader:before, .loader:after {
        border-radius: 50%;
    }

    .loader {
        color: #ffffff;
        font-size: 11px;
        text-indent: -99999em;
        position: relative;
        width: 10em;
        max-width: 10em;
        min-width: 10em;
        height: 10em;
        box-shadow: inset 0 0 0 1em;
        -webkit-transform: translateZ(0);
        -ms-transform: translateZ(0);
        transform: translateZ(0);
    }

    .small {
        transform: scale(0.3);
        top: -46px;
    }

    .loader:before, .loader:after {
        position: absolute;
        content: "";
    }

    .loader:before {
        width: 5.2em;
        height: 10.2em;
        background: #003795;
        border-radius: 10.2em 0 0 10.2em;
        top: -0.1em;
        left: -0.1em;
        -webkit-transform-origin: 5.1em 5.1em;
        transform-origin: 5.1em 5.1em;
        -webkit-animation: load2 2s infinite 1.0s ease;
        animation: load2 2s infinite 1.0s ease;
    }

    .loader:after {
        width: 5.2em;
        height: 10.2em;
        background: #003795;
        border-radius: 0 10.2em 10.2em 0;
        top: -0.1em;
        left: 4.9em;
        -webkit-transform-origin: 0.1em 5.1em;
        transform-origin: 0.1em 5.1em;
        -webkit-animation: load2 2s infinite 0.5s ease;
        animation: load2 2s infinite 0.5s ease;
    }

    @-webkit-keyframes load2 {
        0% {
            -webkit-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }

    @keyframes load2 {
        0% {
            -webkit-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
</style>

{#if !small}
    <div class="loader">Loading...</div>
{:else}
    <div class="loader small">Loading...</div>
{/if}
