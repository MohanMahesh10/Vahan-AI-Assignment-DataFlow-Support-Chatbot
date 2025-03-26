<template>
  <div class="bg-white rounded-lg shadow-md p-4 mb-4">
    <h3 class="text-lg font-semibold mb-3">Google AI Studio API Key</h3>
    
    <div v-if="showForm">
      <p class="text-sm text-gray-600 mb-3">
        Enter your Google AI Studio API key to enable AI-powered responses.
      </p>
      
      <form @submit.prevent="saveApiKey" class="space-y-3">
        <div>
          <label for="apiKey" class="block text-sm font-medium text-gray-700 mb-1">API Key</label>
          <input 
            type="password" 
            id="apiKey" 
            v-model="apiKey" 
            class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
            placeholder="Enter your API key"
            required
          />
        </div>
        
        <div class="flex justify-end space-x-2">
          <button 
            type="button" 
            @click="showForm = false"
            class="px-3 py-1 border border-gray-300 rounded-md text-sm text-gray-700 hover:bg-gray-50"
          >
            Cancel
          </button>
          <button 
            type="submit" 
            class="px-3 py-1 bg-blue-600 text-white rounded-md text-sm hover:bg-blue-700"
          >
            Save
          </button>
        </div>
      </form>
    </div>
    
    <div v-else class="flex justify-between items-center">
      <div>
        <p class="text-sm" :class="apiKeyStatus.color">
          <span class="flex items-center">
            <svg v-if="apiKeyStatus.icon === 'check'" class="h-4 w-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
            </svg>
            <svg v-else-if="apiKeyStatus.icon === 'warning'" class="h-4 w-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"></path>
            </svg>
            {{ apiKeyStatus.text }}
          </span>
        </p>
      </div>
      <button 
        @click="showForm = true"
        class="text-sm text-blue-600 hover:text-blue-800"
      >
        {{ hasApiKey ? 'Change' : 'Add' }}
      </button>
    </div>
  </div>
</template>

<script>
import { ref, computed, onMounted } from 'vue';
import { apiConfig } from '../config/apiConfig';

export default {
  name: 'ApiKeyForm',
  emits: ['api-key-updated'],
  setup(props, { emit }) {
    const apiKey = ref('');
    const showForm = ref(false);
    const hasApiKey = ref(false);
    
    // Check if API key exists on mount
    onMounted(() => {
      const storedKey = localStorage.getItem('googleAIStudioKey');
      if (storedKey) {
        hasApiKey.value = true;
        // Update the apiConfig with the stored key
        apiConfig.googleAIStudioKey = storedKey;
      } else {
        // Show form if no API key is stored
        showForm.value = true;
      }
    });
    
    // Computed property for API key status display
    const apiKeyStatus = computed(() => {
      if (hasApiKey.value) {
        return {
          text: 'API Key configured',
          color: 'text-green-600',
          icon: 'check'
        };
      } else {
        return {
          text: 'API Key not configured',
          color: 'text-amber-600',
          icon: 'warning'
        };
      }
    });
    
    // Save API key to localStorage and update config
    const saveApiKey = () => {
      if (apiKey.value) {
        localStorage.setItem('googleAIStudioKey', apiKey.value);
        apiConfig.googleAIStudioKey = apiKey.value;
        hasApiKey.value = true;
        showForm.value = false;
        apiKey.value = '';
        
        // Emit event to notify parent component
        emit('api-key-updated', true);
      }
    };
    
    return {
      apiKey,
      showForm,
      hasApiKey,
      apiKeyStatus,
      saveApiKey
    };
  }
};
</script>