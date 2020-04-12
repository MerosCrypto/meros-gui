<script>
	import Card from "./Card.svelte";

    export let max = 3;
    let count = 0;
    function getTransactions() {
        return [
            { type: "send", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:15" },
            { type: "receive", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:16" },
            { type: "send", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:15" },
            { type: "receive", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:16" },
            { type: "send", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:15" },
            { type: "receive", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:16" },
            { type: "send", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:15" },
            { type: "receive", amount: 32.322, id: "mrpntizet91n359", date: "July 1, 2020", time:"17:16" },
        ];
    }
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
    }

    img {
        max-width: 25px;
    }

    h2 {
        width: auto;
    }

    p {
        margin: 0px
    }

    b h2{
        font-weight: bold !important
    }
</style>

<div class="container">
    {#each getTransactions() as transaction, i}
        {#if (i < max) || (max == -1)}
            <Card padding="10px">
                <div style="max-height: 70px;" class="row">
                    {#if transaction.type == "send"}
                        <img style="margin-left: 20px;" src="./svg/send.svg" alt="">
                    {:else if transaction.type == "receive"}
                        <img style="margin-left: 20px;" src="./svg/receive.svg" alt="">
                    {/if}

                    <div style="margin-left: 26px;" class="col">
                        {#if transaction.type == "send"}
                            <h2 style="margin-bottom: 5px;" >Sent</h2>
                        {:else}
                            <h2 style="margin-bottom: 5px;" >Received</h2>
                        {/if}
                        <b>
                            <h2>{transaction.amount}</h2>
                        </b>
                    </div>

                    <div style="margin-left: auto; padding: 10px;" class="col">
                        <div style="margin-bottom: 6px">
                            <p style="color:#008512">{transaction.id}</p>
                        </div>
                        <div>
                            <p style="color:#ADADAD">{transaction.date + " " + transaction.time}</p>
                        </div>
                    </div>
                </div>
            </Card>
        {/if}
    {/each}
</div>
