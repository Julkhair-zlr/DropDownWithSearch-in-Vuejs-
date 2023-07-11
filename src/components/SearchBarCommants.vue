<template>
  <section class="dropdown-wrapper">
    <div class="seleted-item" @click="isVisible = !isVisible">
      <span v-if="selectedItem">{{ selectedItem.name }}</span>
      <span v-else>Select Items</span>
      <svg
        :class="isVisible ? 'dropdown' : ''"
        class="drop-down-icon"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        width="24"
        height="24"
      >
        <path
          d="M11.9997 10.8284L7.04996 15.7782L5.63574 14.364L11.9997 8L18.3637 14.364L16.9495 15.7782L11.9997 10.8284Z"
        ></path>
      </svg>
    </div>
    <div
      class="dropdown-popover"
      v-if="isVisible"
      :class="isVisible ? 'visible' : 'invisible'"
    >
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search for user.."
      />
      <span v-if="filteredUsers.length === 0">No Data Available</span>
      <div class="options-parent">
        <div class="options">
          <ul>
            <li
              @click="selectItem(user)"
              v-for="(user, index) in filteredUsers"
              :key="`user-${index}`"
            >
              {{ user.name.toUpperCase() }}
              <div style="border-bottom: 2px solid gray" />
              <div style="display: flex; gap: 5px; justify-content: center">
                <p style="min-width: 200px; text-align: right; padding: 20px">
                  {{ user.name }}
                </p>
                <div style="border-right: 2px solid blue" / >
                <div style="display: flex; flex-direction: column">
                  <p style="font-weight: bold">{{ user.name }}</p>
                  <p style="color: grey">
                    {{ user.body }}
                  </p>
                  <p style="color: grey">
                    {{ user.email }}
                  </p>
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>
  <script>
export default {
  data() {
    return {
      searchQuery: "",
      selectedItem: null,
      isVisible: false,
      userArray: [],
    };
  },
  computed: {
    filteredUsers() {
      const query = this.searchQuery.toLowerCase();
      if (this.searchQuery === "") {
        return this.userArray;
      }
      return this.userArray.filter((user) => {
        return Object.values(user).some((word) =>
          String(word).toLowerCase().includes(query)
        );
      });
    },
  },
  methods: {
    selectItem(user) {
      this.selectedItem = user;
      this.isVisible = false;
    },
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/comments")
      .then((res) => res.json())
      .then((json) => {
        console.log(json);
        this.userArray = json;
      });
  },
};
</script>
  <style lang="scss" scoped>
.dropdown-wrapper {
  max-width: 750px;
  position: relative;
  margin: 0 auto;

  .seleted-item {
    height: 40px;
    border: 2px solid lightgray;
    border-radius: 5px;
    padding: 5px 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 20px;
    font-weight: 400;
    // .drop-down-icon {
    //   transform: rotate(0deg);
    //   transition: all 0.3s ease;
    // }
    // .drop-down-icon.dropdown {
    //   transform: rotate(180deg);
    //   transition: all 0.3s ease;
    // }
    .drop-down-icon {
      transform: rotate(0deg);
      transition: all 0.3s ease;
      &.dropdown {
        transform: rotate(180deg);
      }
    }
  }
  .dropdown-popover {
    position: absolute;
    // border: 2px solid lightgray;
    border: 2px solid red;
    top: 46px;
    left: 0;
    right: 0;
    background-color: #fff;
    max-width: 100%;
    padding: 10px;
    visibility: hidden;
    transition: all 0.5s linear;
    max-height: 0px;
    overflow: hidden;

    &.visible {
      max-height: 450px;
      visibility: visible;
    }
    input {
      width: 100%;
      height: 36px;
      border: 2px solid lightgray;
      font-size: 16px;
      padding-left: 8px;
    }
    .options-parent {
      display: flex;
    }
    .options {
      width: 100%;
      ul {
        list-style: none;
        text-align: left;
        padding: 8px;
        max-height: 180px;
        overflow-y: scroll;
        overflow-x: hidden;

        li {
          width: 100%;
          border-bottom: 1px solid lightgray;
          padding: 10px;
          background-color: #f1f1f1;
          cursor: pointer;
          font-size: 16px;
          &:hover {
            // background: #70878a;
            // color: #fff;
            font-weight: bold;
          }
        }
      }
    }
  }
}
</style>