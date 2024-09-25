<template>
  <div id="app">
    <HeaderComponent />
    <BannerComponent />
    <AboutComponent />
    <NumbersComponent />
    <MapComponent />
    <MissionComponent />
    <BusinessComponent />
    <BenefitsComponent />
    <CorpLifeComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import BannerComponent from './components/BannerComponent.vue';
import AboutComponent from './components/AboutComponent.vue';
import NumbersComponent from './components/NumbersComponent.vue';
import MapComponent from './components/MapComponent.vue';
import MissionComponent from './components/MissionComponent.vue';
import BusinessComponent from './components/BusinessComponent.vue';
import BenefitsComponent from './components/BenefitsComponent.vue';
import CorpLifeComponent from './components/CorpLifeComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    BannerComponent,
    AboutComponent,
    NumbersComponent,
    MapComponent,
    MissionComponent,
    BusinessComponent,
    BenefitsComponent,
    CorpLifeComponent,
  },
};
</script>

<style lang="scss"></style>
