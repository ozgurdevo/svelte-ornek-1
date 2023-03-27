<script>
  import Counter from "./lib/Counter.svelte";
  import Calisanlar from "./lib/calisanlar.svelte";
</script>


<Counter/>
<br><br>

<Calisanlar/>





<!--<script lang="ts">
    import List from "./lib/list.svelte";
    import PropsExample from "./lib/props-example.svelte";

    let ad = "";
  let soyad = "";
  let items =[];

  export let deleteTest = () =>{
        ad="";
        soyad="";
    }

  export let gonder = () =>{
 items = [...items,ad]
  }
</script>
<List/>

<PropsExample bind:ad={ad} bind:soyAd={soyad}  />
{ad} { soyad}
<button on:click={deleteTest}> Sıfırla </button>
<button on:click={gonder}>gönder</button>

<hr>

<List bind:items={items}></List>

<script>
  export let ad;
  export let soyAd;

</script>

<input type="text" bind:value={ad} placeholder="Adınızı giriniz">

<input type="text" bind:value={soyAd}  placeholder="Soyadınızı giriniz"> --> 


<h1>Yusuf Efe</h1>