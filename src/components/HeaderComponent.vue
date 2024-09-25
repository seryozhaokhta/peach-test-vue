<template>
    <header class="header">
        <img src="/images/logo.svg" alt="softline logo" class="header__logo" />
        <nav class="header__nav">
            <ul>
                <li><a href="#">Облачные решения</a></li>
                <li><a href="#">Кибербезопасность</a></li>
                <li><a href="#">Импортозамещение</a></li>
                <li><a href="#">Цифровая трансформация</a></li>
            </ul>
        </nav>
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
};
</script>

<style lang="scss" scoped>
@use "@/styles/header.scss";
</style>
