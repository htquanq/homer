<template>
  <Generic :item="item">
    <template #indicator>
      <div class="popup" v-show="popupVisible">
        <div class="popup-content">
          <span class="icon close fas fa-close" @click="popupVisible = false" />
          <p class="header">{{ item.header }}</p>
          <p class="content">{{ item.content }}</p>
        </div>
      </div>
    </template>
  </Generic>
</template>

<script>
import service from "@/mixins/service.js";
import Generic from "./Generic.vue";

export default {
  name: "Info",
  mixins: [service],
  props: {
    item: Object,
  },
  components: {
    Generic,
  },
  data: () => ({
    popupVisible: false
  }),
};
</script>

<style scoped lang="scss">
.popup {
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.358);
  width: 100%;
  height: 100%;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup-content {
  background-color: #fefefe;
  margin: 24px;
  max-width: 500px;
  max-height: 90vh;
  min-height: 200px;
  width: calc(100% - 48px); 
  overflow-y: scroll;
  height: fit-content;
  padding: 50px 20px;
  position: fixed;
  border-radius: 0.25rem;
}

.icon {
  cursor: pointer;
  color: var(--link);
}

.icon:hover {
  color: var(--link-hover);
}

/* Visible even with scrolling */
.icon.close {
  color: var(--text);
  position: absolute;
  right: 15px;
  top: 15px;
}

.fa-info-circle {
  text-align: right;
  display: inline-block;
  width: 100%;
  padding: 5px;
}

.header {
  font-weight: 900;
}
</style>