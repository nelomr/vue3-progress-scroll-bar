<template>
    <div class="progress-bar--container" :style="`${positionValue};`">
        <div
            :style="`background-color: ${colorValue}; width: ${width}%;`"
            class="progress-bar"
            >
        </div>
    </div>
</template>
<script>
import {computed, ref, onMounted} from 'vue';

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
        const width = ref(0);
        const colorValue = computed(() => (props.color));
        const positionValue = computed(() => {
            let position = props.position;
            if (position === 'top' || position === 'bottom') {
                return `${position}: 0`;
            }
            return 'top: 0';
        });
    
        function progress() {
            let documentHeight = (document.documentElement.scrollHeight - document.documentElement.clientHeight);
            width.value = (window.scrollY*100) / documentHeight;
        }

        onMounted(() => {
            document.addEventListener('scroll', function(){ 
                progress();
            });
        })

        return {colorValue, positionValue, progress, width};
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
