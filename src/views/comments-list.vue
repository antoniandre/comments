<script setup>
import { ref } from 'vue'
import { faker } from '@faker-js/faker'
import Comment from '../components/comment.vue'

const comments = Array(100).fill('').map((item, i) => ({
  id: i + 1,
  text: faker.lorem.sentences(),
  author: faker.person.fullName(),
  avatar: faker.image.avatarGitHub(),
  created: faker.date.recent({ days: 1000 })
}))

const sortedComments = ref(comments.sort((a, b) => (a.created > b.created ? -1 : 1)))

// One counter that triggers the reactivity of every comment every sec so their age is updated.
// Much better than a setInterval in all the comments.
let commentsAgeCounter = ref(0)
setInterval(() => commentsAgeCounter.value++)
</script>

<template lang="pug">
h1 Comments
ul.comments-list
  comment(v-for="(comment, i) in sortedComments" :key="i" :comment="comment" :counter="commentsAgeCounter")
</template>

<style lang="scss">
.flex {display: flex;}
.align-center {align-items: center;}

.comments-list {
  text-align: left;
}
</style>
