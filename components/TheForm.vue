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
                        <input
                            type="text"
                            v-model="form.name"
                            name="name"
                            id="name"
                            class="form__input"
                            placeholder="e.g. Matt Surname"
                        >
                        <span class="form__error">This field is required</span>
                    </div>
                    <div class="form__group">
                        <label
                            for="email"
                            class="form__label"
                        >Email Address</label>
                        <span class="form__error">This field is required</span>
                        <input
                            type="email"
                            v-model="form.email"
                            name="email"
                            id="email"
                            class="form__input"
                            placeholder="e.g. email@mail.com"
                        >
                    </div>
                    <div class="form__group">
                        <label
                            for="phone"
                            class="form__label"
                        >Phone Number</label>
                        <span class="form__error">This field is required</span>
                        <input
                            type="tel"
                            v-model="form.phone"
                            name="phone"
                            id="phone"
                            pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
                            class="form__input"
                            placeholder="e.g. +1 345 909 090"
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
const sectionActive = useState('section-active', () => 'step-1')
const form = ref({
    name: "",
    email: "",
    phone: ""
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

.form__group {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: var(--spacing-100);
    margin-block-end: var(--spacing-400);
}

.form__input {
    padding: var(--spacing-200) var(--spacing-400);
    border: 1px solid var(--light-gray);
    border-radius: var(--border-radius-soft);
}

.form__error {
    position: absolute;
    right: 0;
}

/* Add states to all inputs */

input:hover,
input:active {
    padding: calc(var(--spacing-200) - 1.5px) calc(var(--spacing-4  00) - 1.5px);
    border: 1.5px solid var(--purplish-blue)
}



@media screen and (min-width: 1024px) {
    .form {
        height: 568px;
        padding-inline: var(--spacing-1100);
    }

}
</style>