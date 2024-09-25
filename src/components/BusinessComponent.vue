<template>
    <section class="business">
        <div class="accordion">
            <h1>Направления бизнеса</h1>
            <div v-for="(item, index) in accordionItems" :key="index"
                :class="['accordion__container', { 'accordion__container--opened': activeIndex === index }]"
                @click="toggle(index)">
                <div class="accordion__content-wrapper">
                    <p class="accordion__label">{{ item.label }}</p>
                    <span class="accordion__arrow arrow">
                        <span class="arrow__left-piece"></span>
                        <span class="arrow__right-piece"></span>
                    </span>
                    <p class="accordion__content">{{ item.content }}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import { ref } from 'vue';

export default {
    name: 'BusinessComponent',
    setup() {
        const activeIndex = ref(null);
        const accordionItems = [
            {
                label: 'Решения Softline',
                content: 'ГК Softline предлагает клиентам собственную линейку оборудования (ПК, серверы, торговое оборудование и проч.), разработку программных продуктов, облачных решений, решений в области информационной безопасности.',
            },
            {
                label: 'Кибербезопасность',
                content: 'Softline обладает всеми необходимыми государственными лицензиями для организации проектов по информационной безопасности и аттестации.',
            },
            {
                label: 'Импортозамещение',
                content: 'ГК Softline обладает широчайшим портфелем решений и услуг для импортозамещения, включая ПО и оборудование собственного производства.',
            },
            {
                label: 'Облачные решения',
                content: 'Softline использует современные облачные решения как российских, так и международных вендоров для масштабирования бизнеса своих клиентов. Подписки, услуги, трансформация.',
            },
            {
                label: 'Цифровая трансформация и разработка ПО',
                content: 'Softline использует современные технологи и новые возможности для увеличения производительности бизнеса заказчика. В штате ГК Softline - 2000+ разработчиков, которые трансформируют ПО под нужды конкретного предприятия.',
            },
            {
                label: 'Техническая поддержка Softline',
                content: '200+ инженеров, 24 часа в сутки, 7 дней в неделю, 12 месяцев в году, сервисное партнерство с 30+ мировыми производителями.',
            },
        ];

        const toggle = (index) => {
            if (window.innerWidth >= 1024) return;
            activeIndex.value = activeIndex.value === index ? null : index;
        };

        return {
            accordionItems,
            activeIndex,
            toggle,
        };
    },
};
</script>

<style lang="scss" scoped>
@use "@/styles/business.scss";
</style>
