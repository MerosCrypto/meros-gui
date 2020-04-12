<script>
    import Card from "./../components/Card.svelte";

    function getPeers() {
        return [
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 },
        { ip: "107.19.18.123", port: "5132", karma: 10 }
        ];
    }

    let ip, port;
    function connect() {

    }

</script>

<style>
    .col p {
        margin: 0px;
    }

    hr {
        border-color: rgba(0, 0, 0, 0.123);
        width: 100%;
    }
</style>

<div class="row">
    <div class="half">
        <Card padding="0px">
            <div class="bcard col" style="padding:20px;">
                <div class="row">
                    <img style="height:30px; width: 30px; margin-right: 20px" src="/svg/settings_white.svg" alt="">
                    <b>
                        <h3 style="margin-top:3px">Add Peer</h3>
                    </b>
                </div>

                <p style="margin-top:20px">IP</p>
                <input type="text" bind:value={ip} name="" id="" cols="30" rows="10">

                <p style="margin-top:20px">Port</p>
                <input type="text" bind:value={port} name="" id="" cols="30" rows="10">
            </div>

            <button style="margin-left:auto; margin-right:20px; margin-bottom:30px;" on:click={connect}>
                <img src="/svg/peers_white.svg" alt="">
                <p>Add</p>
            </button>
        </Card>
    </div>

    <div class="half">
        <Card padding="0px">
            <div class="bcard col" style="padding:20px; max-height:60px !important">
                <div class="row">
                    <img style="height:30px; width: 30px; margin-right: 20px" src="/svg/peers_white.svg" alt="">
                    <b>
                        <h3 style="margin-top:3px">Connected Peers</h3>
                    </b>
                </div>
            </div>

            <div class="col" style="margin-top: 0px; padding:10px overflow-y:scroll; overflow-x:hidden; max-height:550px;">
                {#each getPeers() as peer}
                    <hr>
                    <Card padding="10px" style="border: solid 1px #000">
                        <div class="row">
                            <img style="height:30px; width: 30px;" src="/svg/nav_data.svg" alt="">
                            <div class="col">
                                <b>
                                    <p>IP: {peer.ip + "  "}</p>
                                </b>
                                <p>Port: {peer.port + "  Karma: " + peer.karma}</p>
                            </div>
                        </div>
                    </Card>
                {/each}
            </div>
        </Card>
    </div>
</div>
