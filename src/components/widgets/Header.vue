<script lang="ts" setup>
import ArrowIcon from "@/components/ui/ArrowIcon.vue";
</script>

<template>
  <header class="header">
    <h1 class="header__title">Карточки</h1>
    <div class="header-utilities">
      <div class="header-project">
        <p class="header-project__title">Проект:</p>
        <div  class="project__select-small" name="language">
          <div class="option-label">
            <div class="option__title">Не выбрано</div>
            <ArrowIcon />
          </div>
          <div v-if="0" class="option-group">
            <div class="project__option" disabled>Выбрать</div>
            <div class="project__option" value="HTML">HTML</div>
            <div class="project__option" value="JavaScript">JavaScript</div>
            <div class="project__option" value="PHP">PHP</div>
          </div>
        </div>
      </div>
      <button class="button-main-blue">Добавить карточку</button>
      <button class="button-main-blue">Сохранить изменения</button>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
  &__title {
    font-size: 32px;
    font-weight: 700;
    color: var(--main-text-color);
  }
  &-utilities {
    display: flex;
    align-items: center;
    gap: 8px;
    .header-project {
      display: flex;
      align-items: center;
      gap: 4px;
      &__title {
        color: var(--light-text-color);
        font-size: 12px;
        font-weight: 400;
      }
      .project__select-small {
        position: relative;
        border-radius: 4px;
        background: var(--card-color);
        .option-label {
          display: flex;
          align-items: center;
          gap: 8px;
          padding: 8px;
          .option__title {
            font-size: 13px;
            font-weight: 400;
            color: var(--light-blue-text-color);
          }
        }
        .option-group {
          width: 100%;
          position: absolute;
          top: 40px;
          display: flex;
          flex-direction: column;
          background-color: var(--main-white);
          border-radius: 4px;
          overflow: hidden;
          .project__option {
            padding: 8px;
            font-size: 13px;
            font-weight: 400;
            color: var(--light-blue-text-color);
            cursor: pointer;
            transition: 0.15s;
            &:hover {
              background-color: var(--card-color);
            }
          }
        }
      }
    }
  }
}
</style>
