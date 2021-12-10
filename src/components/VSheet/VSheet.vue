<template>
  <div :class="sheetClasses" :style="sheetStyles">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
import { ISheetStyles, ISheetClasses } from "./types";

@Component
export default class VSheet extends Vue {
  @Prop({ type: String, default: "#E80459" })
  color?: string;
  @Prop({ type: Boolean, default: false })
  outlined?: boolean;
  @Prop({ type: Boolean, default: false })
  rounded?: boolean;
  @Prop({ type: Boolean, default: false })
  shaped?: boolean;
  @Prop({ type: String, default: "100" })
  width?: string;
  @Prop({ type: String, default: "100" })
  height?: string;

  get sheetClasses() {
    return [
      "v-sheet",
      { outlined: this.outlined, rounded: this.rounded, shaped: this.shaped },
    ];
  }

  get sheetBackgroundColor(): ISheetStyles {
    return {
      backgroundColor: this.color,
    };
  }

  get sheetWidth(): ISheetStyles {
    return {
      width: `${this.width}px`,
    };
  }

  get sheetHeight(): ISheetStyles {
    return {
      height: `${this.height}px`,
    };
  }

  get sheetStyles(): ISheetStyles {
    return {
      ...this.sheetBackgroundColor,
      ...this.sheetWidth,
      ...this.sheetHeight,
    };
  }
}
</script>

<style scoped lang="scss">
@import "styles";
</style>
