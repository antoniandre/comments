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
const sortedComments = ref(comments.value.sort((a, b) => (a.created > b.created ? -1 : 1)))
</script>

<template lang="pug">
h1 Comments
ul.comments-list
  comment(v-for="(comment, i) in sortedComments" :key="i" :comment="comment")
</template>

<style lang="scss">
.flex {display: flex;}
.align-center {align-items: center;}

.comments-list {
  text-align: left;
}
</style>
