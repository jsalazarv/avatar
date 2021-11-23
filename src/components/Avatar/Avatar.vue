<template>
  <div :class="avatarClasses" :style="avatarStyles">
    <slot></slot>
  </div>
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

  @Prop({ type: String, default: "48" })
  size!: string;

  @Prop({ type: Boolean, default: false })
  tile!: boolean;

  get avatarClasses() {
    return ["avatar", { rounded: this.rounded, tile: this.tile }];
  }

  get avatarBackgroundColor(): IAvatarStyles {
    return {
      backgroundColor: this.color,
    };
  }

  get avatarSize(): IAvatarStyles {
    return {
      width: `${this.size}px`,
      height: `${this.size}px`,
    };
  }

  get avatarStyles(): IAvatarStyles {
    return {
      ...this.avatarSize,
      ...this.avatarBackgroundColor,
    };
  }
}
</script>

<style scoped lang="scss">
@import "styles";
</style>
