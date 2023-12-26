
<template>
 <section class="banner">
          <div class="container">
            <div class="banner-item">
              <h2 class="banner-item--title">
                Онлайн-сервис <br />
                доставки еды на дом
              </h2>
              <p class="banner-item--subtitle">
                Блюда из любимого ресторана привезет курьер в перчатках, маске и
                с антисептиком
              </p>
            </div>
          </div>
        </section>
        <section class="products">
          <div class="container">
            <div class="products-header">
              <h3 class="products-header--title">Рестораны</h3>
              <input
                type="text"
                class="products-header--search"
                placeholder="Поиск блюд и ресторанов"
              />
            </div>
            <div class="products-wrapper" id="rests-container">
              <router-link 
              class="products-card" 
              v-for="rest in restArray" 
              :key="rest.id"
              :to="`/rest?id=${rest.id}`" 
              >
                <div class="products-card__image">
                  <img :src="getUrl(rest.image)" alt="image-1" />
                </div>
                <div class="products-card__description">
                  <div class="products-card__description-row">
                    <h4 class="products-card__description--title">
                      {{ rest.title }}
                    </h4>
                    <div class="products-card__description--badge">{{ rest.time }} мин</div>
                  </div>
                  <div class="products-card__description-row">
                    <div class="products-card__description-info">
                      <div class="products-card__description-info--raiting">
                        <img src="../assets/images/icons/Star.svg" alt="Star" />
                        {{ rest.rating }}
                      </div>
                      <div class="products-card__description-info--price">
                        От {{ rest.price }} €
                      </div>
                      <div class="products-card__description-info--groap">
                        {{ rest.type }}
                      </div>
                    </div>
                  </div>
                </div>
              </router-link>
            
            </div>
          </div>
        </section>
</template>

<script setup>
// import  Header  from '../components/Header1.vue'
// import Footer from '../components/Footer.vue'
import {restArray} from '../constants/rests'
  const getUrl = (name) => {
    return new URL(`../assets/images/restorans/${name}`, import.meta.url)
  }
 
</script>