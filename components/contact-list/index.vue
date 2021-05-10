<template>
  <div class="min-h-screen bg-grey bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="card">
        <div class="text-2xl font-bold mb-6">Your contacts</div>
        <sortable-list v-model="contacts">
          <div class="contact-list">
            <sortable-list-item
              v-for="contact in contacts"
              :key="contact.id"
              class="contact-list-item"
            >
              <div class="contact-list-contact">
                <img class="contact-list-avatar" :src="contact.avatar" alt="" />
                <div>
                  <div class="contact-list-name">
                    {{ contact.name }}
                  </div>
                  <div class="contact-list-email">
                    {{ contact.email }}
                  </div>
                </div>
                <sortable-list-handle>
                  <button class="ml-auto btn">Drag</button>
                </sortable-list-handle>
              </div>
            </sortable-list-item>
          </div>
        </sortable-list>
      </div>
      <div class="card">
        <pre>
          {{ contacts }}
        </pre>
      </div>
    </div>
  </div>
</template>

<script>
import SortableList from "@/components/sortable/SortableList";
import SortableListItem from "@/components/sortable/SortableListItem";
import SortableListHandle from "@/components/sortable/SortableListHandle";
export default {
  components: {
    SortableList,
    SortableListItem,
    SortableListHandle
  },
  data() {
    return {
      contacts: [
        {
          id: 1,
          name: "Victor Biletsky",
          email: "vb@gmail.com",
          avatar: "https://randomuser.me/api/portraits/men/1.jpg"
        },
        {
          id: 2,
          name: "Illya Semenov",
          email: "ilyasemenov@gmail.com",
          avatar: "https://randomuser.me/api/portraits/men/2.jpg"
        },
        {
          id: 3,
          name: "Chris",
          email: "chris@gmail.com",
          avatar: "https://randomuser.me/api/portraits/men/3.jpg"
        }
      ]
    };
  }
};
</script>
