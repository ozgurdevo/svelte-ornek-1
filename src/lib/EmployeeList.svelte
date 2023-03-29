<script lang="ts">
  //@ts-nocheck
  import Columns from "./Columns.svelte";
  import { onMount } from "svelte";
  import Employee from "./Employee.svelte";
  let employeeList = [];

  onMount(async () => {
    const res = fetch(`http://localhost:3004/employees`).then(
      async (response) => {
        employeeList = await response.json();
      }
    );
  });
</script>

<div
  class="my-28 max-w-5xl mx-auto md:w-200 h-auto overflow-x-scroll bg-slate-400"
>
  <Columns />
  {#each employeeList as employee, i}
    <Employee {...employee} />
  {/each}
</div>
