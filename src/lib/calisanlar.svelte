<script lang="ts">
  //@ts-nocheck
  import { onMount } from "svelte";
  import { listen } from "svelte/internal";
  let Deneme = [];
  let selected = null;

  onMount(async () => {
    const res = fetch(`http://localhost:3004/employees`).then(
      async (response) => {
        Deneme = await response.json();
        console.log("request data received!");
      }
    );
    console.log("request ended!");
    console.log(await selected);
  });
  let x = null;
</script>

<input bind:value={x} type="text" />

<ul>
  {#each Deneme as deneme, i}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div style="display:flex; width:200px">
      <li
        bind:this={selected}
        on:click={(event) => {
          console.log(event.target);

          if (event.target.style.textDecoration == "") {
            event.target.style.textDecoration = "line-through";
          } else {
            event.target.style.textDecoration = "";
          }
        }}
      >
        {deneme.fullname}
      </li>
      <button
        on:click={() => {
          console.log(selected);
          x = deneme.fullname;
        }}>güncelle</button
      >
    </div>
  {/each}
</ul>
