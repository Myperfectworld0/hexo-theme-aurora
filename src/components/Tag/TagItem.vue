<template>
  <div
    class="flex flex-row items-center hover:opacity-50 mr-2 mb-2 cursor-pointer transition-all"
  >
    <span
      class="bg-ob-deep-900 text-center px-3 py-1 rounded-tl-md rounded-bl-md text-sm"
      :style="stylingTag()"
    >
      <router-link :to="{ name: 'tags-search', query: { slug: slug } }">
        <em class="opacity-50"># </em>{{ name }}
      </router-link>
    </span>
    <b
      class="bg-ob-deep-900 text-ob-secondary text-center px-2 py-1 rounded-tr-md rounded-br-md text-sm opacity-70"
      :style="stylingTag()"
    >
      {{ count }}
    </b>
  </div>
</template>

<script lang="ts">
import { defineComponent, toRefs } from 'vue'

export default defineComponent({
  name: 'ObTagItem',
  props: {
    name: String,
    slug: String,
    count: {
      type: Number,
      default: 0
    },
    size: {
      type: String,
      default: 'base'
    }
  },
  setup(props) {
    const tagSize = toRefs(props).size

    const stylingTag = () => {
      if (tagSize.value === 'xs') {
        return {
          fontSize: '0.75rem',
          lineHeight: '1rem'
        }
      }

      if (tagSize.value === 'sm') {
        return {
          fontSize: '0.875rem',
          lineHeight: '1.25rem'
        }
      }

      if (tagSize.value === 'lg') {
        return {
          fontSize: '1.125rem',
          lineHeight: '1.75rem'
        }
      }

      if (tagSize.value === 'xl') {
        return {
          fontSize: '1.25rem',
          lineHeight: '1.75rem'
        }
      }

      if (tagSize.value === '2xl') {
        return {
          fontSize: '1.5rem',
          lineHeight: '2rem'
        }
      }

      return {
        fontSize: '1rem',
        lineHeight: '1.5rem'
      }
    }

    return { stylingTag }
  }
})
</script>
