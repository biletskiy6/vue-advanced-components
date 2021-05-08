<template>
  <div class="">
    <div class="max-w-sm mx-auto mt-8 card">
      <label class="form-label">Tags:</label>
      <tag-input v-model="tags"></tag-input>
    </div>
    <div class="max-w-sm mx-auto mt-8 card">
      <label class="form-label">Renderless TagInput:</label>
      <inline-tag-input v-model="tags"></inline-tag-input>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import AnnouncmentModal from "@/components/announcment-modal";
import MediaCard from "@/components/MediaCard";
import UserSettingsForm from "../components/lesson1-2/UserSettingsForm";
import Pikaday from "../components/Pikaday";
import ConfirmDeleteModal from "../components/ConfirmDeleteModal";
import PrimaryButton from "../components/primary-button";
import ContactList from "../components/ContactList";
import HelloWorld from "../components/HelloWorld.vue";
import TagInput from "../components/TagInput.vue";
import RenderlessTagInput from "../components/RenderlessTagInput.vue";
import InlineTagInput from "../components/InlineTagInput.vue";

export default {
  data() {
    return {
      modalOpen: false,
      accountId: 9,
      date: "1941-06-22",
      tags: ["tag10", "awesome", "hello"]
    };
  },
  components: {
    ContactList,
    PrimaryButton,
    ConfirmDeleteModal,
    Pikaday,
    UserSettingsForm,
    MediaCard,
    AnnouncmentModal,
    Logo,
    HelloWorld,
    TagInput,
    RenderlessTagInput,
    InlineTagInput
  }
};
</script>

<style l, InlineTagInputang="scss">
@mixin triangle($width: 15px, $direction: "down", $color: #333333) {
  @if $direction == "up" {
    width: 0;
    height: 0;
    border-left: $width / 2 solid transparent;
    border-right: $width / 2 solid transparent;
    border-bottom: $width / 2 solid $color;
  } @else if $direction == "left" {
    width: 0;
    height: 0;
    border-top: $width / 2 solid transparent;
    border-bottom: $width / 2 solid transparent;
    border-right: $width / 2 solid $color;
  } @else if $direction == "right" {
    width: 0;
    height: 0;
    border-top: $width / 2 solid transparent;
    border-bottom: $width / 2 solid transparent;
    border-left: $width / 2 solid $color;
  } @else {
    width: 0;
    height: 0;
    border-left: $width / 2 solid transparent;
    border-right: $width / 2 solid transparent;
    border-top: $width / 2 solid $color;
  }
}

.triangle {
  position: absolute;
  transition: transform 0.25s ease;
  /*background-color: #333;*/
  &-down {
    @include triangle(42px, "down");
    top: 5px;
    left: 5px;
    transform: translateY(-30px);
  }
  &-up {
    @include triangle(42px, "up");
    bottom: 5px;
    left: 5px;
    transform: translateY(30px);
  }
  &-right {
    @include triangle(42px, "right");
    left: 5px;
    top: 5px;
    transform: translateX(-30px);
  }
  &-left {
    @include triangle(42px, "left");
    right: 5px;
    top: 5px;
    transform: translateX(30px);
  }
}

.primary-button {
  position: relative;
  width: 56px;
  height: 56px;
  background-color: transparent;
  border: 2px solid red;
  overflow: hidden;
  h6 {
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    width: 80%;
    height: 90%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 101;
    background-color: transparent;
    transition: background-color 0.25s ease 1s;
  }
  &:hover {
    .triangle {
      transition: transform 0.25s ease, background-color 0.25s 0.15s;
      background-color: #333;
      &-down,
      &-up {
        transform: translateY(0px);
      }
      &-left,
      &-right {
        transform: translateX(0px);
      }
    }
  }
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
