<template>
    <form action="">

        <section
            id="step-1"
            v-if="sectionActive === sections[0]"
        >
            <div class="form__description">
                <h2>Personal info</h2>
                <p>Please provide your name, email address, and phone number.</p>
            </div>

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
            <div class="form__description">
                <h2>Select your plan</h2>
                <p>You have the option of monthly or yearly billing.</p>
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
            <div class="form__description">
                <h2>Pick add-ons</h2>
                <p>Add-ons help enhance your gaming experience.</p>
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
            <div class="form__description">
                <h2>Finishing up</h2>
                <p>Double-check everything looks OK before confirming.</p>
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
.form__description h2 {
    font-size: var(--font-size-800);
}

.form__description p {
    color: var(--cool-gray);
    font-weight: var(--font-weight-bold);
}
</style>