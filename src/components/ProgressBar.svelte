<script>
    export let Progress = 1;
</script>

<style>
    .progressbar {
        margin-top: 18px;
        max-height: 5px;
        width: 60%;
        border: solid 2px #fff;
        color: #fff;
        padding: 2px;
        background-color: #00000000;
        border-radius: 6px;
    }

    .bar {
        display: block;
        background-color: #fff;

        border-radius: 5px;
        height: 5px;
        z-index: 20;
    }
</style>

<div class="progressbar" value={$Progress}>
    <div class="bar" style="width: calc(100% * {$Progress})"></div>
</div>
