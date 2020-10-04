<template>
  <div class="topbar">
    <div class="topbar__container container">
      <div class="topbar__location">
        <IconLocation />
        <span>Волгоградская область</span>
      </div>
      <div class="topbar__menu">
        <ul class="topbar__list">
          <li class="topbar__item">Тендеры</li>
          <li class="topbar__item">База подрядчиков</li>
          <li class="topbar__item topbar__item--drop">Другие сервисы</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import IconLocation from "../components/Icons/IconLocation.vue";
export default {
  components: {
    IconLocation
  }
};
</script>

<style lang="scss">
.topbar {
  background: $background;
  font-size: $font-size--small;
  line-height: $line-height--small;
  color: $gray;
  border-bottom: 1px solid $border;
  padding: 6px 0;

  &__container {
    @media (max-width: $screen-md) {
      flex-direction: column;
    }
  }

  &__location {
    display: flex;
    align-items: center;
    cursor: pointer;

    span {
      margin-left: 8px;
    }
  }

  &__list {
    padding: 0;
    margin: 0;
    list-style-type: none;
    display: flex;
  }

  &__item {
    margin: 0 12px;
    cursor: pointer;
    &--drop {
      &:after {
        content: url("../assets/chevron.svg");
        width: 10px;
        height: 6px;
        margin-left: 6px;
      }
    }

    &:first-of-type {
      margin-left: 0px;
    }

    &:last-of-type {
      margin-right: 0px;
    }
  }
}
</style>
