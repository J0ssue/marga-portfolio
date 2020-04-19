<template>
    <div
        class="bg-black text-white lausanne relative"
        id="layout-default"
    >
        <nav class="navigation w-full z-10 flex base-font-size px-8 py-6 fixed top-0 left-0">
            <div class="">
                <p
                    class="nav-text-shadow"
                    to="#"
                    v-text="nav.brand"
                />
            </div>
            <div class="home__nav-btn">
                <div class="relative">
                    <button
                        class="flex mx-auto nav-text-shadow focus:outline-none arrow-down-cursor"
                        @click="toggleNav"
                    >
                        <img
                            class="inline-block -mt-2"
                            src="/images/icons/arrow-icon.png"
                            alt="arrow icon"
                        >
                        <span>index</span>
                    </button>
                    <!-------------- dropdown  -------------------->
                    <div
                        class="navigation-dropdown"
                        :class="{
                        'fade-out': !isDropdownOpen,
                        'fade-in': isDropdownOpen
                    }"
                    >
                        <ul>
                            <li>
                                <button
                                    class="hand-cursor"
                                    v-text="'No Singular Narrative'"
                                    @click="navigateTo('#ns')"
                                />
                            </li>
                            <li>
                                <button
                                    class="hand-cursor"
                                    @click="navigateTo('#line-editorial')"
                                    v-text="'A Line Which Forms a Volume 3'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#line-editorial')"
                                    v-text="'Editorial Design'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#line-curation')"
                                    v-text="'Curation'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#line-visual')"
                                    v-text="'Visual'"
                                />
                            </li>
                            <li>
                                <button
                                    @click="navigateTo('#picture-exhibition')"
                                    v-text="'Pictures of an Exhibition'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#picture-exhibition')"
                                    v-text="'Curation'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#picture-editorial')"
                                    v-text="'Editorial Design'"
                                />
                            </li>
                            <li>
                                <button
                                    class="hand-cursor"
                                    @click="navigateTo('#microscopic-editorial')"
                                    v-text="'FMTBTCI'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#microscopic-editorial')"
                                    v-text="'Editorial Design'"
                                />
                            </li>
                            <li>
                                <button
                                    class="ml-12 gray-text hand-cursor"
                                    @click="navigateTo('#microscopic-video')"
                                    v-text="'Video'"
                                />
                            </li>
                            <li>
                                <button
                                    class="hand-cursor"
                                    @click="navigateTo('#ten')"
                                    v-text="'Ten Different Ways'"
                                />
                            </li>
                            <li>
                                <button
                                    class="hand-cursor"
                                    @click="navigateTo('#algorithm')"
                                    v-text="'Algorithmic Archive'"
                                />
                            </li>
                            <li>
                                <button
                                    class="hand-cursor"
                                    @click="navigateTo('#trust')"
                                    v-text="'Trust me, I will (not) deceive you'"
                                />
                            </li>
                        </ul>
                        <!-------------- dropdown  -------------------->
                    </div>
                </div>
            </div>
            <div class="home__nav-contact">
                <a
                    class="apoc-revelations-italic inline-block italic-text-shadow hand-cursor"
                    :href="`mailto:${myEmail}`"
                    target="_blank"
                    v-text="nav.contact"
                />
            </div>
            <div class="flex-1 pl-8">
            </div>
        </nav>
        <p class="home__hero-text hero-text">
            Graphic designer from Lisbon,<br> recently graduated from London<br> College of Communication with<br> an MA in
            <a
                class="apoc-revelations-italic italic-text-shadow hand-cursor"
                href="http://magmd.uk/"
                target="_blank"
            >
                Graphic Media Design<br>
            </a>
            Continuously researching on<br> editorial strategies, navigation<br> and <button
                @click="openCreativityDocument"
                class="apoc-revelations-italic italic-text-shadow focus:outline-none hand-cursor"
            >creativity</button>, with a particular<br> interest in editorial design.,
        </p>
        <nuxt />
        <footer class="flex px-8 pb-8">
            <div>
                <a
                    class="flex items-center hand-cursor"
                    href="https://shop.magculture.com/products/a-line-which-forms-a-volume-3?_pos=1&_sid=1d27693fe&_ss=r"
                    target="_blank"
                >
                    <img
                        src="/images/icons/arrow-icon.png"
                        alt="arrow icon"
                    >
                    <span>MagCulture</span>
                </a>
                <div class="gray-text">
                    &copy; Margarida Morais
                </div>
            </div>
            <div class="separator flex-1"></div>
            <div>
                <div class="flex justify-end">
                    <button
                        class="focus:outline-none arrow-up-cursor"
                        @click="scrollToTop"
                    >
                        <img
                            src="/images/icons/arrow-up.png"
                            alt="arrow up"
                        ></button>
                </div>
                <div>
                    <a
                        class="hand-cursor"
                        :href="`mailto:${myEmail}`"
                        target="_blank"
                        v-text="footer.email"
                    />
                </div>
            </div>
        </footer>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                isDropdownOpen: false,
                myEmail: 'example@example.com',
                nav: {
                    brand: 'Margarida Morais',
                    contact: 'Contact for commissions or collaborations'
                },
                footer: {
                    email: 'Contact for project enquiries. CV available on request'
                },
            };
        },
        methods: {
            openCreativityDocument() {
                window.open('/pdfs/No_Singular_Narrative.pdf', '_blank');
            },
            navigateTo(link) {
                let element = document.querySelector(link);
                element.scrollIntoView({
                    block: "start",
                    behavior: "smooth",
                });
                this.toggleNav();
            },
            scrollToTop() {
                window.scroll({
                    top: 0,
                    left: 0,
                    behavior: 'smooth'
                });
            },
            toggleNav() {
                this.isDropdownOpen = !this.isDropdownOpen;
            }
        },
    }
</script>
