<script setup lang="ts">
import { ref } from 'vue'
import { getOne } from '@/models/users'
import { useRoute } from 'vue-router'


const route = useRoute('/users/[id]')
const user = getOne(route.params.id)

const boxContent = ref(
  'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.',
)

function removeNotification(index: number) {
  notifications.value.splice(index, 1)
}

function deleteBox() {
  boxContent.value = ''
}
</script>

<template>
  <div class="box" v-if="boxContent">
    <article class="media">
      <div class="media-left">
        <figure class="image is-64x64">
          <img src="https://bulma.io/assets/images/placeholders/128x128.png" alt="Image" />
        </figure>
      </div>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>John Smith</strong> <small>@johnsmith</small>
            <small>31m</small>
            <br />
            {{ boxContent }}
          </p>
        </div>
        <nav class="level is-mobile">
          <div class="level-left">
            <a class="level-item" aria-label="reply">
              <span class="icon is-small">
                <i class="fas fa-reply" aria-hidden="true"></i>
              </span>
            </a>
            <a class="level-item" aria-label="retweet">
              <span class="icon is-small">
                <i class="fas fa-retweet" aria-hidden="true"></i>
              </span>
            </a>
            <a class="level-item" aria-label="like">
              <span class="icon is-small">
                <i class="fas fa-heart" aria-hidden="true"></i>
              </span>
            </a>
          </div>
        </nav>
      </div>
      <button class="delete" @click="deleteBox"></button>
    </article>
  </div>
</template>

<style scoped></style>
