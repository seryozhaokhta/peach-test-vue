<template>
    <section class="corp-life">
        <div class="corp-life__glide glide">
            <div class="glide__controls-container">
                <h2>Корпоративная жизнь</h2>
                <div class="glide__arrows" data-glide-el="controls">
                    <button class="glide__arrow glide__arrow--left" data-glide-dir="<">
                        <!-- SVG для левой стрелки -->
                        <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <rect width="56" height="56" rx="28" transform="matrix(-1 0 0 1 56 0)" fill="#F0F0F0" />
                            <path d="M33 18L23 28L33 38" stroke="#A30C33" stroke-width="2" />
                        </svg>
                    </button>
                    <button class="glide__arrow glide__arrow--right" data-glide-dir=">">
                        <!-- SVG для правой стрелки -->
                        <svg width="56" height="56" viewBox="0 0 56 56" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <rect width="56" height="56" rx="28" fill="#F0F0F0" />
                            <path d="M23 18L33 28L23 38" stroke="#A30C33" stroke-width="2" />
                        </svg>
                    </button>
                </div>
            </div>
            <div class="glide__track" data-glide-el="track">
                <ul class="glide__slides">
                    <li class="glide__slide" v-for="slide in slides" :key="slide.id">
                        <img :src="slide.large" :srcset="`${slide.sm} 280w, ${slide.large} 1110w`"
                            sizes="(max-width: 600px) 280px, 1100px" :alt="`Slide ${slide.id}`" />
                    </li>
                </ul>
            </div>
            <div class="glide__bullets" data-glide-el="controls[nav]">
                <button v-for="slide in slides" :key="slide.id" class="glide__bullet"
                    :data-glide-dir="`=${slide.id - 1}`"></button>
            </div>
        </div>
    </section>
</template>

<script>
import { ref, onMounted } from 'vue';
import Glide from '@glidejs/glide';

export default {
    name: 'CorpLifeComponent',
    setup() {
        const slides = ref([
            { id: 1, sm: 'images/corp-life/sm/1.png', large: 'images/corp-life/large/1.png' },
            { id: 2, sm: 'images/corp-life/sm/2.png', large: 'images/corp-life/large/2.png' },
            { id: 3, sm: 'images/corp-life/sm/3.png', large: 'images/corp-life/large/3.png' },
            { id: 4, sm: 'images/corp-life/sm/4.png', large: 'images/corp-life/large/4.png' },
            { id: 5, sm: 'images/corp-life/sm/5.png', large: 'images/corp-life/large/5.png' },
        ]);

        onMounted(() => {
            new Glide('.glide', {
                type: 'carousel',
                autoplay: 5000,
            }).mount();
        });

        return {
            slides,
        };
    },
};
</script>

<style lang="scss" scoped>
@use "@/styles/corp-life.scss";
</style>
