<script setup>
import { ref } from 'vue'
import { faker } from '@faker-js/faker'
import Comment from '../components/comment.vue'

let comments = Array(100).fill('').map((item, i) => ({
  id: i + 1,
  text: faker.lorem.sentences(),
  author: faker.person.fullName(),
  avatar: faker.image.avatarGitHub(),
  created: faker.date.recent({ days: 1000 })
}))

comments = ref(comments)
</script>

<template lang="pug">
ul.comments-list
  comment(v-for="(comment, i) in comments" :key="i" :comment="comment")
</template>

<style lang="scss">
.flex {display: flex;}
.align-center {align-items: center;}

.comments-list {
  text-align: left;
}
</style>
