<template>
    <section class="numbers">
        <div class="numbers__number-container">
            <h1 class="numbers__number">
                <span class="numbers__number-accent numbers__number-accent--font-black">&gt;</span>
                30 лет
            </h1>
            <p class="numbers__text">на IT-рынке</p>
        </div>
        <div class="numbers__number-container">
            <h1 class="numbers__number">4600</h1>
            <p class="numbers__text">сотрудников в России</p>
        </div>
        <div class="numbers__number-container">
            <h1 class="numbers__number">25</h1>
            <p class="numbers__text">городов России</p>
        </div>
        <div class="numbers__number-container">
            <h1 class="numbers__number">
                2000 <span class="numbers__number-accent">+</span>
            </h1>
            <p class="numbers__text">разработчиков</p>
        </div>
        <div class="numbers__number-container">
            <h1 class="numbers__number">
                3000 <span class="numbers__number-accent">+</span>
            </h1>
            <p class="numbers__text--line-height-120">
                сотрудников ежегодно<br />
                проходят оценку и обучение
            </p>
        </div>
    </section>
</template>

<script>
export default {
    name: 'NumbersComponent',
};
</script>

<style lang="scss" scoped>
@use "@/styles/numbers.scss";
</style>
