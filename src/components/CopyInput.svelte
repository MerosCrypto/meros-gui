<script>
  import { tick } from "svelte";

  export let value = null;
  let areaDom;

  async function copy() {
    await tick();
    areaDom.select();
    document.execCommand("copy");
  }
</script>

<style>
  div {
    cursor: pointer;
    font-size: 12px;

    border: solid #fff 2px;
    border-radius: 30px;
	max-height: 21px;
    width: auto;
	padding: 4px;
	background-color: #003795;
    transition: 3s;
	box-shadow: none;

    display: flex;
    flex-direction: row;
  }

  div p {
    width: auto;
    margin: 0px;
    padding: 0px;
    margin-left: 3px;
  }

  div:active {
    border: solid rgb(61, 255, 109) 2px;
    color: rgb(61, 255, 109);
	background-color: rgba(7, 114, 16, 0.349);
    transition: 0s;
  }

  svg {
      margin-left: auto;
      margin-right: 5px;
  }
  textarea {
      position: fixed;
      top: 2000px;
  }
</style>

<div on:click={copy}>
    <p bind:this={areaDom}>{value}</p>

    <textarea readonly bind:this={areaDom} id="" cols="30" rows="10">{ value }</textarea>

    <svg
        title="Copy to clipboard"
        class="octicon octicon-clippy"
        viewBox="0 0 14 16"
        version="1.1"
        width="14"
        height="16"
        aria-hidden="true"
    >
    <path fill-rule="evenodd" fill="#fff"
            d="M2 13h4v1H2v-1zm5-6H2v1h5V7zm2 3V8l-3 3 3 3v-2h5v-2H9zM4.5 9H2v1h2.5V9zM2 12h2.5v-1H2v1zm9 1h1v2c-.02.28-.11.52-.3.7-.19.18-.42.28-.7.3H1c-.55 0-1-.45-1-1V4c0-.55.45-1 1-1h3c0-1.11.89-2 2-2 1.11 0 2 .89 2 2h3c.55 0 1 .45 1 1v5h-1V6H1v9h10v-2zM2 5h8c0-.55-.45-1-1-1H8c-.55 0-1-.45-1-1s-.45-1-1-1-1 .45-1 1-.45 1-1 1H3c-.55 0-1 .45-1 1z"></path>
    </svg>
</div>
