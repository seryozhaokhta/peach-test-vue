<template>
    <section class="map">
        <div class="map__menu">
            <div :class="['map__dropdown', dropdownOpened ? 'map__dropdown--opened' : 'map__dropdown--closed']"
                @click="toggleDropdown">
                Офисы Softline
                <span class="map__dropdown-arrow arrow">
                    <span class="arrow__left-piece"></span>
                    <span class="arrow__right-piece"></span>
                </span>
                <nav class="map__navbar" v-if="dropdownOpened">
                    <ul class="map__navlist">
                        <li class="map__nav-item"><a href="#">Москва</a></li>
                        <li v-for="(region, index) in expandableRegions" :key="index"
                            :class="['map__nav-item--expandable', { 'map__nav-item--expanded': expandedRegion === region.value }]"
                            @click.stop="toggleExpandable(region.value)">
                            <p class="map__nav-item-text">{{ region.label }}</p>
                            <div class="triangle"></div>
                            <ul class="map__nav-nested-list" v-if="expandedRegion === region.value">
                                <li class="map__nav-item" v-for="(city, idx) in region.cities" :key="idx">
                                    <a href="#">{{ city }}</a>
                                </li>
                            </ul>
                        </li>
                    </ul>
                </nav>
            </div>

            <fieldset class="map__tabs">
                <input type="radio" value="all" id="region-all" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-all" class="map__tab-text">Все</label>

                <input type="radio" value="moscow" id="region-moscow" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-moscow" class="map__tab-text">Москва</label>

                <input type="radio" value="center" id="region-center" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-center" class="map__tab-text">Центр</label>

                <input type="radio" value="north-west" id="region-north-west" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-north-west" class="map__tab-text">Северо-Запад</label>

                <input type="radio" value="south" id="region-south" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-south" class="map__tab-text">Юг</label>

                <input type="radio" value="volga" id="region-volga" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-volga" class="map__tab-text">Волга</label>

                <input type="radio" value="ural" id="region-ural" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-ural" class="map__tab-text">Урал</label>

                <input type="radio" value="siberia" id="region-siberia" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-siberia" class="map__tab-text">Сибирь</label>

                <input type="radio" value="far-east" id="region-far-east" name="map-region" class="map__tab-input"
                    v-model="selectedRegion" /><label for="region-far-east" class="map__tab-text">Дальний Восток</label>
            </fieldset>
        </div>

        <div class="map__map-container">
            <object class="map__map-img" type="image/svg+xml" :data="mapData"></object>
        </div>
    </section>
</template>

<script>
import { ref, onMounted, watch } from 'vue';

export default {
    name: 'MapComponent',
    setup() {
        const dropdownOpened = ref(false);
        const expandedRegion = ref(null);
        const selectedRegion = ref('all');
        const mapData = ref(`${import.meta.env.BASE_URL}images/map.svg`);


        const expandableRegions = [
            { label: 'Центр', value: 'center', cities: ['Воронеж', 'Ярославль', 'Белгород'] },
            { label: 'Северо-Запад', value: 'north-west', cities: ['Санкт-Петербург', 'Калининград'] },
            { label: 'Юг', value: 'south', cities: ['Ростов-на-Дону', 'Краснодар', 'Волгоград'] },
            { label: 'Волга', value: 'volga', cities: ['Казань', 'Самара', 'Уфа', 'Оренбург', 'Нижний Новгород'] },
            { label: 'Урал', value: 'ural', cities: ['Екатеринбург', 'Челябинск', 'Пермь', 'Сургут', 'Тюмень', 'Ижевск'] },
            { label: 'Сибирь', value: 'siberia', cities: ['Новосибирск', 'Омск', 'Томск', 'Красноярск', 'Иркутск'] },
            { label: 'Дальний Восток', value: 'far-east', cities: ['Хабаровск', 'Владивосток'] },
        ];

        const toggleDropdown = () => {
            dropdownOpened.value = !dropdownOpened.value;
        };

        const toggleExpandable = (regionValue) => {
            if (window.innerWidth >= 1024) return;
            if (expandedRegion.value === regionValue) {
                expandedRegion.value = null;
            } else {
                expandedRegion.value = regionValue;
            }
        };

        watch(selectedRegion, (newVal) => {
            const mapObject = document.querySelector('.map__map-img');
            if (mapObject && mapObject.contentDocument) {
                const regions = mapObject.contentDocument.querySelectorAll('g[data-map-region]');
                regions.forEach((region) => {
                    if (newVal === 'all' || region.getAttribute('data-map-region') === newVal) {
                        region.style.display = 'block';
                    } else {
                        region.style.display = 'none';
                    }
                });
            }
        });

        return {
            dropdownOpened,
            expandedRegion,
            toggleDropdown,
            toggleExpandable,
            expandableRegions,
            selectedRegion,
            mapData,
        };
    },
};
</script>

<style lang="scss" scoped>
@use "@/styles/corp-life.scss";
</style>
