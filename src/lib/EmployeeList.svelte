<script lang="ts">
  //@ts-nocheck
  import Columns from "./Columns.svelte";
  import { onMount } from "svelte";
  import Employee from "./Employee.svelte";
  let employeeList = [];
  let nameInput, emailInput;

  onMount(async () => {
    const res = fetch(`http://localhost:3004/employees`).then(
      async (response) => {
        employeeList = await response.json();
      }
    );
  });

  let updateEmployeeInputsHandler = (nameValue, emailValue) => {
    nameInput = nameValue;
    emailInput = emailValue;
  };

  let deleteEmployeeHandler = (i) => {
    employeeList = employeeList.filter((el, index) => index !== i);
  };
</script>

<div
  class="my-28 max-w-5xl mx-auto md:w-200 h-auto overflow-x-scroll bg-slate-400"
>
  <h1 class="text-xl text-center">Calisanlar</h1>
  <form
    class="grid grid-cols-12 p-2 min-h-14 gap-1 w-250 md:w-200 h-auto overflow-x-scroll"
    onSubmit={null}
  >
    <div class="col-span-3">
      <input
        type="text"
        placeholder="ad"
        bind:value={nameInput}
        class="border border-gray-300 bg-white focus:border-gray-400 focus:outline-none text-gray-500 rounded-md indent-2 w-full h-full"
      />
    </div>
    <div class="col-span-4">
      <input
        type="text"
        placeholder="e-mail"
        bind:value={emailInput}
        class="border border-gray-300 bg-white focus:border-gray-400 focus:outline-none text-gray-500 rounded-md indent-2 w-full h-full"
      />
    </div>
    <div class="col-span-1" />
    <div class="col-span-2" />
    <div class="col-span-2 flex justify-center items-center gap-2">
      <button class="border border-black rounded-md p-1 bg-white">iptal</button>
      <button class="border border-black rounded-md p-1 bg-white">ekle</button>
    </div>
  </form>
  <Columns />
  {#each employeeList as employee, i}
    <Employee
      {...employee}
      updateEmployeeInputsHandler={() =>
        updateEmployeeInputsHandler(employee.fullname, employee.email)}
      deleteEmployeeHandler={() => deleteEmployeeHandler(i)}
    />
  {/each}
</div>
