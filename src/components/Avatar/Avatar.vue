<template>
  <div :class="containerClasses" :style="avatarStyles">JS</div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";
import { IAvatarStyles } from "@/components/Avatar/types";

@Component
export default class Avatar extends Vue {
  @Prop({ type: String, default: "48" })
  size!: string;

  @Prop({ type: String, default: "#E80459" })
  color!: string;

  get containerClasses(): string {
    return "avatar";
  }

  get containerStyles(): IAvatarStyles {
    return {
      width: `${this.size}px`,
      height: `${this.size}px`,
    };
  }

  get backgroundColor(): IAvatarStyles {
    return {
      backgroundColor: this.color,
    };
  }

  get avatarStyles(): IAvatarStyles {
    return {
      ...this.containerStyles,
      ...this.backgroundColor,
    };
  }
}
</script>

<style scoped lang="css">
@import "styles.css";
</style>
