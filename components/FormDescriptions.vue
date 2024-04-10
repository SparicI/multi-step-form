<template>
    <div class="form__description">
        <h2>
            {{ title }}
        </h2>
        <p>
            {{ description }}
        </p>
    </div>
</template>

<script
    setup
    lang="ts"
>

const props = defineProps({
    title: {
        type: String,
        default: ''
    },
    description: {
        type: String,
        default: ''
    }
})

</script>

<style scoped>
.form__description {
    margin-block-end: var(--spacing-400);
}

.form__description h2 {
    font-size: var(--font-size-800);
}

.form__description p {
    color: var(--cool-gray);
    font-weight: var(--font-weight-bold);
}

@media screen and (min-width: 1024px) {

    .form__description {
        margin-block-end: var(--spacing-800);
    }

}
</style>