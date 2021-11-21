<template>
  <div :class="containerClasses" :style="avatarStyles">JS</div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";
import { IAvatarStyles } from "@/components/Avatar/types";

@Component
export default class Avatar extends Vue {
  @Prop({ type: String, default: "#E80459" })
  color!: string;

  @Prop({ type: Boolean, default: false })
  rounded!: boolean;

  @Prop({ type: String, default: "48px" })
  size!: string;

  get containerClasses() {
    return ["avatar", { rounded: this.rounded }];
  }

  get backgroundColor(): IAvatarStyles {
    return {
      backgroundColor: this.color,
    };
  }

  get containerStyles(): IAvatarStyles {
    return {
      width: `${this.size}px`,
      height: `${this.size}px`,
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
