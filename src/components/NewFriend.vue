<template>
  <form @submit.prevent="onNewFriendSubmit">
    <div>
      <label for="name">Friend's Name</label>
      <input type="text" id="name" ref="name" required />
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" id="email" ref="email" required />
    </div>
    <div>
      <label for="phone">Phone Number</label>
      <input type="number" ref="phone" required />
    </div>
    <div>
      <label for="favorite">Favorite Status</label>
      <input type="checkbox" name="favorite" id="favorite" ref="favorite" />
    </div>
    <div>
      <button type="submit">Add New Friend</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: {
    "new-friend": (formUserData) => {
      if (!formUserData.name) {
        return false;
      }

      if (!formUserData.phone) {
        return false;
      }

      if (!formUserData.email) {
        return false;
      }

      if (!formUserData.id) {
        return false;
      }
      return true;
    },
  },
  methods: {
    onNewFriendSubmit() {
      const newUserData = {
        id: this.$refs.name.value.toLowerCase(),
        name: this.$refs.name.value,
        phone: this.$refs.phone.value,
        email: this.$refs.email.value,
        isFavFriend: this.$refs.favorite.checked,
      };

      this.$emit("new-friend", newUserData);

      this.$refs.name.value = "";
      this.$refs.email.value = "";
      this.$refs.phone.value = "";
      this.$refs.favorite.checked = false;
    },
  },
};
</script>
