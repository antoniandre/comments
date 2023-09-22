<script setup>

// All in seconds.
const durations = {
  second: 1,
  minute: 60,
  hour: 3600,
  day: 86400,
  week: 604800,
  month: 2592000,
  year: 31536000
}

const formatTimeAgo = date => {
  if (typeof date === 'string') date = new Date(date.replace(/-/g, '/'))

  const ageInSeconds = (new Date().getTime() - date.getTime()) / 1000 // Delta seconds to now.

  if (ageInSeconds < 10) return 'Just now' // Less than 10s ago.

  Object.entries(durations).forEach(([durationName, durationValue], i) => {
    if (ageInSeconds >= durationValue) {
      const number = ~~(ageInSeconds / durationValue)
      date = `${number} ${durationName}${number > 1 ? 's' : ''} ago`
    }
  })

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
    color: var(--title-color);
  }

  &__date {
    color: var(--discrete-color);
    font-size: 0.8rem;
  }

  &__text {
    margin: 0.75rem 0 0;
    line-height: 1.2;
    font-size: 0.9rem;
    color: var(--body-color);
  }
}
</style>
