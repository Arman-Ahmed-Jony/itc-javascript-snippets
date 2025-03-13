# VSCode Extension: Vue and Pinia Snippets

## Overview
This VSCode extension provides a set of useful snippets for initializing Vue components, Pinia stores, actions, services, and forms in JavaScript and TypeScript projects. The snippets are designed to streamline development with Vue 3, Pinia, and Quasar.

## Snippets Included

### 1. **Pinia Store Initialization**
- **Prefix:** `init.store`
- **Description:** Generates a basic Pinia store.
- **Usage:**
  ```javascript
  import { defineStore } from 'pinia'
  import actions from './actions'

  export const useExampleStore = defineStore('examples', {
    state: () => ({
      examples: [],
      example: {}
    }),
    actions
  })
  ```

### 2. **Pinia Actions File**
- **Prefix:** `init.action`
- **Description:** Creates a Pinia actions file with basic CRUD operations.
- **Usage:**
  ```javascript
  import Api from 'services/ExampleService'

  export default {
    async getAll(payload) {
      try {
        const { data: { data } } = await Api.getAll(payload)
        this.examples = data
      } catch (error) {}
    },
    async getById(payload) {
      try {
        const { data: { data } } = await Api.getById(payload)
        this.example = data
      } catch (error) {}
    },
    async create(payload) {
      try {
        const { data } = await Api.create(payload)
        this.examples.push(data)
      } catch (error) {}
    },
    async update(id, payload) {
      try {
        const { data } = await Api.update(id, payload)
        const index = this.examples.findIndex(example => example.id === id)
        this.examples[index] = data
      } catch (error) {}
    },
    async deleteById(id) {
      try {
        await Api.deleteById(id)
        this.examples = this.examples.filter(example => example.id !== id)
      } catch (error) {}
    }
  }
  ```

### 3. **API Service File**
- **Prefix:** `init.service`
- **Description:** Generates a basic API service for handling HTTP requests.
- **Usage:**
  ```javascript
  import client from './client'

  const RESOURCE_NAME = 'example'

  export default {
    getAll() {
      return client().get(RESOURCE_NAME)
    },
    getById(id) {
      return client().get(`${RESOURCE_NAME}/${id}`)
    },
    create(payload) {
      return client().post(RESOURCE_NAME, payload)
    },
    update(id, payload) {
      return client().put(`${RESOURCE_NAME}/${id}`, payload)
    },
    deleteById(id) {
      return client().delete(`${RESOURCE_NAME}/${id}`)
    }
  }
  ```

### 4. **Quasar List Component**
- **Prefix:** `init.vue.list`
- **Description:** Creates a Quasar `<q-list>` component for displaying data.

### 5. **Quasar Form Component**
- **Prefix:** `init.vue.form`
- **Description:** Generates a Quasar `<q-form>` component with validation and submission logic.

### 6. **Quasar Page Component**
- **Prefix:** `init.vue.index`
- **Description:** Creates a full-page Quasar component with list and form components integrated.

## Installation
1. Open VSCode.
2. Navigate to the Extensions Marketplace.
3. Search for the extension and install it.
4. Start using the snippets by typing their respective prefixes.

## Usage
Simply type the snippet prefix in a Vue or JavaScript/TypeScript file and select the snippet from the autocomplete suggestions.

## License
This extension is released under the MIT License.

## Contributions
Contributions are welcome! Feel free to submit pull requests or open issues for enhancements.

