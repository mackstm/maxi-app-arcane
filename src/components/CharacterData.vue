<template>
    <div>
        
    </div>
</template>

<script>
    import { defineComponent, ref } from 'vue';

    export default defineComponent({
        name: 'CounterComposition',
        setup() {
            const counter = ref(0);

            const increment = () => {
                counter.value++;
            };

            const subtract = () => {
                if (counter.value > 0) {
                    counter.value--;
                }
            }

            const double = () => {
                counter.value *= 2;
            }

            const restart = () => {
                counter.value = 0;
            }

            const updateCounter = (event) => {
                counter.value = Math.abs(parseInt(event.target.value));
            }

            return { counter, increment, subtract, double, restart, updateCounter};
        }
    })
</script>

<style lang="scss" scoped>

</style>