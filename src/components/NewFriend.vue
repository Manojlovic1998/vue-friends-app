<template>
  <form @submit.prevent>
    <div>
      <label for="name">Friend's Name</label>
      <input type="text" id="name" />
    </div>
    <div>
      <label for="email">Friend's Email</label>
      <input type="email" id="email" />
    </div>
    <div>
      <label for="phone">Friend's Phone Number</label>
      <input type="number" />
    </div>
    <div>
      <label for="favorite">Favorite Status</label>
      <input type="radio" name="" id="favorite" />
    </div>
  </form>
</template>

<script>
export default {};
</script>