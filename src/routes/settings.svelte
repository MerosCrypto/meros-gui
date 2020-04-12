<script>
    import Card from "./../components/Card.svelte";

    let dataDir = "/home/user/.meros";
    let walletSeed = "77A007E8772DFBABB34C9264E27613B17AE42B9CA95393C38F9452FE71940E11";
    let minerKey = "FC6A437459ED061E306F3CBEEBA925DCEE81EB5D5ECFA9BC51D5C3C8310B42CAF5793D344B7B7B739995FD53644C9562";

    let server = false;
    let tcpPort = "5132";

    let rpc = false;
    let rpcPort = "5133";
</script>

<style>
    hr {
        border-color: rgba(0, 0, 0, 0.123);
        width: 100%;
    }

    input[type="checkbox" i] {
        margin-top: 10px;
        height: 20px;
        width: 20px;
        background-color: rgba(255, 255, 255, 0);
        border: solid 2px #fff;
        color: #fff;
    }
</style>

<Card padding="0px">
    <div class="bcard col" style="padding:20px;">
        <div class=" row ">
            <img style="height:30px; width: 30px; margin-right: 20px" src="/svg/settings_white.svg" alt="">
            <b>
                <h3 style="margin-top:3px" >Settings</h3>
            </b>
        </div>

        <p style="margin-top:20px">Data Directory</p>
        <input type="text" bind:value={dataDir} name="" id="" cols="30" rows="10">

        <p style="margin-top:20px">Wallet</p>
        <input type="text" bind:value={walletSeed} name="" id="" cols="30" rows="10">

        <p style="margin-top:20px">Miner</p>
        <input type="text" bind:value={minerKey} name="" id="" cols="30" rows="10">

        <p style="margin-top:20px">Server</p>
        <div class="row">
            <input type="checkbox" bind:value={server} style="margin-right:20px">
            <input type="text" bind:value={tcpPort} name="" id="" cols="30" rows="10">
        </div>

        <p style="margin-top:20px">RPC</p>
        <div class="row">
            <input type="checkbox" bind:value={rpc} style="margin-right:20px">
            <input type="text" bind:value={rpcPort} name="" id="" cols="30" rows="10">
        </div>
    </div>
</Card>
