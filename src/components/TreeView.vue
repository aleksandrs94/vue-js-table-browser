<template>
  <div>
    <li class="node" :style="{ 'margin-left': `${depth * 28}px` }">
      <p>
        <span
          v-if="hasTable && !hasChildren"
          class="mr-2 pointer table-icon"
          :class="{ 'primary-text': hasBookmarked }"
          @click="bookmarkClicked()"
        >
          {{ hasBookmarked ? "&#9670;" : "&#9671;" }}
        </span>
        <span class="pointer" @click="nodeClicked()">
          <span v-if="hasChildren" class="mr-2">
            {{ expanded ? "&#9660;" : "&#9658;" }}
          </span>
          <span v-else-if="!hasChildren && !hasTable" class="mr-2">
            &#10672;
          </span>
          <span>
            {{ node.name }}
          </span>
        </span>
      </p>
    </li>

    <div v-show="expanded">
      <TreeView
        v-for="(child, i) in node.children"
        :key="i"
        :node="child"
        :depth="depth + 1"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeView",

  props: {
    node: {
      type: Object,
      default: () => {}
    },
    depth: {
      type: Number,
      default: 0
    }
  },

  data() {
    return {
      expanded: false,
      bookmarked: false
    };
  },
  computed: {
    hasChildren() {
      return !!this.node.children;
    },
    hasTable() {
      return !!this.node.name;
    },
    hasBookmarked() {
      return this.bookmarked;
    }
  },
  methods: {
    nodeClicked() {
      if (!this.hasChildren && this.hasTable) {
        // open table
      } else if (this.hasChildren) {
        this.expanded = !this.expanded;
      } else {
        // set opened to null
      }
    },
    bookmarkClicked() {
      this.bookmarked = !this.bookmarked;
    }
  }
};
</script>

<style scoped lang="scss">
.node {
  text-align: left;
  font-size: 16px;
  line-height: 21px;
  margin-top: 1px;
}
.pointer {
  cursor: pointer;
}
.empty {
  color: #7a7a7a;
}
.empty-border {
  border: 1px dotted #7a7a7a;
  border-width: 0 0 1px 1px;
}
ul,
li {
  list-style: none;
  margin: 0;
  padding: 0;
  p {
    margin: 0;
    background: #ffffff;
    position: relative;
    top: 0.6em;
  }
  &.dark {
    background: #121212;
  }
  &.main-categories {
    font-size: 18px;
  }
  .name-text {
    &:hover {
      opacity: 0.85;
    }
  }
}
li {
  padding-left: 1.2em;
  border: 1px dotted black;
  border-width: 0 0 1px 1px;
}
li.dark {
  padding-left: 1.2em;
  border: 1px dotted white;
  border-width: 0 0 1px 1px;
}
li.container {
  border-bottom: 0px;
}
li ul {
  border-top: 1px dotted black;
  margin-left: -1em;
  padding-left: 2em;
}
ul li:last-child ul {
  border-left: 1px white;
  padding-left: -17px;
}
.v-tooltip__content {
  font-size: 13px;
}
</style>
