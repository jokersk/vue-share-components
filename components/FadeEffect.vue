<template>
    <div ref="fade" class="transition duration-700 transform" :class="show ? 'opacity-100 translate-x-0' : hiddenStyle">
        <slot></slot>
    </div>
</template>
<script>
export default {
    props: {
        fromLeft: Boolean,
        fromRight: Boolean,
        fromBottom: Boolean
    },
    data() {
        return {
            show: false
        }
    },
    mounted() {
        this.fade()
    },
    computed: {
        hiddenStyle() {
            if (this.fromLeft) {
                return 'opacity-0 -translate-x-2'
            }
            if (this.fromRight) {
                return 'opacity-0 translate-x-2'
            }
            if (this.fromBottom) {
                return 'opacity-0 translate-y-2'
            }
            return 'opacity-0 -translate-x-2'
        }
    },
    methods: {
        fade() {
            const el = this.$refs.fade
            let options = {
                threshold: 0.75
            }

            const observer = new IntersectionObserver(e => {
                e.forEach(item => {
                    this.show = item.isIntersecting
                })
            }, options)

            observer.observe(el)
        }
    }
}
</script>
