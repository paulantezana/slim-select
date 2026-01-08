<script lang="ts">
import { defineComponent } from 'vue'
import HighlightStyle from '../../components/highlight_style.vue'

import SlimSelect from '@/slim-select'

export default defineComponent({
  name: 'AddButton',
  components: {
    HighlightStyle
  },
  mounted() {
    new SlimSelect({
      select: this.$refs.addButtonSingle as HTMLSelectElement,
      settings: {
        addButtonText: 'Add New Item'
      },
      events: {
        addButton: () => {
          const name = prompt('Enter item name:')
          if (name) {
            console.log('Add button clicked! You entered:', name)
          }
        }
      }
    })

    new SlimSelect({
      select: this.$refs.addButtonMultiple as HTMLSelectElement,
      settings: {
        addButtonText: 'Create Item'
      },
      events: {
        addButton: () => {
          console.log('Add button clicked!')
          // You can perform any action here
          // For example: open a modal, show a form, etc.
        }
      }
    })
  }
})
</script>

<template>
  <div id="addButton" class="content">
    <h2 class="header">addButton Event</h2>
    <p>
      The addButton event enables you to execute a custom action when the add button in the dropdown content is clicked.
      This button appears at the bottom of the dropdown list, providing users with a dedicated action trigger for
      creating new items or performing custom operations.
    </p>
    <p>
      This feature is perfect for scenarios where you want to provide a direct action button within the dropdown,
      allowing you to open modals, show forms, trigger API calls, or any other custom logic you need. The button
      automatically closes the dropdown after the event is triggered.
    </p>

    <div class="row">
      <select ref="addButtonSingle">
        <option value="value1">Value 1</option>
        <option value="value2">Value 2</option>
        <option value="value3">Value 3</option>
      </select>
      <select ref="addButtonMultiple" multiple>
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
            addButtonText: 'Add New Item'
          },
          events: {
            addButton: function () {
              // Your custom logic here
              // For example: open a modal, trigger an API call, etc.
              console.log('Add button clicked!')
            }
          }
        })
      </pre>
    </HighlightStyle>
  </div>
</template>
