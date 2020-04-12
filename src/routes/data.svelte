<script>
    import Card from "./../components/Card.svelte";

    let data;
    function publishData() {}
</script>

<div class="row">
    <div class="half">
        <Card padding="0px">
            <div class="bcard col" style="padding:20px;">
                <div class=" row ">
                    <img style="height:30px; width: 30px; margin-right: 20px" src="/svg/data_white.svg" alt="">
                    <b>
                        <h3 style="margin-top:3px">Data</h3>
                    </b>
                </div>
                <input type="text" bind:value={data} name="" id="" cols="30" rows="10">
            </div>

            <button style="margin-left:auto; margin-right:20px; margin-bottom:30px;" on:click={publishData}>
                <img src="svg/send_white.svg" alt="">
                <p>Publish</p>
            </button>
        </Card>
    </div>
</div>
