<template>
  <li>
    <h2>{{ name }} {{ isFavFriend ? "(Favorite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }}
    </button>
    <button @click="toggleFriendIsFavorite(friendId)">
      {{ isFavFriend ? "Unfavorite" : "Favorite" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phone }}</li>
      <li><strong>Email:</strong> {{ email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
    isFavFriend: {
      type: Boolean,
      required: false,
      default: false,
    },
    friendId: {
      type: String,
      required: true,
    },
  },
  emits: {
    "toggle-favorite": (id) => {
      if (id) {
        return true;
      }

      console.warn("Id is missing");
      return false;
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFriendIsFavorite(id) {
      this.$emit("toggle-favorite", id);
    },
  },
};
</script>
