<template>
  <div class="layout-padding">
    <h1>Grid Component</h1>
    <quasar-grid
      :columns="columns"
      :data="data"
      :rows-per-page="5"
      :selection-mode="selection.mode"
      :selection-actions="selection.actions"
      id-property="unique_id"
    ></quasar-grid>
  </div>
</template>

<script>
import data from 'asset/grid-data.json'

export default {
  data () {
    return {
      data,
      columns: [
        {
          label: 'Date',
          field: 'isodate',
          style: 'width: 100px',
          formatter (value) {
            return new Date(value).toLocaleString()
          }
        },
        {
          label: 'Source',
          field: 'source',
          style: 'width: 100px'
        },
        {
          label: 'Service',
          field: 'serviceable',
          formatter (value) {
            if (value === 'Informational') {
              return '<i>info</i>'
            }
            return value
          },
          style: 'color: green; width: 100px',
          classes: 'text-center'
        },
        {
          label: 'Log Number',
          field: 'log_number',
          style: 'width: 100px'
        },
        {
          label: 'Message',
          field: 'message',
          style: 'width: 700px'
        }
      ],
      selection: {
        mode: 'single',
        actions: [
          {
            label: 'View 1',
            handler (selectedRows) {
              console.dir(selectedRows)
            }
          },
          {
            label: 'View 2',
            handler (selectedRows) {
              console.dir(selectedRows)
            }
          }
        ]
      }
    }
  }
}
</script>
