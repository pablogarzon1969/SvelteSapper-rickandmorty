<script>
  import { onMount } from "svelte";
  import Characters from "./Characters.svelte";
  import Button from "@smui/button";
  import Fab from "@smui/fab";
  import { Label, Icon } from "@smui/common";
  import Textfield from "@smui/textfield";


  let query = "";
  let data = [];
  let characters = [];
  let mostrar = false;
  async function OnChangeInput() {
    const APIFILTER = `https://rickandmortyapi.com/api/character/?name=${query}`;
    const res = await fetch(APIFILTER);
    data = await res.json();
    characters = data.results;
    console.log(Characters.length);
    if (Characters.length > 0) {
      mostrar = true;
    }
  }
</script>

<div>
  <form on:submit|preventDefault={OnChangeInput}>
    <Label for="exampleEmail">Nombre:</Label>
    <Textfield variant="outlined" bind:value={query} id="search" />
    <Button type="submit" variant="raised" color="primary">Buscar</Button>
  </form>
  <br/>
  <Characters {characters} { mostrar } />
</div>
