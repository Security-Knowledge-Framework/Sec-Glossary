<script>
  import { fade, slide } from "svelte/transition";
  export let item;

  let url = "";
  let name = "";

  const { source } = item;

  if (Object.hasOwn(source, "url")) {
    url = source.url;
  }

  if (Object.hasOwn(source, "name")) {
    name = source.name;
  }

  const logo = "http://www.google.com/s2/favicons?domain=" + new URL(url);
</script>

<div class="card" in:slide out:fade>
  <h2>{item.term}</h2>
  <p>{item.description}</p>
  <div class="citation">
    {#if logo}
      <img src={logo} alt={`${name} logo`} />
    {/if}
    {#if url && name}
      <a href={url}>{name}</a>
    {/if}
  </div>
</div>

<style>
  .card {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    width: 100%;
    padding: 24px;
    /* border-radius: 8px; */
    /* background-color: rgb(106, 73, 163); */
    /* box-shadow: 1px 1px 4px 0px rgb(0 0 0 / 20%); */

    background-color: rgba(106, 73, 163, 0.75);
    border-radius: 16px;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(5px);
    -webkit-backdrop-filter: blur(5px);
    border: 1px solid rgba(106, 73, 163, 0.3);
  }

  h2 {
    margin-bottom: 10px;
  }

  .citation {
    margin-top: 10px;
    display: flex;
    align-items: center;
    align-self: flex-end;
  }

  img {
    max-width: 40px;
    margin-right: 10px;
  }
</style>
