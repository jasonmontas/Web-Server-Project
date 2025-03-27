<script setup lang="ts">
import { onMounted, ref } from 'vue'
import NotificationList from '@/components/NotificationList.vue'

// State for dropdown functionality
const isDropdownActive = ref(false)
const selectedType = ref('Select Type')

// Functions to handle dropdown
function toggleDropdown() {
  isDropdownActive.value = !isDropdownActive.value
}

function selectType(type: string) {
  selectedType.value = type
  isDropdownActive.value = false
}

// Functions to open and close a modal
function openModal($el: HTMLElement | null) {
  if ($el) {
    $el.classList.add('is-active')
  }
}

function closeModal($el: HTMLElement | null) {
  if ($el) {
    $el.classList.remove('is-active')
  }
}

function closeAllModals() {
  ;(document.querySelectorAll('.modal') || []).forEach(($modal) => {
    closeModal($modal as HTMLElement)
  })
}

onMounted(() => {
  // Add a click event on buttons to open a specific modal
  ;(document.querySelectorAll('.js-modal-trigger') || []).forEach(($trigger) => {
    const modal = ($trigger as HTMLElement).dataset.target
    const $target = document.getElementById(modal || '')

    $trigger.addEventListener('click', () => {
      openModal($target)
    })
  })

  // Add a click event on various child elements to close the parent modal
  ;(
    document.querySelectorAll(
      '.modal-background, .modal-close, .modal-card-head .delete, .modal-card-foot .button',
    ) || []
  ).forEach(($close) => {
    const $target = ($close as HTMLElement).closest('.modal')

    $close.addEventListener('click', () => {
      closeModal($target as HTMLElement)
    })
  })

  // Add a keyboard event to close all modals
  document.addEventListener('keydown', (event) => {
    if (event.key === 'Escape') {
      closeAllModals()
    }
  })
})
</script>

<template>
  <div class="about">
    <h1 class="title">My Workouts</h1>
    <button class="js-modal-trigger button is-link" data-target="modal-js-example">
      Add Workout
    </button>
    <NotificationList />
  </div>

  <div id="modal-js-example" class="modal">
    <div class="modal-background"></div>

    <div class="modal-content">
      <div class="box">
        <h1 class="title">Add Workout</h1>
        <div class="field">
          <label class="label">Title</label>
          <div class="control">
            <input class="input" type="text" placeholder="Text input" />
          </div>
        </div>

        <div class="field">
          <label class="label">Date</label>
          <div class="control has-icons-left">
            <input class="input" type="date" placeholder="Select date" />
            <span class="icon is-small is-left">
              <i class="fas fa-calendar-alt"></i>
            </span>
          </div>
        </div>

        <div class="field">
          <label class="label">Duration</label>
          <div class="control">
            <input class="input" type="text" placeholder="Text input" />
          </div>
        </div>

        <div class="field">
          <label class="label">Location</label>
          <div class="control">
            <input class="input" type="text" placeholder="Text input" />
          </div>
        </div>

        <div class="field">
          <label class="label">Picture</label>
          <div class="control">
            <input class="input" type="text" placeholder="Text input" />
          </div>
        </div>

        <div class="field">
          <label class="label">Type</label>
          <div :class="['dropdown', { 'is-active': isDropdownActive }]">
            <div class="dropdown-trigger">
              <button class="button" aria-haspopup="true" aria-controls="dropdown-menu4" @click="toggleDropdown">
                <span>{{ selectedType }}</span>
                <span class="icon is-small">
                  <i class="fas fa-angle-down" aria-hidden="true"></i>
                </span>
              </button>
            </div>
            <div class="dropdown-menu" id="dropdown-menu4" role="menu">
              <div class="dropdown-content">
                <a href="#" class="dropdown-item" @click.prevent="selectType('Run')">Run</a>
                <a href="#" class="dropdown-item" @click.prevent="selectType('Bike')">Bike</a>
                <a href="#" class="dropdown-item" @click.prevent="selectType('Walk')">Walk</a>
                <a href="#" class="dropdown-item" @click.prevent="selectType('Cardio')">Cardio</a>
                <a href="#" class="dropdown-item" @click.prevent="selectType('Strength')">Strength</a>
              </div>
            </div>
          </div>
        </div>

        <div class="field is-grouped">
          <div class="control">
            <button class="button is-link" @click="closeAllModals">Submit</button>
          </div>
          <div class="control">
            <button class="button is-link is-light" @click="closeAllModals">Cancel</button>
          </div>
        </div>
      </div>
    </div>

    <button class="modal-close is-large" aria-label="close"></button>
  </div>
</template>

<style>
title {
  font-size: 2rem;
  text-align: center;
}
</style>
