<template>
    <form
        @submit.prevent="formSubmited = true"
        class="form"
    >

        <!----------------------------- SECTION PERSONAL INFO ------------------------------------------- -->
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
                    <div class="profile__group flex-column">
                        <label
                            for="name"
                            class="profile__label"
                        >Name</label>
                        <input
                            type="text"
                            v-model="form.name"
                            name="name"
                            id="name"
                            class="profile__input input-border"
                            :class="{ error: error?.name === true }"
                            placeholder="e.g. Matt Appleseed"
                            required
                        >
                        <span
                            class="profile__error"
                            v-if="error.name"
                        >This field is required</span>
                    </div>
                    <div class="profile__group flex-column">
                        <label
                            for="email"
                            class="profile__label"
                        >Email Address</label>
                        <input
                            type="email"
                            v-model="form.email"
                            name="email"
                            id="email"
                            class="profile__input input-border"
                            :class="{ error: error?.email === true || error?.emailPattern }"
                            placeholder="e.g. email@mail.com"
                            required
                        >
                        <span
                            class="profile__error"
                            v-if="error.email"
                        >This field is required</span>
                        <span
                            class="profile__error"
                            v-if="error.emailPattern"
                        >
                            Invalid format
                        </span>
                    </div>
                    <div class="profile__group flex-column">
                        <label
                            for="phone"
                            class="profile__label"
                        >Phone Number</label>
                        <input
                            type="tel"
                            v-model="form.phone"
                            name="phone"
                            id="phone"
                            class="profile__input input-border"
                            :class="{ error: error?.phone === true }"
                            placeholder="e.g. +1 345 909 090"
                            required
                        >
                        <span
                            class="profile__error"
                            v-if="error.phone"
                        >This field is required</span>
                    </div>

                </div>
            </div>

            <FormButtons
                :currentSection='sectionActive'
                @go-back="goBack"
                @next-step="nextStep"
            />

        </section>

        <!----------------------------- SECTION SELECT PLAN ------------------------------------------- -->
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
                    <div class="plan__wrapper flex-column">
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
                            class="plan__label input-border "
                        >
                            <img
                                src="/images/icon-arcade.svg"
                                alt="Arcade plan"
                            >
                            <span class="flex-column">
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
                            class="plan__label input-border"
                        >
                            <img
                                src="/images/icon-advanced.svg"
                                alt="Arcade plan"
                            >

                            <span class="flex-column">
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
                            class="plan__label input-border"
                        >
                            <img
                                src="/images/icon-pro.svg"
                                alt="Arcade plan"
                            >

                            <span class="flex-column">
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

        <!----------------------------- SECTION PICK ADD-ONS ------------------------------------------- -->
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
                    <div class="add-ons__wrapper flex-column">

                        <!-- Online service -->
                        <input
                            type="checkbox"
                            name="add-ons"
                            id="online-service"
                            value="online-service"
                            v-model="form.addOns"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="online-service"
                            class="add-ons__label flex-row-space-between flex-row-space-between input-border"
                        >
                            <span class="flex-row gap-500">

                                <span class="flex-column">
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
                            v-model="form.addOns"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="larger-storage"
                            class="add-ons__label flex-row-space-between input-border"
                        >
                            <span class="flex-row gap-500">

                                <span class="flex-column">
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
                            v-model="form.addOns"
                            class="add-ons__input hide-input"
                        />
                        <label
                            for="customizable-profile"
                            class="add-ons__label flex-row-space-between input-border"
                        >
                            <span class="flex-row gap-500">

                                <span class="flex-column">
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

        <!----------------------------- SECTION SUMMARY  --------------------------------------------- -->
        <section
            class="padding-inline-sd-400 height-100"
            id="step-3"
            v-if="sectionActive === sections[3]"
        >
            <div v-if="formSubmited === false">
                <div class="form__wrapper">
                    <FormDescriptions
                        title="Finishing up"
                        description="Double-check everything looks OK before confirming."
                    />
                    <div class="form__body">
                        <div class="summary__details">
                            <div class="flex-row-space-between summary__item--top">
                                <div>
                                    <p>{{ paymentOptions?.[form.selectPlan as keyof PaymentOptions]?.title }}
                                        ({{ form.selectPeriod }})</p>
                                    <button
                                        @click="sectionActive = sections[1]"
                                        class="summary__button"
                                    >Change</button>
                                </div>
                                <p>${{ paymentOptions?.[form.selectPlan as keyof
            PaymentOptions]?.[form.selectPeriod]
                                    }}/<span v-if="form.selectPeriod === 'monthly'">mo
                                    </span>
                                    <span v-else>yr</span>
                                </p>
                            </div>
                            <div
                                class="flex-row-space-between summary__item--bottom"
                                v-for="item in form.addOns"
                            >
                                <p class="color-grey">{{ paymentOptions?.[item]?.title }}</p>
                                <p>+${{ paymentOptions?.[item as keyof typeof paymentOptions]?.[form.selectPeriod]
                                    }}/<span v-if="form.selectPeriod === 'monthly'">mo
                                    </span>
                                    <span v-else>yr</span>
                                </p>
                            </div>
                        </div>
                        <div class="summary__total">
                            <div class="summary__item">
                                <p class="color-grey">Total
                                    <span v-if="form.selectPeriod === 'monthly'">(per month)</span>
                                    <span v-else>(per year)</span>
                                </p>
                                <p class="color-purple font-weight-bolder font-size-600">
                                    +${{ totalPrice
                                    }}/<span v-if="form.selectPeriod === 'monthly'">mo
                                    </span>
                                    <span v-else>yr</span>
                                </p>

                            </div>


                        </div>
                    </div>
                </div>

                <FormButtons
                    :currentSection='sectionActive'
                    @go-back="goBack"
                    @next-step="nextStep"
                />

            </div>

            <div
                v-else
                class="form__success flex-column"
            >
                <img
                    src="/images/icon-thank-you.svg"
                    alt="Thank you"
                >
                <FormDescriptions
                    title="Thank you!"
                    description="Thanks for confirming your subscription! We hope you have fun using this platform. If you need support, please feel free to email us at support@loremgaming.com"
                />

            </div>

        </section>


    </form>
