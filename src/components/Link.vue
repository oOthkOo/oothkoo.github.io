<script setup>
    const props = defineProps([
        'link'
    ])
    const link = props.link

    const onLinkClick = (e, l) => {
        if (l.click) {
            e.preventDefault()
            l.click()
        }
    }
</script>

<template>
    <a
        class="link"
        :href="link.url"
        target="_blank"
        @click="(e) => onLinkClick(e, link)"
    >
        <div class="content">
            <div class="icon">
                <font-awesome-icon
                    :icon="link.icon"
                    size="lg"
                    color="white"
                />
            </div>
            <div class="text">{{ link.text }}</div>
        </div>
    </a>
</template>

<style scoped>
    .link {
        text-decoration: none;
        color: #2b2b2b;

        .content {
            height: 54px;
            padding: .25rem 1.5rem;
            display: flex;
            align-items: center;

            .icon {
                width: 40px;
                height: 40px;
                max-width: 40px;
                display: flex;
                justify-content: center;
                align-items: center;
                border-radius: 50%;
                background: rgba(53,57,59);
            }
            .text {
                margin-left: 15px;
                font-size: 1rem;
                font-weight: 700;
                line-height: 1.4;
            }
        }
        .content:hover {
            background: rgba(53,57,59, .05)
        }
    }
</style>