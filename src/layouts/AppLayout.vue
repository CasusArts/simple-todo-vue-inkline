<template>
  <i-layout class="layout-main">
    <i-container>
      <i-row>
        <i-column :xs="12">
          <i-layout-header>
            <i-navbar size="sm">
              <i-navbar-brand>
                <i-button @click="toggleDarkMode" class="_float-right" size="sm">
                  <i-icon icon="light" />
                </i-button>
                Simple To-Do
              </i-navbar-brand>
              <i-navbar-items>
                <i-nav>
                  <i-nav-item>About</i-nav-item>
                </i-nav>
              </i-navbar-items>
            </i-navbar>
          </i-layout-header>
        </i-column>
      </i-row>

      <i-row>
        <i-column :xs="12">
          <i-layout-content>
            <TodoList />
          </i-layout-content>
        </i-column>
      </i-row>
    </i-container>
  </i-layout>
</template>

<script>
import TodoList from "../components/todo/TodoList.vue";
export default {
  name: "AppLayout",
  components: {
    TodoList,
  },
  methods: {
    toggleDarkMode() {
      this.$inkline.config.variant =
        this.$inkline.config.variant === "light" ? "dark" : "light";
    },
  },
};
</script>
