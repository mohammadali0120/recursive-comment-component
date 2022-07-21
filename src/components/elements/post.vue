<script setup lang="ts">
import GlobalComment from "@/components/global/Comment.vue";
import { ref } from "vue";
import ProfilePic from "@/assets/images/person.png";

const comments = ref([
  {
    id: 1,
    fullName: "Ali",
    text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
    likes: 0,
    img: ProfilePic,
    date: "2022-05-10",
    comments: [
      {
        id: 1,
        fullName: "Mohammad",
        text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
        likes: 0,
        img: ProfilePic,
        date: "2022-05-11",
        comments: [
          {
            id: 1,
            fullName: "Thomas",
            text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
            likes: 0,
            img: ProfilePic,
            date: "2022-05-11",
          },
          {
            id: 2,
            fullName: "Javad",
            text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
            likes: 0,
            img: ProfilePic,
            date: "2022-05-12",
            comments: [
              {
                id: 1,
                fullName: "Eric",
                text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
                likes: 0,
                img: ProfilePic,
                date: "2022-05-12",
                comments: [
                  {
                    id: 1,
                    fullName: "John",
                    text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
                    likes: 0,
                    img: ProfilePic,
                    date: "2022-05-11",
                  },
                  {
                    id: 2,
                    fullName: "Omid",
                    text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
                    likes: 0,
                    img: ProfilePic,
                    date: "2022-05-11",
                    comments: [
                      {
                        id: 1,
                        fullName: "Alireza",
                        text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
                        likes: 0,
                        img: ProfilePic,
                        date: "2022-05-11",
                      },
                    ],
                  },
                ],
              },
            ],
          },
        ],
      },
      {
        id: 2,
        fullName: "Reza",
        text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
        likes: 0,
        img: ProfilePic,
        date: "2022-05-12",
      },
    ],
  },
  {
    id: 2,
    fullName: "Tom",
    text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
    likes: 0,
    img: ProfilePic,
    date: "2022-05-10",
    comments: [
      {
        id: 1,
        fullName: "Farbod",
        text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. A dicta nemo aperiam accusamus quisquam necessitatibus, neque quaerat optio, culpa eos magni libero obcaecati tempora dolor ex earum repudiandae animi et!",
        likes: 0,
        img: ProfilePic,
        date: "2022-05-11",
      },
    ],
  },
]);
</script>

<template>
  <div>
    <div class="w-full max-h-lg">
      <img
        src="../../assets/images/pic-1.jpg"
        class="w-full h-full rounded-md"
        alt="pic-1"
      />
    </div>

    <div class="my-4" v-for="(comment, index) in comments" :key="index">
      <GlobalComment :comment="comment" :depth="0" />
    </div>
  </div>
</template>
