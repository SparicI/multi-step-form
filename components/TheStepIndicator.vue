<template>
    <ol class="step__list">
        <li
            aria-current="step"
            class="step__list-item active"
        >
            <p class="step__description">
                <span class="step__counter">step 1</span>
                <span>your info</span>
            </p>

        </li>
        <li class="step__list-item">
            <p class="step__description">
                <span class="step__counter">step 2</span>
                <span>select plan</span>
            </p>
        </li>
        <li class="step__list-item">
            <p class="step__description">
                <span class="step__counter">step 3</span>
                <span>add-ons</span>
            </p>
        </li>
        <li class="step__list-item">
            <p class="step__description">
                <span class="step__counter">step 4</span>
                <span>summary</span>
            </p>
        </li>
    </ol>
</template>

<script
    setup
    lang="ts"
>

</script>

<style scoped>
.step__list {
    display: flex;
    gap: var(--spacing-400);
    justify-content: center;
    counter-reset: step-counter;
    padding-block-start: var(--spacing-800);
    height: 172px;
    list-style: none;
    color: var(--white);
    font-weight: var(--font-weight-bolder);
    text-transform: uppercase;

    background-image: url(/images/bg-sidebar-mobile.svg);
    background-repeat: no-repeat;
    background-size: cover;
}

.step__list-item::before {
    display: grid;
    place-items: center;
    counter-increment: step-counter;
    content: counter(step-counter);
    background-color: transparent;
    border: 2px solid var(--white);
    border-radius: 50%;
    height: 40px;
    aspect-ratio: 1;
}

.active.step__list-item::before {
    background-color: var(--pastel-blue);
    border-color: var(--pastel-blue);
    color: var(--marine-blue);
}


.step__description {
    display: none;
}

@media screen and (min-width: 1024px) {

    .step__list {
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        height: 568px;
        width: 300px;
        padding: var(--spacing-1000);

        background-image: url(/images/bg-sidebar-desktop.svg);
        background-size: auto;
    }

    .step__list-item {
        display: flex;
        align-items: center;
        gap: var(--spacing-400);
    }

    .step__description {
        display: flex;
        flex-direction: column;
    }

    .step__counter {
        font-weight: var(--font-weight-normal);
        color: var(--cool-gray);
    }
}
</style>