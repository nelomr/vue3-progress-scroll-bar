<template>
    <div class="progress-bar--container" :style="`${positionValue};`">
        <div
            v-scroll
            :style="`background-color: ${colorValue};`"
            class="progress-bar"
            >
        </div>
    </div>
</template>
<script>
import {computed} from 'vue';

export default {
    props: {
        color: {
            type: String,
            default: '#000'
        },
        position: {
            type: String,
            default: 'top'
        }
    },
    setup(props) {
        const colorValue = computed(() => (props.color));
        const positionValue = computed(() => {
            let position = props.position;
            if (position === 'top' || position === 'bottom') {
                return `${position}: 0`;
            }
            return 'top: 0';
        });

        return {colorValue, positionValue};
    },
    directives: {
        scroll: {
            mounted(el) {
                document.addEventListener('scroll', () => {
                    const documentHeight = (document.documentElement.scrollHeight - document.documentElement.clientHeight);
                    const width = (window.scrollY*100) / documentHeight;
                    el.style['width'] = `${width}%`;
                });
            }
        }
    }
}
</script>

<style lang="postcss" scoped>
    .progress-bar--container {
        position: fixed;
        left: 0;
        right: 0;
        width: 100%;
        height: 5px;
    }

    .progress-bar {
        position: relative;
        width: 0;
        height: 100%;
        transition: width .1s ease;
    }
</style>
