<template>
    <section class="benefits">
        <div class="benefits__container">
            <h1 class="benefits__h1">Компенсационный пакет</h1>
            <div class="benefits__items-container">
                <figure class="benefits__item" v-for="item in benefitsItems" :key="item.id">
                    <img :src="item.icon" class="benefits__item-icon" />
                    <figcaption class="benefits__item-text">{{ item.text }}</figcaption>
                </figure>
            </div>
        </div>
        <hr class="benefits__line" />
        <div class="benefits__container">
            <h1 class="benefits__h2">Программа дополнительной мотивации</h1>
            <h2 class="benefits__h2--strong">доплата 12% от суммы</h2>
            <div class="benefits__items-container">
                <figure class="benefits__item" v-for="item in motivationItems" :key="item.id">
                    <img :src="item.icon" class="benefits__item-icon" />
                    <figcaption class="benefits__item-text">{{ item.text }}</figcaption>
                </figure>
            </div>
        </div>
    </section>
</template>

<script>
import { ref } from 'vue';

export default {
    name: 'BenefitsComponent',
    setup() {
        const benefitsItems = [
            { id: 1, icon: 'images/benefits/med.svg', text: 'ДМС' },
            { id: 2, icon: 'images/benefits/cake.svg', text: 'Выходной в день рождения' },
            { id: 3, icon: 'images/benefits/phone.svg', text: 'Корпоративная мобильная связь' },
            { id: 4, icon: 'images/benefits/weight.svg', text: 'Корпоративные скидки на спорт' },
            { id: 5, icon: 'images/benefits/deal.svg', text: 'LTI' },
        ];

        const motivationItems = [
            { id: 1, icon: 'images/benefits/printer.svg', text: 'Оргтехники' },
            { id: 2, icon: 'images/benefits/med.svg', text: 'ДМС' },
            { id: 3, icon: 'images/benefits/house.svg', text: 'Ипотеки' },
        ];

        return {
            benefitsItems,
            motivationItems,
        };
    },
};
</script>

<style lang="scss" scoped>
@use "@/styles/benefits.scss";
</style>
