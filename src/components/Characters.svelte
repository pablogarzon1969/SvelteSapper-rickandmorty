<script>
  import DataTable, { Head, Body, Row, Cell } from "@smui/data-table";
  import Card, {
    Content,
    PrimaryAction,
    Media,
    MediaContent,
    Actions,
    ActionButtons,
    ActionIcons
  } from "@smui/card";
  export let characters = [];
  export let mostrar = false;
</script>

{#if mostrar === true}
  <div>
    <DataTable>
      <Head>
        <Row>
          <Cell>Nombre</Cell>
          <Cell>Localizacion</Cell>
          <Cell>Foto</Cell>
        </Row>
      </Head>
      <Body>
        {#each characters as character}
          <Row>
            <Cell>{character.name}</Cell>
            <Cell>{character.location.name}</Cell>
            <Cell>
              <figure>
                <img src={character.image} alt={character.name} />
                <figcaption>{character.name}</figcaption>
              </figure>
            </Cell>
          
          </Row>
        {/each}
      </Body>
    </DataTable>
  </div>
{/if}
<br/>
{#each characters as character}
  <div class="card-container">
    <Card style="width: 350px;">
      <div style="padding: 1rem;">
        <h2 class="mdc-typography--headline6" style="margin: 0;">
          {character.name}
        </h2>
        <h3 class="mdc-typography--subtitle2" style="margin: 0; color: #888;">
          {character.species} - {character.gender}
        </h3>
      </div>
      <PrimaryAction>
        <Media class="card-media-10x6" aspectRatio="10x6">
          <figure>
            <img src={character.image} alt={character.name} />
          </figure>
        </Media>
        <Content class="mdc-typography--body2">
          Localizacion: {character.location.name}
        </Content>
      </PrimaryAction>
    </Card>
  </div>
{/each}
