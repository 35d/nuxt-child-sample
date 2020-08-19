<template>
  <div class="container">
    <div class="l-list-area">
      <ul class="list">
        <li class="list__item" @click="_onClickAdd">
          追加
        </li>
        <li
          v-for="(_, index) in tasks"
          class="list__item"
          :key="_"
          @click="
            () => {
              $router.push(`/tasks/${index}`)
            }
          "
        >
          {{ _ }}
        </li>
      </ul>
    </div>
    <div class="l-detail-area">
      <nuxt-child />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      tasks: ['task0', 'task1', 'task2'],
    }
  },
  mounted() {},
  methods: {
    _click(index: number) {
      this.$router.push(`/tasks/${index}`)
    },
    _onClickAdd() {
      this.tasks.push(`task${this.tasks.length}`)
    },
  },
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex: 1;
}

.l-list-area {
  background-color: #fafafa;
  flex: 1;
}

.l-detail-area {
  flex: 1;
}

.list {
  padding-left: 0;
}

.list__item {
  list-style: none;
  padding: 12px 24px;
  border-bottom: 1px solid #eee;
}

.list__item:hover {
  background-color: #f0f0f0;
  cursor: pointer;
}
</style>
