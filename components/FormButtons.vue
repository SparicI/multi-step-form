<template>
    <div class="form__controls">
        <button
            v-if="currentSection !== 'step-1'"
            type="button"
            class="button button--secondary"
            @click="$emit('goBack')"
        >Go Back</button>
        <button
            :type="currentSection === 'step-4' ? 'submit' : 'button'"
            class="button button--primary"
            @click="$emit('nextStep')"
        >
            <span v-if="currentSection === 'step-4'">Confirm</span>
            <span v-else>Next Step</span>

        </button>
    </div>
</template>

<script
    setup
    lang="ts"
>

const props = defineProps({
    currentSection: {
        type: String,
        default: 'step-1'
    }
})

</script>

<style scoped></style>