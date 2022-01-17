<template>
  <div class="hints">
    <aside class="aside">
      <div class="burger">
        <span></span>
      </div>
      <nav class="nav">
        <ul class="nav__list">
          <li class="nav__item"> <span>01</span> У Бога новый проект</li>
          <li class="nav__item nav__item-active"><span>02</span> Подсказки</li>
          <li class="nav__item"><span>03</span> Вопросы и ответы</li>
        </ul>
      </nav>
      <div class="scroll-next">
        <span class="text-o-vertical">Скрольте дальше </span> <img :src="Arrow" alt="">
      </div>
    </aside>
    <main>
      <header class="header">
        <div class="header__logo">
          <img :src="KinopoiskLogo" alt="Кинопоиск лого">
        </div>
        <h1 class="header__title title">
          Они должны что-то знать
        </h1>
      </header>
      <div class="slider">
        <div class="slider__counter">
          <span>{{ currentSlide + 1}} / {{ this.slidesList.length }}</span>
        </div>
        <div class="slide__container">
          <img
            class="slide__btn_prev"
            src="./assets/images/prev.png"
            alt="Назад"
            v-if="this.currentSlide > 0"
            @click="prevSlide()"
          >
          <Slide
            v-for="(slide, index) in slidesList"
            :key="index"
            :index="index"
            :slide_data="slide"
            :currentSlide="currentSlide"
          />
          <img
            class="slide__btn_next"
            src="./assets/images/next.png"
            alt="Далее"
            v-if="!(this.currentSlide == this.slidesList.length - 1)"
            @click="nextSlide">
        </div>
        <button class="slider__btn">Искать промокод <img src="./assets/images/Arrow.png" alt=""> </button>
      </div>
    </main>
    <img class="slider__clouds" src="./assets/images/cloudsNormal.png" alt="">
    <div class="rightside-link text-o-vertical">
      hd.kinopoisk.ru
    </div>
  </div>
</template>

<script>
import Slide from './components/Slide.vue'
import Arrow from './assets/images/Arrow down.png'

import KinopoiskLogo from './assets/images/KinopoiskLogo.png'
import Racer from './assets/images/slider/Racer.png'
import Redliff from './assets/images/slider/Redliff.png'
import Buschemi from './assets/images/slider/Buschemi.png'
import Visvanathan from './assets/images/slider/Visvanathan.png'

export default {
  name: 'App',
  components: {
    Slide
  },
  data () {
    return {
      KinopoiskLogo: KinopoiskLogo,
      slidesList: [
        {
          img: Racer,
          text: 'Для примера мы показали вам его лицо.  В первой серии он прячется в подвалеза мониторами, и пусть борода не собьёт вас с толку. Найдите героя и нажмите  на паузу — ему не терпится отдать вам промокод.'
        },
        {
          img: Visvanathan,
          text: 'Сотрудница отдела ответов на молитвы в Небесной канцелярии, энергична и инициативна. Она видела промокод, когда пробегала мимо журналиство в 3-й серии у кабинета Бога.'
        },
        {
          img: Redliff,
          text: 'Ангел, работает в отделе ответов на молитвы уже тясячу лет. У него есть промокол CRAIG0, который дает скидку 50% на покупку или аренду любых двух фильмов на hd.kinopoisk.ru'
        },
        {
          img: Buschemi,
          text: 'Создатель Земли и босс небесной канцелярии. Он растерял все промокоды - возможно, что-то завалялось в доме его родителей в 6-й серии.'
        }
      ],
      currentSlide: 0,
      Arrow: Arrow
    }
  },
  methods: {
    nextSlide () {
      if ((this.currentSlide >= 0) && (this.currentSlide <= this.slidesList.length - 2)) {
        this.currentSlide++
      }
    },
    prevSlide () {
      if (this.currentSlide > 0) {
        this.currentSlide--
      }
    }
  }
}
</script>

<style lang="scss">
.wrapper {
  display: flex;
}
</style>
