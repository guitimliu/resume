<script setup>
import ListCard from './components/ListCard.vue'
import Footer from './components/Footer.vue'
import data from './assets/data.json'

const informationList = [
  {
    content: data.information.list.address,
    link: `https://www.google.com/maps/search/${data.information.list.address}`,
  },
  {
    content: data.information.list.tel,
    link: `tel:${data.information.list.tel}`,
  },
  {
    content: data.information.list.email,
    link: `mailto:${data.information.list.email}`,
  },
  {
    content: data.information.list.website,
    link: `https://${data.information.list.website}`,
  },
];

const awards = data.awards.list.map((item) => {
  return {
    content: item,
  }
});
</script>

<template>
  <div class="home">
    <div class="container">
      <h1 class="home__title" v-if="data.name" v-text="data.name" />
      <!-- <img class="home__avatar" :src="data.avatar" :alt="data.name"> -->
      <img class="home__avatar" src="./assets/avatar.png" :alt="data.name">
      <p class="home__title" v-if="data.title" v-text="data.title" />
    </div>
    <div class="home__desc">
      <div class="container">
        <p v-if="data.desc" class="home__desc__text" v-text="data.desc"/>
      </div>
    </div>
    <div class="container">
      <div class="home__listCard">
        <!-- Vito Evans -->
        <ListCard :title="data.information.title" :list="informationList" :itemMarginBottom="2" />
        <!-- Education -->
        <ListCard :title="data.education.title" :list="data.education.list" :itemMarginBottom="4" />
        <!-- Work -->
        <ListCard :title="data.work.title" :list="data.work.list" :itemMarginBottom="4" />
        <!-- Awards -->
        <ListCard :title="data.awards.title" :list="awards" :itemMarginBottom="3" />
      </div>
    </div>
    <Footer :socialLink="data.socialLink" />
  </div>
</template>

<style lang="scss" scoped>
.home {
  &__title {
    font-size: 192px;

    &:nth-of-type(2) {
      text-align: right;
    }
  }

  &__avatar {
    display: block;
    width: 636px;
    height: 848px;
    margin: auto;
  }

  &__desc {
    background-color: #EFEFEF;
    padding: 48px 0;
    margin-bottom: 80px;

    &__text {
      font-size: 32px;
      width: 50%;
      margin-left: auto;
    }
  }

  &__listCard {
    width: 50%;
    margin-bottom: 160px;
  }
}
</style>
