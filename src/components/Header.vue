<template>
  <div class="header">
    <div class="container header__container">
      <div class="header__logo"></div>
      <div class="header__catalog">
        <IconBurger />
        <span>Каталог</span>
      </div>
      <Search class="header__search" :items="items" />
      <div class="header__list">
        <IconList />
        <span>Список</span>
      </div>
      <div class="header__profile"><span>A</span></div>
    </div>
  </div>
</template>

<script>
import Search from "../components/Search.vue";
import IconBurger from "../components/Icons/IconBurger.vue";
import IconList from "../components/Icons/IconList.vue";
export default {
  data() {
    return {
      items: [
        "Кровля и водосток",
        "Теплоизоляция",
        "Гидроизоляция",
        "Окна и двери",
        "Строительная химия",
        "Грунтовка",
        "Напольные покрытия",
        "Отделочные материалы",
        "Декоративные покрытия",
        "Подвесные потолки",
        "Плитка",
        "Сайдинг и фасадные панели",
        "Оргстекло",
        "Дерево и пиломатериалы",
        "Кирпич",
        "Строительные сетки и стеклохолст",
        "Сыпучие строительные материалы",
        "Бетон и железобетонные изделия",
        "Металлопрокат",
        "Тротуарная плитка",
        "Заборы и ограждения",
        "Формы для производства",
        "Строительный крепеж",
        "Мешки строительные"
      ]
    };
  },
  components: {
    Search,
    IconBurger,
    IconList
  }
};
</script>

<style lang="scss">
.header {
  background: $white;
  font-size: $font-size;
  line-height: $line-height;
  color: $black;
  font-weight: 600;
  border-bottom: 1px solid $border;

  &__container {
    align-items: stretch;

    & > * {
      margin: 0 12px;

      @media (max-width: $screen-md) {
        margin: 0 6px;
      }
    }

    @media (max-width: $screen-md) {
      flex-wrap: wrap;
      justify-content: center !important;
    }
  }

  &__logo {
    background: url("../assets/logo.svg");
    width: 221px;
    height: 48px;
    margin: 14px 12px 14px 0;
    flex-shrink: 0;

    @media (max-width: $screen-md) {
      background-repeat: no-repeat;
      background-position-x: center;
      width: 100%;
      order: 1;
    }
  }

  &__search {
    flex: 1 1 auto;
    @media (max-width: $screen-md) {
      width: 100%;
      order: 5;
      padding: 14px 0;
    }
  }

  &__catalog,
  &__list {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;

    span {
      margin-left: 8px;
    }
  }

  &__catalog {
    background-color: $yellow;
    @media (max-width: $screen-md) {
      order: 2;
    }
  }

  &__list {
    background-color: $background;
    border: 1px solid $border;
    padding: 7px 16px;
    @media (max-width: $screen-md) {
      order: 3;
    }
  }

  &__profile {
    background: purple;
    margin: 0 0 0 12px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    flex-shrink: 0;
    cursor: pointer;
    span {
      color: $white;
      margin: 0 auto;
    }
    @media (max-width: $screen-md) {
      order: 4;
      margin-right: 12px;
    }
  }
}
</style>
