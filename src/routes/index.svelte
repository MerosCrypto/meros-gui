<script>
    import CopyInput from "./../components/CopyInput.svelte";
    import SendReceive from "./../components/SendReceive.svelte";
    import Card from "./../components/Card.svelte";
    import Transactions from "./../components/Transactions.svelte";

    let showModal = false;
    let mode;

    function getAmount() {
        return "1234.12345678";
    }
    function getAddress() {
        return "Mrp8ls5tmnpct8lehz3v4yadqw9zvnc7m8s20c6mehp8a25n3w9tvtxkaswl";
    }
</script>

<style>
    img {
        width: 100%;
        max-width: 400px;
        margin: 0 0 1em 0;
    }

    p {
        margin: 1em auto;
    }

    button img {
        max-width: 30px;
        min-width: 30px;
        margin: 0px;
        margin-right: 10px;
    }
    button p {
        margin: 0px;
        margin-top: 6px;
        margin-right: 30px;
    }
</style>

<div class="row">
    <div class="half">
        <Card padding="0px">
            <div>
                <div class="col bcard" style="padding:20px">
                    <div class="row">
                        <img style="height:30px; width: 30px; margin-right: 20px" src="/svg/balance.svg" alt="">
                        <b>
                            <h3 style="margin-top:3px">Balance</h3>
                        </b>
                    </div>
                    <div class="col">
                        <h3>Available</h3>
                        <div class="row">
                            <b> <h3> {getAmount()} </h3> </b>
                            <p style="margin: 0px; margin-left: 10px">Meros</p>
                        </div>
                        <h3>Address</h3>
                        <CopyInput value="{getAddress()}"/>
                    </div>
                </div>
            </div>

            <div style="margin-left:auto; margin-right:0; padding: 25px;" class="row">
                <button on:click="{() => {showModal = true; mode = "send"}}">
                    <img style="height:30px" src="/svg/send_white.svg" alt="">
                    <p>Send</p>
                </button>

                <button on:click="{() => {showModal = true; mode = "receive"}}">
                    <img style="height:30px" src="/svg/receive_white.svg" alt="">
                    <p>Receive</p>
                </button>
            </div>
        </Card>
    </div>

    <div class="half">
        <Transactions max="3"/>
        <a href="transactions">
            <button>
                <p style="margin:0px 10px;">
                    Show more
                </p>
            </button>
        </a>
    </div>
</div>

{#if showModal}
    <SendReceive mode="{mode}" maddress="{getAddress()}" on:close="{() => {showModal = false;}}"/>
{/if}
