<script lang="ts">
  //@ts-nocheck
  import Columns from "./Columns.svelte";
  import { onMount } from "svelte";
  import Employee from "./Employee.svelte";
  let employeeList = [];
  let nameInput,
    emailInput,
    selected = null;

  onMount(async () => {
    const res = fetch(`http://localhost:3004/employees`).then(
      async (response) => {
        employeeList = await response.json();
      }
    );
  });

  // ilgili çalışanın 'güncelle' butonu
  let updateEmployeeInputsHandler = (nameValue, emailValue, i) => {
    // YAPILACAKLAR
    // 1) ad ve email input'larina ilgili çalışanın ad ve email bilgisi atanacak
    // 2) selected değişkenine seçilen çalışanın dizi id'si atanacak
  };

  // ilgili çalışanın 'sil' butonu
  let deleteEmployeeHandler = (i) => {
    // YAPILACAKLAR
    // 1) employeeList dizisinden ilgili çalışan çıkarılacak [i parametresi kullanılarak]
  };

  // iptal butonu
  let cancelHandler = () => {
    // YAPILACAKLAR
    // 1) ad ve email input'ları sıfırlanacak
    // 2) selected'a null atanacak
  };

  // ekle / onayla butonu
  let addHandler = () => {
    // YAPILACAKLAR
    // 1) spread operatörü ile employeeList dizisi kopyalanıp, yeni dizide 'selected' indisindeki çalışanın
    // fullname ve email bilgileri güncellenecek ve employeeListe güncel dizi atanacak
    // 2) ad ve email input'ları sıfırlanacak
    // 3) selected'a null atanacak
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
      <button
        class="border border-black rounded-md p-1 bg-white"
        type="button"
        on:click={cancelHandler}>iptal</button
      >
      <button
        class="border border-black rounded-md p-1 bg-white"
        type="button"
        on:click={addHandler}>{selected === null ? "ekle" : "onayla"}</button
      >
    </div>
  </form>
  <Columns />
  {#each employeeList as employee, i}
    <!-- <Employee
      YAPILACAKLAR
      1) Bu yorum satırlı komponent kullanımı açılıp employee componentine ilgili employee'nin
      fullname, email gibi bilgilerini props özelliği ile gönderilecek
      updateEmployeeInputsHandler={() =>
        updateEmployeeInputsHandler(employee.fullname, employee.email, i)}
      deleteEmployeeHandler={() => deleteEmployeeHandler(i)}
    /> -->
  {/each}
</div>
