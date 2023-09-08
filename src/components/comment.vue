<script setup>
const formatTimeAgo = date => {
  if (typeof date === 'string') date = new Date(date.replace(/-/g, '/'))

  const ageInSeconds = (new Date().getTime() - date.getTime()) / 1000 // Delta seconds to now.
  if (ageInSeconds >= 3600 * 24 * 365) date = '1 year ago'
  else if (ageInSeconds >= 3600 * 24 * 30) date = '1 month ago'
  else if (ageInSeconds >= 3600 * 24) date = '1 day ago'
  else if (ageInSeconds >= 3600) date = '1 hour ago'
  else if (ageInSeconds >= 60) date = '1 minute ago'
  else if (ageInSeconds >= 10) date = '10 seconds ago'
  else if (ageInSeconds < 10) date = 'Just now'

  return date
}

defineProps({
  comment: Object
})
</script>

<template lang="pug">
li.comment
  .flex.align-center
    img.comment__avatar(:src="comment.avatar")
    .comment__author {{ comment.author }}
    .comment__date , {{ formatTimeAgo(comment.created) }} - {{ comment.created }}
  p.comment__text {{ comment.text }}
</template>

<style lang="scss">
.comment {
  list-style-type: none;
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 8px;
  background-color: rgba(124, 124, 124, 0.03);

  &:nth-child(odd) {
    background-color: rgba(124, 124, 124, 0.08);
  }

  &__avatar {
    border-radius: 99em;
    width: 1.5rem;
    aspect-ratio: 1;
    margin-right: 0.75rem;
  }

  &__author {
    font-weight: bold;
  }

  &__date {
    color: #ffffff69;
    font-size: 0.8rem;
  }

  &__text {
    margin: 0.75rem 0 0;
    line-height: 1.2;
    font-size: 0.9rem;
    color: #ffffffbe;
  }
}
</style>
