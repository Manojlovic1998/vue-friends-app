<template>
  <li>
    <h2>{{ name }} {{ thisFriendIsFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }}
    </button>
    <button @click="toggleFriendIsFavorite()">
      {{ thisFriendIsFavorite ? "Unfavorite" : "Favorite" }}
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
  },
  data() {
    return {
      detailsAreVisible: false,
      thisFriendIsFavorite: this.isFavFriend,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFriendIsFavorite() {
      this.thisFriendIsFavorite = !this.thisFriendIsFavorite;
    },
  },
};
</script>
