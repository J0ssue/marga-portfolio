<template>
    <section
        class="base-section mb-32"
        :id="settings.slug"
    >
        <div class="flex items-center justify-center">
            <h2
                class="mr-4 section-title-size apoc-revelations-italic"
                v-html="settings.title"
            />
            <button
                class="focus:outline-none plus-cursor"
                @click="toggleTextVisibility"
            ><span v-show="!isDescriptionVisible">+</span><span v-show="isDescriptionVisible">-</span></button>
        </div>
        <p
            class="mb-6 text-center lausanne section-subtitle-size"
            v-text="settings.subtitle"
        />
        <div
            class="base-section__dynamic-text flex justify-center mb-8"
            :class="{
                'show-text': isDescriptionVisible,
                'hide-text': !isDescriptionVisible,
            }"
        >
            <p
                class="w-3/6"
                v-html="settings.description"
            />
        </div>
        <div>
            <VueSlickCarousel v-bind="carouselSettings">
                <div
                    class="arrow-right-cursor"
                    v-for="(img, i) in settings.images"
                    :key="i"
                >
                    <img
                        class="section-img block mx-auto"
                        :src="img"
                        alt="project image"
                    >
                </div>
            </VueSlickCarousel>
        </div>
    </section>
</template>

<script>
    export default {
        props: {
            settings: {
                type: Object
            }
        },
        data() {
            return {
                isDescriptionVisible: false,
                carouselSettings: {
                    "dots": true,
                    "focusOnSelect": false,
                    "infinite": true,
                    "speed": 500,
                    "slidesToShow": 1,
                    "slidesToScroll": 1,
                    "touchThreshold": 5,
                }
            };
        },
        methods: {
            toggleTextVisibility() {
                this.isDescriptionVisible = !this.isDescriptionVisible;
            }
        },
    }
</script>