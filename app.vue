<script setup lang="ts">
const isOpen: Ref<boolean> = ref(false);

const buttonText: ComputedRef<string> = computed(() => (isOpen.value ? "Close Card" : "Open Card"));

useHead({
    title: "Season's Greetings",
});
</script>

<template>
    <div class="h-screen relative flex justify-center items-center bg-green-400">
        <div class="">
            <div class="card-wrapper">
                <div class="card front-page back" :class="isOpen ? 'open' : ''">
                    <img src="~/assets/images/santa.webp" class="h-[90%] w-[90%] rounded-lg" />
                </div>

                <div class="card front-page relative" :class="isOpen ? 'open' : ''">
                    <div class="">
                        <p class="text-[50px] text-center">Merry Christmas</p>
                        <p class="text-[50px] text-center">to You</p>
                    </div>

                    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 -z-10">
                        <img src="~/assets/images/aricon.jpeg" class="h-10" />
                    </div>

                    <div class="absolute top-2 left-0">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute top-2 right-0">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute bottom-2 left-0">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute bottom-2 right-0">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                </div>

                <div class="card back-page relative" :class="isOpen ? 'open' : ''">
                    <p class="text-[45px] z-10">And a Happy New Year</p>

                    <p class="text z-10">
                        Cheers to more fruitful days <br />
                        in health and wealth
                    </p>

                    <p class="text flex justify-end z-10">~ Jekon</p>

                    <div class="absolute -top-6 -left-6">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute -top-6 -right-6">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute -bottom-6 -left-6">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                    <div class="absolute -bottom-6 -right-6">
                        <img src="~/assets/images/snow-flake.jpeg" class="h-16" />
                    </div>
                </div>
            </div>

            <div class="mt-10 flex justify-end">
                <button @click="isOpen = !isOpen" class="px-4 py-1 text-white font-medium bg-red-500 rounded-md">
                    {{ buttonText }}
                </button>
            </div>
        </div>

        <div class="absolute top-4 right-4">
            <img src="~/assets/images/santa-claus.gif" class="h-40" />
        </div>
    </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Dancing+Script");

.main {
    margin: 0;
    background-color: #4caf50;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    perspective: 1000px;
    transform-style: preserve-3d;
}

.flip-enter-from,
.flip-leave-to {
    transform: translateX(-300px);
}

.flip-enter-to,
.flip-leave-from {
}

.flip-enter-active,
.flip-leave-active {
    transition: all 1.5s cubic-bezier(0.4, 0, 0.2, 1);
    transform-origin: center left;
}

*,
*:after,
*:before {
    box-sizing: border-box;
}

p {
    font-family: "Dancing Script";
    color: green;
}

p.text {
    font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
    font-size: 16px;
}
.card-wrapper {
    width: 350px;
    height: 450px;
    position: relative;
    transform: rotateX(30deg);
    transform-style: preserve-3d;
    box-shadow: 0 4px 2px rgba(0, 0, 0, 0.3);
    border-radius: 6px;
}

.card {
    height: 100%;
    width: 100%;
    background-color: #ffffff;
    border-radius: 2px;
    position: relative;
    border: 8px solid #b60003;
    border-radius: 6px;
    text-align: center;
    padding: 10px;
}
.card.front-page {
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 1.5s cubic-bezier(0.4, 0, 0.2, 1);
    transform-origin: center left;
    position: absolute;
    top: 0;
    left: 0;
    z-index: 20;
    backface-visibility: hidden;
    -webkit-backface-visibility: hidden;
}

.card.front-page.open {
    transform: rotateY(-180deg);
}

.card.front-page.back {
    z-index: 0;
    backface-visibility: visible;
    -webkit-backface-visibility: visible;
}

.card.back-page {
    overflow: hidden;
    padding: 20px 10px;
    display: grid;
    gap: 20px;
}

.card.back-page.open:before {
    transform: translateX(-155%);
    opacity: 0.1;
}
.card.back-page:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
    z-index: 1;
    opacity: 1;
    transition: all 1s ease-in-out;
}
</style>
