<script setup>
import { ref } from 'vue';

const props = defineProps({
  title: {
    type: String,
  },
  list: {
    type: Object,
  },
  itemMarginBottom: {
    type: Number,
  },
});

const spacing = ref(4);
</script>

<template>
  <div class="listCard">
    <h2 v-if="props.title" class="listCard__title" v-text="props.title" />
    <ul v-if="list" class="listCard__list">
      <li v-for="item in props.list" :key="item.content" class="listCard__item" :style="{marginBottom: `${props.itemMarginBottom * spacing}px`}">
        <span v-if="item.date" class="listCard__item__small" v-text="item.date" />
        <h3 v-if="item.content" class="listCard__item__content" v-text="item.content" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
$spacing: 4px;
.listCard {
  margin-bottom: $spacing * 10;
  line-height: 1.5;

  &__title {
    font-size: 40px;
    color: #AE0000;
    border-bottom: 2px solid #AE0000;
    margin-bottom: $spacing * 4;
  }

  &__item {
    &__small {
      font-size: 20px;
      color: #949494;
    }

    &__content {
      font-size: 24px;
    }
  }
}
</style>
