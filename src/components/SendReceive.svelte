<script>
	import CopyInput from "./CopyInput.svelte";
	import { createEventDispatcher, onDestroy } from "svelte";

	const dispatch = createEventDispatcher();
	const close = () => dispatch("close");

    let modal;
	export let mode = "";
	export let maddress;

	let destination;
	let amount;

	function send() {
		close();
	}

	const handle_keydown = (e) => {
		if (e.key === "Escape") {
			close();
			return;
		}

		if (e.key === "Tab") {
			const nodes = modal.querySelectorAll("*");
			const tabbable = Array.from(nodes).filter(n => n.tabIndex >= 0);

			let index = tabbable.indexOf(document.activeElement);
			if (index === -1 && e.shiftKey) index = 0;

			index += tabbable.length + (e.shiftKey ? -1 : 1);
			index %= tabbable.length;

			tabbable[index].focus();
			e.preventDefault();
		}
	};

	const previously_focused = (typeof(document) !== "undefined") && document.activeElement;
	if (previously_focused) {
		onDestroy(() => {
			previously_focused.focus();
		});
	}
</script>

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.616);
		z-index: 1000;
	}

	.modal {
		z-index: 1001;
		position: absolute;
		left: 50%;
		top: 50%;
		width: calc(100vw - 4em);
		max-width: 36em;
		max-height: calc(100vh - 4em);
		overflow: hidden;
		transform: translate(-50%,-50%);
		background: white;
		box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.699);
        transition: 0.3s;
		margin-top: auto;
		margin-bottom: auto;
	}

    .modal::after {

	}

	button img {
		max-width: 30px !important;
		min-width: 30px !important;
		margin: 0px !important;
		margin-right: 10px !important;
	}

	button p {
		margin: 0px !important;
		margin-top: 6px !important;
		margin-right: 30px !important;
	}

	h3 {
        font-weight: bold;
    }

	div p {
		width: auto;
		margin: 0px;
		padding: 0px;
		margin-left: 3px;
	}
</style>

<svelte:window on:keydown={handle_keydown}/>

<div class="modal-background" on:click={close}></div>

<div class="modal" role="dialog" aria-modal="true" bind:this={modal}>
	<div class=" col bcard" style="padding: 30px;">
		<div class="row">
			{#if mode == "send"}
				<img style="height:30px; width: 30px; margin-right: 20px" src="/svg/send_white.svg" alt="">
				<h3 style="margin-top:3px">Send</h3>
			{:else if  mode == "receive"}
				<img style="height:30px; width: 30px; margin-right: 20px" src="/svg/receive_white.svg" alt="">
				<h3 style="margin-top:3px">Receive</h3>
			{/if}
		</div>

		{#if mode == "send"}
			<div class="col">
				<p style="margin-top:20px">Destination</p>
				<input type="text" bind:value={destination} name="" id="" cols="30" rows="10">
				<p style="margin-top:20px">Amount</p>
				<input type="number" bind:value={amount} name="" id="" cols="30" rows="10">

				<button style="margin-top:50px; margin-left:auto; margin-right:30px;" on:click={send}>
					<img src="svg/send_white.svg" alt="">
					<p>Send</p>
				</button>
			</div>
		{:else if mode == "receive"}
			<div class="col">
				<img src="svg/address.svg" alt="">
				<div style="text-align: center; margin-top: 30px">
					<h2>This is <b>your</b> address!</h2>
					<CopyInput value="{maddress}"/>
				</div>
			</div>
		{/if}
	</div>

	<!-- svelte-ignore a11y-autofocus -->
	<button style="margin-left:auto; margin-right:auto; margin-bottom:30px;" autofocus on:click={close}>
		<img src="svg/exit.svg" alt="">
		<p>Close</p>
	</button>
</div>
