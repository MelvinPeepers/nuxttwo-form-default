<!-- <template>
  <Form/>
</template>

<script>
import Form from '~/components/Form.vue';

export default {
  name: 'IndexPage'
}
</script> -->

<template>
  <div>
    <h1>Netlify Form Example</h1>
    <NetlifyForm />
  </div>
</template>

<script>
import Form from '~/components/Form.vue';

export default {
  components: {
    Form,
  },
};
</script>

