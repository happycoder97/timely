<template>
  <div class="h-screen flex flex-col">
    <nav class="p-2 flex space-x-4 bg-white">
      <div
        v-for="tab in tabs"
        :key="tab"
        class="border-b border-gray-100"
        :class="tab_active == tab?'border-red-500':'hover:border-red-300'"
        @click="tab_active=tab"
      >
        {{ tab }}
      </div>
    </nav>
    <main class="flex-1 flex flex-col overflow-y-auto">
      <Boards v-if="tab_active == 'Boards'" />
      <Timetable v-if="tab_active == 'Timetable'" />
    </main>
  </div>
</template>

<script>
import Boards from './Boards.vue'
import Timetable from './Timetable.vue'

export default {
  components: {
    Boards,
    Timetable
  },
  data: function () {
    return {
      tabs: ['Boards', 'Timetable', 'Timetrack'],
      tab_active: 'Boards'
    }
  }
}
</script>
