<template>
  <div class="vue-time-picker">
    <div class="vue-time-picker-input">
      <input
      type="text"
      placeholder="请选择"
      :value="padString(hours) + ':' + padString(minutes) + ':' + padString(seconds)">
    </div>
    <div class="vue-time-picker-dropDown-container">
      <div class="vue-time-picker-dropDown">
        <ul class="vue-time-picker-dropDown-list">
          <li
            @click="timePickerItemHoursEvent(item - 1)"
            v-for="item of 60"
            :key="'hh' + (item - 1)"
            :class="item - 1 === hours ? 'vue-time-picker-item-active' : ''"
            class="vue-time-picker-dropDown-list-item">
            {{ padString(item - 1) }}
          </li>
        </ul>
        <ul class="vue-time-picker-dropDown-list">
          <li
            @click="timePickerItemMinutesEvent(item - 1)"
            v-for="item of 60"
            :key="'mm' + (item - 1)"
            :class="item - 1 === minutes ? 'vue-time-picker-item-active' : ''"
            class="vue-time-picker-dropDown-list-item">
            {{ padString(item - 1) }}
          </li>
        </ul>
        <ul class="vue-time-picker-dropDown-list">
          <li
            @click="timePickerItemSecondsEvent(item - 1)"
            v-for="item of 60"
            :key="'ss' + (item - 1)"
            :class="item - 1 === seconds ? 'vue-time-picker-item-active' : ''"
            class="vue-time-picker-dropDown-list-item">
            {{ padString(item - 1) }}
          </li>
        </ul>
      </div>
      <div class="vue-time-picker-dropDown-menu">
        <span class="vue-time-picker-dropDown-menu-button vue-time-picker-dropDown-menu-button-cancel">取消</span>
        <span class="vue-time-picker-dropDown-menu-button vue-time-picker-dropDown-menu-button-confim">确定</span>
      </div>
      <!-- <div class="vue-time-picker-dropDown-popper-arrow"></div> -->
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class VueTimePicker extends Vue {
  private format: string = 'timestamp';

  private step: string = '00:01';

  private valueFormat: string = 'timestamp';

  private readonly: boolean = false;

  private value: number = 0;

  private hours: number = 0;

  private minutes: number = 0;

  private seconds: number = 0;

  public padString(val: any): string {
    return String(val).padStart(2, '0');
  }

  public timePickerItemHoursEvent(value: number): void {
    this.hours = value;
  }

  public timePickerItemMinutesEvent(value: number): void {
    this.minutes = value;
  }

  public timePickerItemSecondsEvent(value: number): void {
    this.seconds = value;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .vue-time-picker {
    width: 150px;
    margin: 0 auto;
    .vue-time-picker-input {
      input {
        width: 100%;
        box-sizing: border-box;
        border: 1px solid #999;
        border-radius: 5px;
        padding: 10px;
      }
    }
    .vue-time-picker-dropDown-container {
      overflow: hidden;
      margin-top: 10px;
      border-radius: 5px;
      box-shadow: 0 0 5px 0 #999;
      position: relative;
      .vue-time-picker-dropDown {
        ul, li {
          list-style: none;
          margin: 0;
          padding: 0;
        }
        display: flex;
        .vue-time-picker-dropDown-list {
          flex: 1;
          height: 300px;
          overflow-y: scroll;
          .vue-time-picker-dropDown-list-item {
            padding: 5px;
            box-sizing: border-box;
            font-size: 14px;
            cursor: pointer;
            &:hover {
              background: #f3f3f3;
            }
            &.vue-time-picker-item-active {
              background: #ff5c44;
              color: #fff;
            }
          }
        }
      }
      .vue-time-picker-dropDown-menu {
        display: flex;
        justify-content: flex-end;
        border-top: 1px solid #b7b7b7;
        .vue-time-picker-dropDown-menu-button {
          width: 50px;
          height: 30px;
          font-size: 12px;
          line-height: 30px;
          &.vue-time-picker-dropDown-menu-button-confim {
            color: #ff5c44;
            &:hover {
              color: #d83c25;
            }
          }
        }
      }
      .vue-time-picker-dropDown-popper-arrow {
        &::after {
          width: 0;
          height: 0;
          border: 0;
          border-bottom: 6px solid red;
          border-left: 6px solid red;
          border-right: 6px solid red;
          border-top: 6px solid transparent;
          content: " ";
          position: absolute;
          top: 0;
          left: 35px;
        }
      }
    }

  }
</style>
