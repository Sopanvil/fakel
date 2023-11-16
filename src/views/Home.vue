<script lang="ts" se>
import { ref } from "vue";
import FilterUp from "@/components/ui/FilterUpIcon.vue";
import FilterDown from "@/components/ui/FilterDownIcon.vue";

import NoteEdit from "@/components/ui/NoteEdit.vue";
import Garbage from "@/components/ui/Garbage.vue";
import Draggable from "@/components/ui/Draggable.vue";
import LabelEllipse from "@/components/ui/LabelEllipse.vue";

export default {
  components: {
    FilterUp,
    FilterDown,
    NoteEdit,
    Garbage,
    Draggable,
    LabelEllipse,
  },
  props: {
    stages: {
      type: Object,
      required: true,
    },
    cards: {
      type: Object,
      required: true,
    },
    projects: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    let x = "";
    const cardProject = (projectName: any) => {
      x = ""
      props.projects.forEach((item: any) => {
        if (item.code == projectName) {
          x = item.name;
        }
      });
      return x
    };
    return {
      cardProject,
    };
  },
};
</script>

<template>
  <section class="todos">
    <div class="todos__container">
      <div v-for="stage in stages" :key="stage.id" class="todos-stage">
        <div class="stage-label">
          <div class="stage-text">
            <LabelEllipse />
            <p class="label__title">{{ stage.name }}</p>
          </div>
          <div class="stage-filters">
            <FilterDown />
            <FilterUp />
          </div>
        </div>
        <div class="stage-cards">
          <div v-for="card in cards.filter((item: any) => item.stage === stage.code)" :key="card.id" class="stage-card">
            <div class="card-info">
              <div class="info-utilities">
                <div class="utilities-main">
                  <h1 class="card__name">{{ card.title }}</h1>
                  <div class="card-icons">
                    <NoteEdit />
                    <Garbage />
                  </div>
                </div>
                <Draggable />
              </div>
              <p class="card__score">
                Балл: <span class="card__score-number">{{ card.score }}</span>
              </p>
            </div>
            <p v-if="!card.project == false" class="card-project">{{ cardProject(card.project) }}</p>
          </div>
        </div>
        <button class="add-card__button">Добавить</button>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.todos {
  &__container {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    .todos-stage {
      width: 300px;
      padding: 12px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      border-radius: 4px;
      background: var(--card-color);
      .stage-label {
        display: flex;
        align-items: center;
        justify-content: space-between;
        .stage-text {
          display: flex;
          align-items: center;
          gap: 8px;
          .label__title {
            color: var(--main-text-color);
            font-size: 15px;
            font-weight: 600;
          }
        }
      }
      .stage-cards {
        display: flex;
        flex-direction: column;
        gap: 8px;
        .stage-card {
          min-height: 120px;
          display: flex;
          flex-direction: column;
          align-items: flex-start;
          justify-content: space-between;
          padding: 12px;
          border-radius: 4px;
          background: var(--main-white);
          .card-info {
            width: 100%;
            .info-utilities {
              width: 100%;
              display: flex;
              align-items: center;
              justify-content: space-between;
              margin-bottom: 8px;
              .utilities-main {
                display: flex;
                align-items: center;
                justify-content: space-between;
                gap: 8px;
                .card__name {
                  font-size: 14px;
                  font-weight: 600;
                  color: var(--main-text-color);
                }
                .card-icons {
                  display: flex;
                  align-items: center;
                  gap: 4px;
                }
              }
            }
            .card__score {
              font-size: 12px;
              font-weight: 400;
              color: var(--light-text-color);
              &-number {
                color: var(--main-text-color);
                font-weight: 600;
              }
            }
          }
          .card-project {
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 400;
            background: #e5e9ef;
            border: 1px solid #d2dae4;
            color: var(--light-blue-text-color);
          }
        }
      }
      .add-card__button {
        width: 100%;
        display: flex;
        justify-content: center;
        padding: 8px;
        border-radius: 4px;
        background: none;
        font-size: 13px;
        font-weight: 400;
        color: var(--light-blue-text-color);
        transition: 0.15s;
        &:hover {
          background: var(--main-white);
        }
      }
    }
  }
}
</style>
