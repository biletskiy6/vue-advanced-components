<template>
  <button @click="confirmDeleteModal = true" type="button" class="text-red-dark hover:underline">
    Delete Account
    <confirm-delete-modal :show="confirmDeleteModal" @close="confirmDeleteModal = false" :account-id="accountId"></confirm-delete-modal>
  </button>

</template>

<script>
import ConfirmDeleteModal from "./ConfirmDeleteModal";
export default {
  name: "DeleteAccountButton",
  components: {
    ConfirmDeleteModal
  },
  data() {
    return {
      confirmDeleteModal: false,
      accountId: 10
    }
  },
}
</script>
