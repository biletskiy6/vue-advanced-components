<template>
  <form style=" opacity: 0.5 " class="card" @submit.prevent="submit">
    <h1 class="text-2xl font-bold mb-6">Your Settings</h1>
    <label class="block mb-6">
      <span class="form-label mb-2">Email Address</span>
      <input v-model="email" class="form-input" placeholder="you@example.com" />
    </label>
    <div class="mb-8">
      <span class="form-label mb-2">Newsletter</span>
      <div class="flex justify-between items-center">
        <p class="mr-4">Send you occasional news and updates.</p>
        <toggle-input v-model="receiveNewsletter"></toggle-input>
      </div>
    </div>
    <div class="flex justify-between">
      <delete-account-button></delete-account-button>
      <button type="submit" class="btn btn-blue">Update Settings</button>
    </div>
  </form>
</template>

<script>
import ToggleInput from "@/components/ToggleInput";
import ConfirmDeleteModal from "../ConfirmDeleteModal";
import DeleteAccountButton from "../DeleteAccountButton";
export default {
  components: {
    DeleteAccountButton,
    ConfirmDeleteModal,
    ToggleInput
  },
  data() {
    return {
      email: "jane@example.com",
      receiveNewsletter: false,
      confirmDeleteModal: false,
      accountId: 9
    };
  },
  methods: {
    submit() {
      console.log("Submitting preferences...", {
        email: this.email,
        receiveNewsletter: this.receiveNewsletter
      });
    },
    toggle() {
      this.receiveNewsletter = !this.receiveNewsletter;
    }
  }
};
</script>
