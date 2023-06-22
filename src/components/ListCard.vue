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
      <li v-for="item in props.list" :key="item.content" class="listCard__item" :class="{'hover': item.link}" :style="{marginBottom: `${props.itemMarginBottom * spacing}px`}">
        <span v-if="item.date" class="listCard__item__small" v-text="item.date" />
        <h3 v-if="item.content && !item.link" class="listCard__item__content" v-text="item.content" />
        <a class="listCard__item__link" v-if="item.content && item.link" :href="item.link" target="_blank">
          <h3 class="listCard__item__content" v-text="item.content" />
        </a>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
$spacing: 4px;
.listCard {
  margin-bottom: $spacing * 10;

  &__title {
    font-size: 40px;
    color: #AE0000;
    border-bottom: 2px solid #AE0000;
    margin-bottom: $spacing * 4;
  }

  &__item {
    transition: transform .3s;

    &__small {
      font-size: 20px;
      color: #949494;
    }

    &__content {
      font-size: 24px;
    }

    &__link {
      color: #000000;
      text-decoration: none;
    }

    &.hover:hover {
      transform: translateY(-5px);
    }
  }
}
</style>
