<template>
    <section @mouseover="onHovered" @mouseout="onHovered(false)" class="card-user" v-for="user in users">
        <img class="avatar" :src="avatar" :alt="name" />
        <p>{{ name }}</p>
        <p>{{ email }}</p>
        <p v-if="bio">
          <template v-if="isHovered">{{ bio }}</template>
        </p>
        <p v-else>No bio available</p>
    </section>
</template>

<script>
export default {
    props: {
        avatar: String,
        name: String,
        email: String,
        bio: String,
    },
    data() {
        return {
          isHovered: false
        }
    },
    methods: {
      onHovered(over = true) {
        this.isHovered = over
      },
    }
}

</script>