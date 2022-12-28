<script>
  export default {
    data() {
        return {
          users: [],
          isHovered: false
        }
    },
    async mounted() {
     const users = await fetch('http://52.77.211.222:3000/users').then(data => {
            return data.json()
        })

      this.users = users;
    },
    methods: {
      onHovered(over = true) {
        this.isHovered = over
      },
    }
  }
</script>

<template>
  <main class="wrapper">

    <section @mouseover="onHovered" @mouseout="onHovered(false)" class="card-user" v-for="user in users">
        <img class="avatar" :src="`https://robohash.org/${user.id}?size=300x300`" :alt="user.name" />
        <p>{{ user.name }}</p>
        <p>{{ user.email }}</p>

        <p v-if="user.bio">
          <template v-if="isHovered">{{ user.bio }}</template>
        </p>
        <p v-else>No bio available</p>
    </section>
  </main>
</template>

<style scoped>
.wrapper {
  display: flex;
  background-color: antiquewhite;
}

.card-user {
  background-color: aquamarine;
  width: 200px;
  padding: 10px;
}

.card-user:not(:last-child) {
  margin-right: 10px;
}

.avatar {
    width: auto;
    height: 100px;
}
</style>
