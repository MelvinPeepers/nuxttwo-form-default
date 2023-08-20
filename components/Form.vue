<template>
<div class="container">

<h1>Netlify Forms on Nuxt 2</h1>

<h2>Contact Form</h2>

<p>Have any questions or suggestions?</p>

<form 
    name="contact" 
    method="POST" 
    data-netlify="true"
    @submit.prevent="handleSubmit"
>

    <input type="hidden" name="form-name" value="contact" />

    <div class="row">

        <div class="column">
            <label>Name</label>
            <input type="text" name="name" placeholder="Full name here">
        </div>

        <div class="column">
            <label for="email">Email</label>
            <input type="email" name="email" placeholder="Email">
        </div>

    </div>

    <div class="row">

        <div class="column">
            <label>Title</label>
            <input type="text" name="title" placeholder="Title of message">
        </div>

    </div>

    <div class="row">
        <div class="column">
            <label>Message</label>
            <textarea name="message" placeholder="Leave your message here"></textarea>
        </div>
    </div>

    <div class="vertical-center">
        <button type="submit">Submit</button>
    </div>

</form>

</div>
</template>


<style>
@import url("~/assets/styling.css");
</style>

<script>
    export default {
        data() {
            return {
                formData: {
                    name: '',
                    email: '',
                    message: '',
            },
        };
    },
        methods: {
            handleSubmit() {
                const formData = new FormData();
                for (const key in this.formData) { 
                    formData.append(key, this.formData[key]);
                }

                fetch('/', {
                    method: 'POST',
                    body: formData,
                })
                .then(() => {
                    alert('Form submitted successfully!');
                    // Handle success actions or redirects here
                })
                .catch((error) => {
                    console.error('Error submitting the form:', error);
                    // Handle error cases here
                });
            },
        },
    };
</script>
