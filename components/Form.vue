<template>
    <div>
        <form name="contact" method="post" data-netlify="true" @submit.prevent="handleSubmit">
        <input type="hidden" name="form-name" value="contact" />
        <label>
            Name:
        <input type="text" name="name" v-model="formData.name" required />
        </label>
        <label>
            Email:
        <input type="email" name="email" v-model="formData.email" required />
        </label>
        <label>
            Message:
            <textarea name="message" v-model="formData.message" required></textarea>
        </label>
        <button type="submit">Submit</button>
        </form>
    </div>
</template>

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
