<script setup>
import { ref } from 'vue'
import Comment from '../components/comment.vue'

const comments = ref([
  { id: 1, text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Dicta quis autem expedita libero provident dolor sint impedit, ad possimus, atque similique architecto. Voluptate deserunt consectetur debitis repudiandae ut exercitationem a.', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 2, text: 'Sint rem aspernatur, beatae porro similique recusandae consectetur sed voluptatem blanditiis enim incidunt ipsam ab quasi omnis corporis id repudiandae maxime voluptates? Ex neque vitae nulla fuga, magnam rerum voluptate!', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 3, text: 'Velit voluptas fugiat facere delectus ea, laboriosam reiciendis tenetur eligendi iusto placeat nobis dolor unde molestias nihil harum iste in porro impedit sint, obcaecati non aliquid. Facere asperiores aut exercitationem?', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 4, text: 'Eveniet odit voluptate voluptatibus, aut asperiores natus reprehenderit sint nihil quam fuga temporibus culpa ipsa repudiandae quibusdam, at accusantium vitae? Eum voluptatibus, adipisci sed quam laborum tempora maxime sequi minima!', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 5, text: 'Error dolorum explicabo ad, illo molestias, rem cum nam obcaecati assumenda veniam ratione iste provident! Temporibus blanditiis, ut rerum iure ipsum vel eos voluptatum? Dolores accusantium ipsum dicta dolorem quam.', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 6, text: 'Eum odio sed possimus tempora quo nemo veritatis libero rem deleniti, incidunt praesentium dignissimos aliquam corrupti necessitatibus porro illum. Nesciunt officia voluptatibus hic laudantium quod odit error totam possimus numquam.', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 7, text: 'Corrupti nobis et perspiciatis deserunt voluptatem. Distinctio cum numquam quos quo, vitae incidunt deleniti cupiditate, deserunt totam aperiam iure assumenda sed iusto dolores in tenetur recusandae qui, temporibus fugit perferendis!', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 8, text: 'Libero quis natus delectus laboriosam. Facere voluptates animi ipsa ullam culpa, ab eum quod corrupti quas, voluptatibus ea, velit suscipit earum nam inventore error molestiae rem tempora quia iure libero.', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 9, text: 'Assumenda ipsam, id fugiat nihil doloremque facere officiis sunt eveniet saepe ea molestiae praesentium vero voluptatibus adipisci optio suscipit aut maiores labore rerum neque debitis eaque? Cupiditate fuga consequatur at!', author: 'Antoni', created: '2023-09-08 11:37:46' },
  { id: 10, text: 'Quas natus saepe eius, dolore soluta ab distinctio, illum odio expedita modi possimus velit quaerat iure vero pariatur laboriosam at laudantium neque voluptas officiis. Dolore dignissimos at perspiciatis temporibus voluptatum!', author: 'Antoni', created: '2023-09-08 11:37:46' }
])
</script>

<template lang="pug">
ul.comments-list
  comment(v-for="(comment, i) in comments" :key="i" :comment="comment")
</template>

<style lang="scss">
.flex {display: flex;}
.align-center {align-items: center;}

.comments-list {text-align: left;}
</style>
