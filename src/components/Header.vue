<script>
export default {
    data () {
        return {
            menu: false
        }
    },
    watch: {
        menu () {
            if (this.menu) {
                document.querySelector('body').style.overflow = 'hidden';
            } else {
                document.querySelector('body').style.overflow = 'visible';
            }
        }
    }
}
</script>

<template>
    <header class="header">
        <div class="container header__container">
            <a href="" class="header__logo">
                <img :src="$getImage('header-logo.svg')" alt="">
            </a>
            <ul class="header__navs">
                <li>
                    <a href="#" class="header__navs_link">Какие задачи решаем</a>
                </li>
                <li>
                    <a href="#" class="header__navs_link">Инструменты</a>
                </li>
                <li>
                    <a href="#" class="header__navs_link">Тарифы</a>
                </li>
                <li>
                    <a href="#" class="header__navs_link">Почему нас выбирают</a>
                </li>
                <li>
                    <a href="#" class="header__navs_link">Отзывы о нас</a>
                </li>
            </ul>
            <div class="header__right">
                <router-link to="/" class="header__right_link">
                    <span>Войти</span>
                    <img :src="$getImage('user-icon.svg')" alt="">
                </router-link>
                <button @click="menu = true">
                    <img :src="$getImage('bars.svg')" alt="">
                </button>
            </div>
        </div>
    </header>

    <!-- Menu -->
    <div 
        class="menu"
        :class="{
            'active': menu
        }"
    >
        <div class="menu__top">
            <router-link to="/">
                <img :src="$getImage('header-logo.svg')" alt="">
            </router-link>
            <button @click="menu = false">
                <img :src="$getImage('times.svg')" alt="">
            </button>
        </div>
        <ul class="menu__nav">
            <li>
                <router-link to="#" class="menu__nav_link">Какие задачи решаем</router-link>
            </li>
            <li>
                <router-link to="#" class="menu__nav_link">Инструменты</router-link>
            </li>
            <li>
                <router-link to="#" class="menu__nav_link">Тарифы</router-link>
            </li>
            <li>
                <router-link to="#" class="menu__nav_link">Почему нас выбирают селлеры</router-link>
            </li>
            <li>
                <router-link to="#" class="menu__nav_link">Отзывы о нас</router-link>
            </li>
        </ul>
        <button class="menu__btn">
            <img :src="$getImage('support.svg')" alt="">
            <span>Написать в поддержку</span>
        </button>
    </div>
    <!-- Menu end -->
</template>