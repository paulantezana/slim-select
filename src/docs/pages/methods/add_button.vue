<script lang="ts">
import { defineComponent } from 'vue'
import HighlightStyle from '../../components/highlight_style.vue'

import SlimSelect from '@/slim-select'

export default defineComponent({
  name: 'AddButtonMethod',
  components: {
    HighlightStyle
  },
  data() {
    return {
      addButtonSelect: null as SlimSelect | null
    }
  },
  mounted() {
    this.addButtonSelect = new SlimSelect({
      select: this.$refs.addButtonMethod as HTMLSelectElement,
      settings: {
        addButtonEnabled: true,
        addButtonText: 'Add Custom Item'
      },
      events: {
        addButton: () => {
          alert('Add button was clicked! You can customize this behavior.')
        }
      }
    })
  }
})
</script>

<template>
  <div id="addButtonMethod" class="content">
    <h2 class="header">addButton settings</h2>
    <p>
      The addButton feature provides settings to enable and customize the add button displayed at the bottom of the
      dropdown content area. This button executes a custom callback when clicked, allowing you to implement features
      like opening a modal, creating new items, or performing any other custom action.
    </p>
    <p>
      You can enable the add button and customize its text label through the settings object. The button appears after
      the list of options and automatically closes the dropdown after the event is triggered, providing a smooth user
      experience.
    </p>

    <div class="row">
      <select ref="addButtonMethod">
        <option value="value1">Value 1</option>
        <option value="value2">Value 2</option>
        <option value="value3">Value 3</option>
      </select>
    </div>

    <HighlightStyle language="javascript">
      <pre>
        new SlimSelect({
          select: '#selectElement',
          settings: {
            // Enable the add button
            addButtonEnabled: true,
            
            // Set the text displayed on the button
            addButtonText: 'Add New Item'
          },
          events: {
            // Handle the add button click
            addButton: function () {
              // Perform your custom action here
              console.log('Add button clicked!')
              
              // Examples:
              // - Open a modal for creating new items
              // - Show a form
              // - Trigger an API call
              // - Open a new tab or page
              // - Any custom logic you need
            }
          }
        })
      </pre>
    </HighlightStyle>
  </div>
</template>
