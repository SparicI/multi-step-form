<template>
    <form action="">

        <section id="step-1">
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
                        name="phone"
                        id="phone"
                        pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
                        class="form__input"
                    >
                </div>

            </div>


            <div class="form__controls">


            </div>

        </section>

    </form>
</template>

<script
    setup
    lang="ts"
>

</script>

<style scoped></style>