<template>
    <form
        action=""
        class="form"
    >

        <section
            id="step-1"
            class="padding-inline-sd-400"
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
            class="padding-inline-sd-400"
            id="step-2"
            v-if="sectionActive === sections[1]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Select your plan"
                    description="You have the option of monthly or yearly billing."
                />
                <div class="form__body">
                    <div class="plan__wrapper">
                        <!-- Arcade plan -->
                        <input
                            type="radio"
                            id="arcade"
                            value="arcade"
                            v-model="form.selectPlan"
                            class="plan__input hide-input"
                        />
                        <label
                            for="arcade"
                            class="plan__label"
                        >
                            <img
                                src="/images/icon-arcade.svg"
                                alt="Arcade plan"
                            >
                            <span class="plan__description">
                                <span class="plan__title">Arcade</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'monthly'"
                                >$9/mo</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'yearly'"
                                >$90/yr</span>
                                <span
                                    class="plan__free"
                                    v-if="form.selectPeriod === 'yearly'"
                                >2 months free</span>
                            </span>
                        </label>
                        <!-- Advanced plan -->
                        <input
                            type="radio"
                            id="advanced"
                            value="advanced"
                            v-model="form.selectPlan"
                            class="plan__input hide-input"
                        />
                        <label
                            for="advanced"
                            class="plan__label"
                        >
                            <img
                                src="/images/icon-advanced.svg"
                                alt="Arcade plan"
                            >

                            <span class="plan__description">
                                <span class="plan__title">Advanced</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'monthly'"
                                >$12/mo</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'yearly'"
                                >$120/yr</span>
                                <span
                                    class="plan__free"
                                    v-if="form.selectPeriod === 'yearly'"
                                >2 months free</span>
                            </span>
                        </label>
                        <!-- Pro plan -->
                        <input
                            type="radio"
                            id="pro"
                            value="pro"
                            v-model="form.selectPlan"
                            class="plan__input hide-input"
                        />
                        <label
                            for="pro"
                            class="plan__label"
                        >
                            <img
                                src="/images/icon-pro.svg"
                                alt="Arcade plan"
                            >

                            <span class="plan__description">
                                <span class="plan__title">Pro</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'monthly'"
                                >$15/mo</span>
                                <span
                                    class="plan__price"
                                    v-if="form.selectPeriod === 'yearly'"
                                >$150/yr</span>
                                <span
                                    class="plan__free"
                                    v-if="form.selectPeriod === 'yearly'"
                                >2 months free</span>
                            </span>
                        </label>
                    </div>

                    <div class="period__wrapper">

                        <div class="period__switch">
                            <input
                                type="radio"
                                id="monthly"
                                value="monthly"
                                v-model="form.selectPeriod"
                                class="period__input period__input--left"
                            />
                            <label
                                for="monthly"
                                class="period__label period__label--left"
                            >
                                Monthly
                            </label>

                            <input
                                type="radio"
                                id="yearly"
                                value="yearly"
                                v-model="form.selectPeriod"
                                class="period__input period__input--right"
                            />
                            <label
                                for="yearly"
                                class="period__label period__label--right"
                            >
                                Yearly
                            </label>

                            <div class="period__overlay"></div>
                        </div>



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
            class="padding-inline-sd-400"
            id="step-3"
            v-if="sectionActive === sections[2]"
        >
            <div class="form__wrapper">
                <FormDescriptions
                    title="Pick add-ons"
                    description="Add-ons help enhance your gaming experience."
                />
                <div class="form__body">
                    <div class="add-ons__wrapper">
                        <!-- Online service -->
                        <input
                            type="checkbox"
                            name="add-ons"
                            id="online-service"
                            value="online-service"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="online-service"
                            class="add-ons__label"
                        >
                            <span class="flex-row gap-500">

                                <span class="add-ons__desc">
                                    <span class="plan__title">Online service</span>
                                    <span class="plan__price">Access to multiplayer games</span>
                                </span>
                            </span>
                            <span
                                v-if="form.selectPeriod === 'monthly'"
                                class="color-purple"
                            >+$1/mo</span>
                            <span
                                v-if="form.selectPeriod === 'yearly'"
                                class="color-purple"
                            >+$10/yr</span>
                        </label>

                        <!-- Larger storage -->
                        <input
                            type="checkbox"
                            name="add-ons"
                            id="larger-storage"
                            value="larger-storage"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="larger-storage"
                            class="add-ons__label"
                        >
                            <span class="flex-row gap-500">

                                <span class="add-ons__desc">
                                    <span class="plan__title">Larger storage</span>
                                    <span class="plan__price">Extra 1TB of cloud save</span>
                                </span>
                            </span>
                            <span
                                v-if="form.selectPeriod === 'monthly'"
                                class="color-purple"
                            >+$2/mo</span>
                            <span
                                v-if="form.selectPeriod === 'yearly'"
                                class="color-purple"
                            >+$20/yr</span>
                        </label>

                        <!-- Customizable profile -->
                        <input
                            type="checkbox"
                            name="add-ons"
                            id="customizable-profile"
                            value="customizable-profile"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="customizable-profile"
                            class="add-ons__label"
                        >
                            <span class="flex-row gap-500">

                                <span class="add-ons__desc">
                                    <span class="plan__title">Customizable profile</span>
                                    <span class="plan__price">Custom theme on your profile.</span>
                                </span>
                            </span>
                            <span
                                v-if="form.selectPeriod === 'monthly'"
                                class="color-purple"
                            >+$2/mo</span>
                            <span
                                v-if="form.selectPeriod === 'yearly'"
                                class="color-purple"
                            >+$20/yr</span>
                        </label>
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
            class="padding-inline-sd-400"
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
    name: '',
    email: '',
    phone: '',
    selectPlan: 'arcade',
    selectPeriod: 'monthly'
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
    width: min(100%, 470px);
    margin-inline: auto;
}

