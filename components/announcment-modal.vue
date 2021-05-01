<template>
  <div class="modal-backdrop">
    <div ref="modal" class="modal" tabindex="0">
      <h1 class="text-center text-2xl font-bold mb-4">Here is a title</h1>
      <p class="text-center mb-6">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut cupiditate
        dolore eligendi exercitationem, labore libero obcaecati provident sed
        veniam vero. Labore praesentium, soluta. Ab autem corporis cum mollitia
        quam, similique?
      </p>
      <div class="text-center">
        <button class="btn btn-blue" type="button">
          Dismiss
        </button>
      </div>
    </div>
  </div>
</template>


<style>
.modal {
  border: 1px solid blue;
}
.modal:focus {
  outline: 2px solid red;
}
</style>
