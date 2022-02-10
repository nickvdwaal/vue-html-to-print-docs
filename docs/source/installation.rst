Installation
=====


To use vue-html-to-print, first install it using npm:

.. code-block:: console

   npm install vue-html-to-print

If the installation is successful we can import it in our ``main.js``

.. code-block:: javascript

  import { createApp } from 'vue'
  import HtmlToPrint from "vue-html-to-print";

  const app = createApp(App)

  const options = {
      name: '_blank',
      specs: [
        'fullscreen=yes',
        'titlebar=yes',
        'scrollbars=yes'
      ],
      styles: [
          '/styles.css',
          'https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css'
      ]
  }
  
  app.use(HtmlToPrint, options).mount('#app')
  
Inside any of our components

.. code-block:: javascript

  <template>
    <div>
      <h1>This is a default page</h1>
      <!-- The div with the desired contents -->
      <div id="print">
        <h1>I'd like to print this</h1>
      </div>
      <button @click="print">Print</button>
    </div>
  <template>

  <script>
    export default {
      methods: {
        async print () {
          // Pass the element id here
          await this.$htmlToPrint('print');
        }
      }
    }
  </script>
  
Optionally you can apply different options with each call by defining other options

.. code-block:: javascript

  this.$htmlToPrint('print', { /* local options */ });