.form__wrapper {
    margin-inline: auto;
    margin-block-start: var(--spacing-form);
    padding-block: var(--spacing-800);
    padding-inline: var(--spacing-400);
    border-radius: var(--border-radius-10);
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
    border-radius: var(--border-radius-5);
}

.form__error {
    position: absolute;
    right: 0;
}

/* Section SELECT PLAN */

.plan__wrapper,
.add-ons__wrapper {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-400)
}

.plan__label {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-900);
    padding: var(--spacing-400);
    border: 1px solid var(--light-gray);
    border-radius: var(--border-radius-5);
}


.plan__description {
    display: flex;
    flex-direction: column;
}

.plan__title {
    color: var(--marine-blue);
    font-weight: var(--font-weight-bold);
}

.plan__price {
    color: var(--cool-gray);
    font-weight: var(--font-weight-bold);
}

.plan__free {
    color: var(--marine-blue);
}

/* Period */

.period__wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: var(--spacing-400);
    margin-block: var(--spacing-800);
    padding: var(--spacing-400);
    background-color: var(--magnolia);
    border-radius: var(--border-radius-10);
}

.period__switch {
    position: relative;
    display: flex;
    height: 25px;
    width: 45px;
    background: var(--marine-blue);
    border-radius: 25px;
}

.period__input {
    position: relative;
    top: -2px;
    height: 100%;
    width: 50%;
    background: transparent;
    appearance: none;
}

.period__overlay {
    position: absolute;
    top: 50%;
    left: 5px;
    transform: translateY(-50%);
    height: 17px;
    width: 17px;
    border-radius: 50%;
    background: var(--white);
    transition: all 0.3s ease-in;
    z-index: 10;
    pointer-events: none;
}

.period__input--left:checked+.period__overlay {
    left: 10px;
}

.period__input--right:checked~.period__overlay {
    left: 22.5px;
}


.period__input--left:checked+.period__label--left,
.period__input--right:checked+.period__label--right {
    color: var(--marine-blue);
}

.period__label {
    position: absolute;
    color: var(--cool-gray);
    font-weight: var(--font-weight-bolder)
}

.period__label--left {
    left: -75px;
}

.period__label--right {
    left: 60px;
}

/* Add states to all inputs */

/* input:checked+label {
    border: 1.5px solid var(--purplish-blue);
} */

.plan__input:checked+.plan__label,
.plan__label:hover {
    border: 1.5px solid var(--purplish-blue);
    padding: calc(var(--spacing-400) - 0.5px);
}

.add-ons__label:hover,
.add-ons__input:checked+.add-ons__label {
    border: 1.5px solid var(--purplish-blue);
    padding-block: calc(var(--spacing-400) - 0.5px);
    padding-inline: calc(60px - 0.5px) calc(var(--spacing-400) - 0.5px);
}

/* input:hover,
input:active {
    padding: calc(var(--spacing-200) - 0.5px) calc(var(--spacing-400) - 0.5px);
    border: 1.5px solid var(--purplish-blue)
} */

/* Add-ons */

.add-ons__label {
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-block: var(--spacing-400);
    padding-inline: 60px var(--spacing-400);
    border: 1px solid var(--light-gray);
    border-radius: var(--border-radius-10);
}

.add-ons__label::before {
    content: '';
    position: absolute;
    left: 20px;
    height: 20px;
    width: 20px;
    border: 1px solid var(--light-gray);
    border-radius: var(--border-radius-5);
}

.add-ons__input:checked+.add-ons__label::before {
    content: "\2713";
    display: grid;
    place-content: center;
    color: var(--white);
    border: 1px solid var(--purplish-blue);
    background-color: var(--purplish-blue);
}

.add-ons__desc {
    display: flex;
    flex-direction: column;
}



@media screen and (min-width: 1024px) {
    .form {
        height: 568px;
        width: 500px;
        margin-inline: var(--spacing-1100);
    }

    .form__wrapper {
        margin-block-start: 0;
    }

    /* Section SELECT PLAN */

    .plan__wrapper {
        flex-direction: row;
    }

    .plan__label {
        flex-direction: column;
        flex-grow: 1;
        flex-basis: 0;
    }

}
</style>