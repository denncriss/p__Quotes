<template>
  <div class="card-box">
    <h3 class="text-title">
      <icon-base viewBox="0 0 22 20" class="icon-quote">
        <IconQuotes />
      </icon-base>
      {{ quote }}
    </h3>
    <p class="text-author">
      {{ author }}
    </p>
    <div class="card-buttons">
      <button-icon :link="linkDinamic">
        <icon-base viewBox="0 0 28 22" class="icon-twitter">
          <IconTwitter />
        </icon-base>
      </button-icon>
      <Button name="New cite" @click="$emit('onChangeQuote')" />
    </div>
  </div>
</template>

<script>
  import IconQuotes from './icon/IconQuotes.vue';
  import Button from './Button.vue';
  import ButtonIcon from './ButtonIcon.vue';
  import IconBase from './icon/IconBase.vue';
  import IconTwitter from './icon/IconTwitter.vue';
  import { computed } from 'vue';
  export default {
    components: { Button, IconBase, IconTwitter, ButtonIcon, IconQuotes },
    props: ['quote', 'author'],
    emits: ['onChangeQuote'],
    setup(props) {
      const linkDinamic = computed(
        () =>
          `https://twitter.com/intent/tweet?text=${props.quote}-${props.author}`
      );
      return { linkDinamic };
    },
  };
</script>

<style scoped>
  .card-box {
    max-width: 31.25rem;
    background-color: white;
    padding: 1.5rem 1.5rem;
    color: var(--current-color);
    border-radius: 0.9rem;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
      0 4px 6px -2px rgba(0, 0, 0, 0.05);
    overflow: hidden;
  }
  .text-title {
    position: relative;
    font-size: 1.25rem;
    margin-top: 1rem;
    z-index: 10;
  }

  .icon-quote {
    width: 5rem;
    position: absolute;
    top: -2.5rem;
    left: -1.5rem;
    opacity: 0.15;
    z-index: -1;
  }
  .text-author {
    text-transform: uppercase;
    font-size: 0.9rem;
    text-align: end;
    font-weight: 600;
    letter-spacing: 0.05rem;
    margin-top: 0.8rem;
    display: flex;
    justify-content: flex-end;
    font-style: italic;
  }
  .text-author::before {
    content: '';
    width: 2rem;
    height: 0.125rem;
    border-radius: 10px;
    display: inline;
    background-color: var(--current-color);
    color: #000;
    position: relative;
    top: 0.52rem;
    margin-right: 0.5rem;
  }
  .card-buttons {
    margin-top: 1.5rem;
    display: flex;
    justify-content: space-between;
    z-index: 10;
  }
  @media (min-width: 768px) {
    .text-title {
      font-size: 1.6rem;
    }
    .card-box{
      padding: 1.7rem 2rem;
    }
    .icon-quote {
    left: -2rem;
  }
  }
</style>
