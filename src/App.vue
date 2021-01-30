<template>
  <div class="content" :style="{ '--current-color': color }">
    <main class="principal" >
      <QuoteBox
        :quote="quote.quote"
        :author="quote.author"
        @onChangeQuote="handleNewQuote"
      />
    </main>
  </div>
</template>

<script>
  import data from '@/api/quotes.json';
  import { getRandomNumber } from './helpers/getRandomNumber';
  import { getRandomColor } from './helpers/getRandomColor';
  import { ref } from 'vue';
  import QuoteBox from './components/QuoteBox.vue';
  export default {
    name: 'App',
    components: { QuoteBox },
    setup() {
      const QUOTES = data.quotes;
      const QUOTES_INDEX = QUOTES.length;
      const QUOTES_RANDOM = getRandomNumber(QUOTES_INDEX);

      const quote = ref(QUOTES[QUOTES_RANDOM]);
      const color = ref(getRandomColor());

      const handleNewQuote = () => {
        const NEW_QUOTE_RANDOM = getRandomNumber(QUOTES_INDEX);
        quote.value = QUOTES[NEW_QUOTE_RANDOM];
        color.value = getRandomColor();
      };

      return { quote, color, handleNewQuote };
    },
  };
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

  body {
    font-family: 'Poppins', sans-serif;
  }
  .content {
    min-height: 100vh;
    background-color: var(--current-color);
  }
  .principal {
    height: 100vh;
    background-color: var(--current-color);

    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }
  .btn,
  .btn-icon {
    padding: 0.6rem 3rem;
    border-radius: 0.3rem;
    letter-spacing: 0.05rem;
    text-transform: uppercase;
    box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  }
  .btn-icon {
    padding: 0.6rem 0.7rem;
    background-color: var(--current-color);
    color: white;
    display: flex;
    align-items: center;
  }
  .icon-twitter {
    width: 1.4rem;
  }
  .btn:focus,
  .btn-icon:focus {
    outline: none;
  }
</style>
