<template>
  <div :class="['flex', message.type === 'user' ? 'justify-end' : 'justify-start']">
    <div 
      :class="[
        'max-w-3/4 rounded-lg p-3 break-words', 
        message.type === 'user' 
          ? 'bg-blue-600 text-white rounded-br-none' 
          : 'bg-gray-100 text-gray-800 rounded-bl-none'
      ]">
      <div class="whitespace-pre-line" v-html="formattedText"></div>
      <div 
        :class="[
          'text-xs mt-1', 
          message.type === 'user' ? 'text-blue-200' : 'text-gray-500'
        ]">
        {{ formattedTime }}
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue';
import { format } from 'date-fns';

export default {
  name: 'ChatMessage',
  props: {
    message: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    // Format the message text with markdown-like syntax
    const formattedText = computed(() => {
      if (!props.message.text) return '';
      
      // Replace markdown-style bold with HTML bold
      let formatted = props.message.text.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>');
      
      // Replace markdown-style lists with HTML lists
      formatted = formatted.replace(/^- (.*?)$/gm, '• $1');
      
      // Replace newlines with <br>
      formatted = formatted.replace(/\n/g, '<br>');
      
      return formatted;
    });

    // Format the timestamp
    const formattedTime = computed(() => {
      if (!props.message.timestamp) return '';
      return format(props.message.timestamp, 'h:mm a');
    });

    return {
      formattedText,
      formattedTime
    };
  }
};
</script>