<script>
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
import { Swiper, SwiperSlide } from 'swiper/vue';

import 'swiper/css';

import 'swiper/css/pagination';
import 'swiper/css/navigation';

import { Pagination, Navigation } from 'swiper/modules';
import { ref, onMounted } from "vue";

export default {
  components: {
    Header,
    Footer,
    Swiper,
    SwiperSlide,
  },
  setup() {
    const tarifSwp = ref(null);

    const onSwiper = (swiperInstance) => {
      tarifSwp.value = swiperInstance;
    };

    const goToFirstSlide = (idx) => {
      if (tarifSwp._value.slideTo(idx)) {
        tarifSwp._value.slideTo(idx)
      }
    }

    return {
      tarifSwp,
      onSwiper,
      goToFirstSlide,
      modules: [Pagination],
    };
  },
  data () {
    return {
      tarif: 1,
      discount: 4,
    }
  },
  methods: {
  },
}
</script>

<template>
  <div class="wrapper">

    <!-- Header -->
    <Header />
    <!-- Header end -->

    <main>

      <!-- Tarif -->
      <section class="tarif">
        <div class="container tarif__container">
          <h2 class="sec-title tarif__title">Тарифы</h2>
          <ul class="tarif__type" :class="`active-${tarif}`">
            <li 
              @click="goToFirstSlide(0)"
              :class="{
                'active': tarif == 1
              }"
            >Бесплатно</li>
            <li 
              @click="goToFirstSlide(1)"
              :class="{
                'active': tarif == 2
              }"
            >Базовый</li>
            <li 
              @click="goToFirstSlide(2)"
              :class="{
                'active': tarif == 3
              }"
            >Расширенный</li>
          </ul>
          <div class="tarif__discount">
            <h3>Выберите срок подписки</h3>
            <div class="line">
              <span :class="`active-${discount}`"></span>
            </div>
            <ul>
              <li @click="discount = 1">
                <span 
                  class="icon"
                  :class="{
                    'active': discount >= 1,
                    'hidden': discount == 1
                  }"></span>
                <p class="desk">1 месяц</p>
              </li>
              <li @click="discount = 2">
                <span 
                  class="icon"
                  :class="{
                    'active': discount >= 2,
                    'hidden': discount == 2
                  }"></span>
                <p class="desk">3 месяца <span>(-10%)</span></p>
              </li>
              <li @click="discount = 3">
                <span 
                  class="icon"
                  :class="{
                    'active': discount >= 3,
                    'hidden': discount == 3
                  }"></span>
                <p class="desk">6 месяцев <span>(-20%)</span></p>
              </li>
              <li @click="discount = 4">
                <span 
                  class="icon"
                  :class="{
                    'active': discount >= 4,
                    'hidden': discount == 4
                  }"></span>
                <p class="desk">12 месяцев <span>(-30%)</span></p>
              </li>
            </ul>
          </div>
          <swiper
            slidesPerView="auto"
            :spaceBetween="10"
            :initial-slide="1"
            :speed="500"
            :centeredSlides="true"
            :breakpoints="{
              992: {
                slidesPerView: 3,
                centeredSlides: false,
                spaceBetween: 16,
              }
            }"
            @slideChange="(swiper) => {
              tarif = swiper.realIndex + 1;
            }"
            class="tarif__swp"
            @swiper="onSwiper"
          >
            <swiper-slide class="tarif__card">
              <div class="line"></div>
              <h4 class="title">Бесплатно</h4>
              <p class="subtitle">Телеграм-бот MARKETPROD</p>
              <h3 class="price">0 ₽</h3>
              <div class="status">Что включено:</div>
              <div class="networks">
                <a href="#">
                  <img :src="$getImage('wb.svg')" alt="">
                  <span>1 кабинет </span>
                </a>
                <a href="#">
                  <img :src="$getImage('tg-blue.svg')" alt="">
                  <span>Телеграм-бот</span>
                </a>
              </div>
              <button class="btn">Выбрать тариф</button>
              <ul>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Прогнозная прибыль <br>от продаж за день</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Сводка о вчерашних продажах</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Поиск и уведомления <br>о найденных поставках</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Оповещения о низком балансе <br>на рекламе</p>
                </li>
              </ul>
            </swiper-slide>
            <swiper-slide class="tarif__card">
              <div class="line bg-violet"></div>
              <h4 class="title">Базовый</h4>
              <p class="subtitle">Доступны все инструменты</p>
              <h3 class="price">990 ₽/месяц</h3>
              <div class="status">Что включено:</div>
              <div class="networks">
                <a href="#">
                  <img :src="$getImage('wb.svg')" alt="">
                  <span>1 кабинет </span>
                </a>
                <a href="#">
                  <img :src="$getImage('tg-blue.svg')" alt="">
                  <span>Телеграм-бот</span>
                </a>
              </div>
              <button class="btn">Выбрать тариф</button>
              <ul>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Прогнозная прибыль <br>от продаж за день</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Рекомендации по отгрузке товаров на склады</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Расчет прибыли за периоды</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Детальная сводка о продажах</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Отслеживание позиций карточек по запросам</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Поиск и уведомления <br>о найденных поставках</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Оповещения о низком балансе <br>на рекламе</p>
                </li>
              </ul>
            </swiper-slide>
            <swiper-slide class="tarif__card">
              <div class="line bg-gradient"></div>
              <h4 class="title">Расширенный</h4>
              <p class="subtitle">Доступны все инструменты <span>+ 7 кабинетов</span></p>
              <h3 class="price">4950 ₽/месяц</h3>
              <div class="status">Что включено:</div>
              <div class="networks">
                <a href="#">
                  <img :src="$getImage('wb.svg')" alt="">
                  <span>7 кабинет </span>
                </a>
                <a href="#">
                  <img :src="$getImage('tg-blue.svg')" alt="">
                  <span>Телеграм-бот</span>
                </a>
              </div>
              <button class="btn">Выбрать тариф</button>
              <ul>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Прогнозная прибыль <br>от продаж за день</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Рекомендации по отгрузке товаров на склады</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Расчет прибыли за периоды</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Детальная сводка о продажах</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Отслеживание позиций карточек по запросам</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Поиск и уведомления о найденных поставках</p>
                </li>
                <li>
                  <img :src="$getImage('check-icon-2.svg')" alt="">
                  <p>Оповещения о низком балансе <br>на рекламе</p>
                </li>
              </ul>
            </swiper-slide>
          </swiper>
        </div>
      </section>
      <!-- Tarif end -->

      <!-- Promo code -->
      <section class="promo-code">
        <div class="container promo-code__container">
          <h2 class="promo-code__title">Введите <br> промокод</h2>
          <img :src="$getImage('promo-code-card.png')" alt="" class="promo-code__card">
          <img :src="$getImage('promo-code-card-mb.png')" alt="" class="promo-code__card mb">
          <div class="promo-code__form">
            <input type="text" placeholder="Введите цифры">
            <button>
              <span>Применить</span>
              <img :src="$getImage('check-btn-icon.svg')" alt="">
            </button>
          </div>
        </div>
      </section>
      <!-- Promo code end -->

    </main>

    <!-- Footer -->
    <Footer />
    <!-- Footer end -->

  </div>
</template>