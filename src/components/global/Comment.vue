<script lang="ts" setup>
import GlobalFontIcon from "@/components/global/FontIcon.vue";
import GlobalComment from "@/components/global/Comment.vue";

import { computed, ref } from "vue";
// props
interface Props {
  comment: {
    id: number;
    fullName: string;
    text: string;
    likes: number;
    img: string;
    date: string;
    comments?: any;
  };
  depth: number;
}
const props = defineProps<Props>();
// emits

// variables
const showChildren = ref(false);

// computed properties
const indent = computed((): any => {
  return { paddingLeft: `${props.depth * 20}px` };
});

// watches

// methods
const toggleChildren = (): void => {
  showChildren.value = !showChildren.value;
};
// hooks
</script>

<template>
  <div class="overflow-x-auto ">
    <div :style="indent" class="flex flex-wrap justify-between">
      <div class="w-full">
        <div
          class="w-full flex items-center lg:justify-between lg:h-10 h-6 whitespace-nowrap"
        >
          <div
            class="lg:w-10 lg:h-10 lg:min-w-10 lg:min-h-10 w-6 h-6 min-w-6 min-h-6"
          >
            <img
              :src="props.comment.img"
              class="w-full h-full rounded-full border border-transparent"
              alt="profile-img"
            />
          </div>

          <div
            class="lg:block flex items-center justify-between lg:w-fit w-full"
          >
            <div class="lg:mx-4 mx-2">
              <h4 class="font-bold text-black">
                {{ props.comment.fullName }}
              </h4>
            </div>

            <div class="lg:hidden block">
              <p class="">
                {{ props.comment.date }}
              </p>
            </div>
          </div>

          <div class="w-fit ml-auto lg:block hidden">
            <div class="flex items-start justify-end">
              <div class="flex items-center cursor-pointer">
                <div class="lg:w-4 lg:h-4 w-3 h-3">
                  <GlobalFontIcon
                    :icon="{ prefix: 'fa-solid', value: 'fa-thumbs-up' }"
                  />
                </div>
                <div class="mx-2">
                  <span> Like </span>
                </div>
              </div>
              <div class="flex items-center cursor-pointer lg:ml-4 ml-2">
                <div class="lg:w-4 lg:h-4 w-3 h-3">
                  <GlobalFontIcon
                    :icon="{
                      prefix: 'fa-solid',
                      value: 'fa-comment',
                    }"
                  />
                </div>
                <div class="mx-2">
                  <span> Reply </span>
                </div>
              </div>

              <div
                class="flex items-center lg:ml-4 ml-2 cursor-pointer"
                v-if="
                  props.comment.comments && props.comment.comments.length >= 1
                "
                @click="toggleChildren"
              >
                <div class="lg:w-4 lg:h-4 w-3 h-3 mx-1">
                  <GlobalFontIcon
                    :icon="{
                      prefix: 'fa-solid',
                      value: 'fa-chevron-down',
                    }"
                  />
                </div>

                <div class="flex">
                  <span v-if="!showChildren"> Show </span>
                  <span v-else> Hide </span>
                  <span class="mx-1 block">Comments</span>
                </div>
              </div>

              <div class="lg:ml-4 ml-2">
                <p class="">
                  {{ props.comment.date }}
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="lg:my-2 my-1 max-h-56 overflow-auto lg:pl-4 pl-2">
          <p class="text-justify text-gray-400 lg:leading-8 leading-6">
            {{ props.comment.text }}
          </p>
        </div>
        <div class="w-fit ml-auto lg:hidden contents whitespace-nowrap">
          <div class="flex items-start justify-between">
            <div class="flex items-center">
              <div class="flex items-center cursor-pointer">
                <div class="lg:w-4 lg:h-4 w-3 h-3">
                  <GlobalFontIcon
                    :icon="{ prefix: 'fa-solid', value: 'fa-thumbs-up' }"
                  />
                </div>
                <div class="mx-2">
                  <span> Like </span>
                </div>
              </div>
              <div class="flex items-center cursor-pointer lg:ml-4 ml-2">
                <div class="lg:w-4 lg:h-4 w-3 h-3">
                  <GlobalFontIcon
                    :icon="{
                      prefix: 'fa-solid',
                      value: 'fa-comment',
                    }"
                  />
                </div>
                <div class="mx-2">
                  <span> Reply </span>
                </div>
              </div>
            </div>
            <div class="lg:ml-4 ml-2 flex items-center">
              <div
                class="flex items-center lg:mr-4 mr-2 cursor-pointer"
                v-if="
                  props.comment.comments && props.comment.comments.length >= 1
                "
                @click="toggleChildren"
              >
                <div class="lg:w-4 lg:h-4 w-3 h-3 mx-1">
                  <GlobalFontIcon
                    :icon="{
                      prefix: 'fa-solid',
                      value: 'fa-chevron-down',
                    }"
                  />
                </div>
                <div class="flex">
                  <span v-if="!showChildren"> Show </span>
                  <span v-else>Hide </span>
                  <span class="mx-1 block">Comments</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <GlobalComment
      v-if="showChildren"
      v-for="(comment, index) in props.comment.comments"
      :key="index"
      :comment="comment"
      :depth="props.depth + 1"
    >
    </GlobalComment>
  </div>
</template>
