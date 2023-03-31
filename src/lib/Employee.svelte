<script lang="ts">
  export let fullname,
    email,
    maritalStatus,
    department,
    updateEmployeeInputsHandler,
    deleteEmployeeHandler;
</script>

<div
  class={`grid grid-cols-12 px-2 min-h-14 py-4 text-center border border-l-0 border-b-0 border-r-0 select-none`}
>
  <div class="col-span-3 inline-flex justify-center items-center">
    {fullname}
  </div>
  <div class="col-span-4 inline-flex justify-center items-center">
    {email}
  </div>
  <div class="col-span-1 inline-flex justify-center items-center">
    {maritalStatus === true ? "evli" : "bekar"}
  </div>
  <div class="col-span-2 inline-flex justify-center items-center">
    {department}
  </div>
  <div class="col-span-1 inline-flex justify-center items-center">
    <button
      class="bg-slate-200 hover:bg-slate-300 focus:bg-slate-400 focus:text-white p-1 rounded-md"
      on:click={updateEmployeeInputsHandler}>güncelle</button
    >
  </div>
  <div class="col-span-1 inline-flex justify-center items-center">
    <button
      class="bg-slate-200 hover:bg-slate-300 focus:bg-slate-400 focus:text-white p-1 rounded-md"
      on:click={deleteEmployeeHandler}>sil</button
    >
  </div>
</div>