</template>

<script
    setup
    lang="ts"
>

type PaymentOptions = {
    [category: string]: {
        [category: string]: string | number,
    }
}

type Form = {
    name: string,
    email: string,
    phone: string,
    selectPlan: string,
    selectPeriod: string,
    addOns: string[]
}

const paymentOptions: PaymentOptions = {
    arcade: {
        title: 'Arcade',
        monthly: 9,
        yearly: 90
    },
    advanced: {
        title: 'Advanced',
        monthly: 12,
        yearly: 120
    },
    pro: {
        title: 'Pro',
        monthly: 15,
        yearly: 150
    },
    'online-service': {
        title: 'Online service',
        monthly: 1,
        yearly: 10
    },
    'larger-storage': {
        title: 'Larger storage',
        monthly: 2,
        yearly: 20
    },
    'customizable-profile': {
        title: 'Customizable profile',
        monthly: 2,
        yearly: 20
    },

}

const sections = ['step-1', 'step-2', 'step-3', 'step-4']
const sectionActive = useState('section-active', () => 'step-1')
const formSubmited = ref(false)
const form = ref<Form>({
    name: '',
    email: '',
    phone: '',
    selectPlan: 'arcade',
    selectPeriod: 'monthly',
    addOns: []
})

const error = ref({
    name: false,
    email: false,
    emailPattern: false,
    phone: false
})

const totalPrice = computed(() => {
    const addOns = form.value.addOns.reduce((acc: number, current: string) => {
        const temp: number = paymentOptions?.[current]?.[form.value.selectPeriod] as number
        acc += temp
        return acc
    }, 0) as number
    return (paymentOptions?.[form.value.selectPlan]?.[form.value.selectPeriod] as number) + addOns
})

// Validate form

const validateProfileSection = () => {
    let result = true
    if (!form?.value.name) {
        error.value.name = true
        result = false
    }

    if (!form?.value.email) {
        error.value.email = true
        result = false
    }

    const regexEmail = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g

    if (form?.value.email && !regexEmail.test(form?.value.email)) {
        error.value.emailPattern = true
        result = false
    }

    if (!form?.value.phone) {
        error.value.phone = true
        result = false
    }

    return result
}

// Reset form errors

const resetFormErrors = () => {
    error.value.name = false
    error.value.email = false
    error.value.emailPattern = false
    error.value.phone = false
}

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
    resetFormErrors()
    if (currentIndex === 0 && !validateProfileSection()) {
        return
    }
    if (currentIndex === sections.length - 1) {
        sectionActive.value = sections[sections.length - 1]
    } else {
        sectionActive.value = sections[currentIndex + 1]
    }
}


</script>

<style>
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

/* ------------------------------------------ Profile ------------------------------------------------- */

.profile__group {
    position: relative;
    gap: var(--spacing-100);
    margin-block-end: var(--spacing-400);
}

.profile__input {
    padding: var(--spacing-200) var(--spacing-400);
}

.profile__error {
    position: absolute;
    right: 0;
    font-weight: var(--font-weight-bold);
    color: var(--strawberry-red);
}

.profile__input.error {
    border: 1px solid var(--strawberry-red);
}



/* --------------------------------------- SELECT PLAN --------------------------------------------- */

.plan__wrapper,
.add-ons__wrapper {
    gap: var(--spacing-400)
}

.plan__label {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-900);
    padding: var(--spacing-400);
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

/* ---------------------------------- Period ------------------------------------------ */

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

/*  ---------------------------------------- Add-ons -------------------------------------------- */

.add-ons__label {
    position: relative;
    padding-block: var(--spacing-400);
    padding-inline: 60px var(--spacing-400);
}

.add-ons__label::before {
    content: '';
    position: absolute;
    left: 20px;
    height: 20px;
    width: 20px;
    border: 1px solid var(--light-gray);
    border-radius: var(--border-radius-soft);
}

.add-ons__input:checked+.add-ons__label::before {
    content: url(/public/images/icon-checkmark.svg);
    display: grid;
    place-content: center;
    background-color: var(--purplish-blue);
}

/* ------------------------------------------ Summary ------------------------------------------------- */

.summary__details {
    padding: var(--spacing-500);
    border-radius: var(--border-radius-10);
    background-color: var(--magnolia);
}

.summary__total {
    padding: var(--spacing-500);
}

.summary__item--top {
    padding-block-end: var(--spacing-700);
    border-bottom: 1px solid var(--light-gray);
    font-weight: var(--font-weight-bolder);
}

.summary__item--bottom {
    margin-block-start: var(--spacing-400);
}

.summary__button {
    background-color: transparent;
    border: none;
    padding: 0;
    margin: 0;
    text-decoration: underline;
    color: var(--cool-gray);
    font-weight: var(--font-weight-normal);
}

.form__success {
    align-items: center;
    justify-content: center;
    gap: var(--spacing-800);
    height: 100%;
    text-align: center;
}

.form__success .form__description h2 {
    margin-block-end: var(--spacing-500)
}

/* ------------------------------------------- Add states to all inputs ------------------------------------------ */

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

.profile__input:hover {
    border: 1.5px solid var(--purplish-blue);
    padding: calc(var(--spacing-200) - 0.5px) calc(var(--spacing-400) - 0.5px);
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