<template>
  <form class="search">
    <label class="search__wrapper" aria-label="Поиск">
      <input
        class="search__input"
        type="search"
        placeholder="Хочу найти..."
        @input="onInput"
        v-model="search"
      />
      <button class="search__btn" aria-label="Искать" type="submit">
        <IconSearch class="search__icon" />
      </button>
    </label>
    <transition name="fade" mode="in-out">
      <ul class="search__list" v-show="isOpened">
        <li
          v-for="(item, i) in results"
          @click="select(i)"
          class="search__item"
          :key="i"
        >
          {{ item }}
        </li>
      </ul>
    </transition>
  </form>
</template>

<script>
import IconSearch from "../components/Icons/IconSearch.vue";
export default {
  data() {
    return {
      isOpened: false,
      search: "",
      results: []
    };
  },
  components: {
    IconSearch
  },
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    onInput(e) {
      const condition = new RegExp(this.search, "i");
      this.results = this.search
        ? this.items.filter(item => item.match(condition))
        : [];
      this.isOpened =
        e.target.value.length && this.results.length ? true : false;
    },
    select(index) {
      let selectedOption = this.results[index];
      this.search = selectedOption;
      this.isOpened = false;
    }
  }
};
</script>

<style lang="scss">
.search {
  position: relative;
  font-weight: 400;

  &__wrapper {
    display: block;
    position: relative;
    margin: 0 auto;
    overflow: hidden;
    border: none;
  }

  &__input {
    font-size: $font-size;
    line-height: $line-height;
    color: $gray;
    display: block;
    width: 100%;
    padding: 7px 40px 7px 14px;
    overflow: hidden;
    text-overflow: ellipsis;
    word-break: break-all;
    background: $white;
    border: 1px solid $border;
    border-radius: 4px;
    outline: 0;
    -webkit-tap-highlight-color: #708598;

    &:focus,
    &:active {
      border-color: #708598;
    }
  }

  &__btn {
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 0;
    right: 10px;
    bottom: 0;
    width: 20px;
    padding: 0;
    cursor: pointer;
    background-color: transparent;
    border: none;
    outline: none;
  }

  &__list {
    position: absolute;
    background-color: $white;
    list-style-type: none;
    width: 100%;
    border: 1px solid $border;
    border-radius: 4px;
    color: $gray;
    padding: 7px 14px;
    margin: 0;
  }

  &__item {
    cursor: pointer;
    padding: 3px;
    &:hover {
      background: $yellow;
    }
  }
}
</style>
