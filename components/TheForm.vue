<template>
    <form
        action=""
        class="form"
    >

        <section
            id="step-1"
            v-if="sectionActive === sections[0]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Personal info"
                    description="Please provide your name, email address, and phone number."
                />

                <div class="form__body">
                    <div class="form__group">
                        <label
                            for="name"
                            class="form__label"
                        >Name</label>
                        <span class="error">This field is required</span>
                        <input
                            type="text"
                            v-model="form.name"
                            name="name"
                            id="name"
                            class="form__input"
                        >
                    </div>
                    <div class="form__group">
                        <label
                            for="email"
                            class="form__label"
                        >Email Address</label>
                        <span class="error">This field is required</span>
                        <input
                            type="email"
                            v-model="form.email"
                            name="email"
                            id="email"
                            class="form__input"
                        >
                    </div>
                    <div class="form__group">
                        <label
                            for="phone"
                            class="form__label"
                        >Phone Number</label>
                        <span class="error">This field is required</span>
                        <input
                            type="tel"
                            v-model="form.phone"
                            name="phone"
                            id="phone"
                            pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
                            class="form__input"
                        >
                    </div>

                </div>
            </div>

            <FormButtons
                :currentSection='sectionActive'
                @go-back="goBack"
                @next-step="nextStep"
            />

        </section>

        <section
            id="step-2"
            v-if="sectionActive === sections[1]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Select your plan"
                    description="You have the option of monthly or yearly billing."
                />
                <div class="form__body"></div>
            </div>

            <FormButtons
                :currentSection='sectionActive'
                @go-back="goBack"
                @next-step="nextStep"
            />

        </section>

        <section
            id="step-3"
            v-if="sectionActive === sections[2]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Pick add-ons"
                    description="Add-ons help enhance your gaming experience."
                />
                <div class="form__body"></div>
            </div>
            <FormButtons
                :currentSection='sectionActive'
                @go-back="goBack"
                @next-step="nextStep"
            />


        </section>

        <section
            id="step-3"
            v-if="sectionActive === sections[3]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Finishing up"
                    description="Double-check everything looks OK before confirming."
                />
                <div class="form__body"></div>
            </div>

            <FormButtons
                :currentSection='sectionActive'
                @go-back="goBack"
                @next-step="nextStep"
            />

        </section>


    </form>
</template>

<script
    setup
    lang="ts"
>

const sections = ['step-1', 'step-2', 'step-3', 'step-4']
const sectionActive = ref('step-1')
const form = ref({
    name: "Some Name",
    email: 'email@mail.com',
    phone: "e.g. +1 345 909 090"
})

const goBack = () => {
    const currentIndex = sections.findIndex(item => item === sectionActive.value)
    if (currentIndex === 0) {
        sectionActive.value = sections[0]
    } else {
        sectionActive.value = sections[currentIndex - 1]
    }
}

const nextStep = () => {
    const currentIndex = sections.findIndex(item => item === sectionActive.value)
    if (currentIndex === sections.length - 1) {
        sectionActive.value = sections[sections.length - 1]
    } else {
        sectionActive.value = sections[currentIndex + 1]
    }
}

</script>

<style scoped>
.form {
    position: relative;
    height: calc(100vh - 172px);
}

.form__wrapper {
    width: min(100%, 550px);
    margin-inline: auto;
    padding-block: var(--spacing-800);
    padding-inline: var(--spacing-400);
    background-color: var(--white);
}

@media screen and (min-width: 1024px) {
    .form {
        height: 568px;
        padding-inline: var(--spacing-1100);
    }

    /* .form__description {
        margin-block-end: var(--spacing-800);
    } */

}
</style>