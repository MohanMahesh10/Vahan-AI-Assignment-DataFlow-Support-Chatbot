<template>
  <div class="min-h-screen bg-gray-50 flex flex-col relative">
    <header class="bg-blue-600 text-white py-4 shadow-md">
      <div class="container mx-auto px-4 flex items-center justify-between">
        <div class="flex items-center">
          <svg class="h-8 w-8 mr-2" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2 17L12 22L22 17" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M2 12L12 17L22 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <h1 class="text-xl font-bold">DataFlow Support</h1>
        </div>
        <div class="hidden md:flex space-x-4 z-10">
          <a href="javascript:void(0)" @click.prevent="activeSection = 'dashboard'" 
                  class="px-3 py-2 hover:text-blue-200 focus:outline-none transition-colors relative z-10 cursor-pointer"
                  :class="[activeSection === 'dashboard' ? 'font-bold border-b-2 border-white' : '']">
            Dashboard
          </a>
          <a href="javascript:void(0)" @click.prevent="activeSection = 'documentation'" 
                  class="px-3 py-2 hover:text-blue-200 focus:outline-none transition-colors relative z-10 cursor-pointer"
                  :class="[activeSection === 'documentation' ? 'font-bold border-b-2 border-white' : '']">
            Documentation
          </a>
          <a href="javascript:void(0)" @click.prevent="activeSection = 'contact'" 
                  class="px-3 py-2 hover:text-blue-200 focus:outline-none transition-colors relative z-10 cursor-pointer"
                  :class="[activeSection === 'contact' ? 'font-bold border-b-2 border-white' : '']">
            Contact
          </a>
        </div>
      </div>
    </header>

    <main class="flex-grow container mx-auto px-4 py-6 flex flex-col md:flex-row gap-6">
      <!-- Dashboard Section -->
      <div v-if="activeSection === 'dashboard'" class="w-full">
        <div class="bg-white rounded-lg shadow-md p-6">
          <h2 class="text-2xl font-bold mb-6 text-blue-600">Dashboard</h2>
          
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
            <div class="bg-blue-50 p-4 rounded-lg shadow">
              <h3 class="text-lg font-semibold mb-2">Total Users</h3>
              <p class="text-3xl font-bold text-blue-600">1,245</p>
              <p class="text-sm text-gray-500 mt-1">+12% from last month</p>
            </div>
            
            <div class="bg-green-50 p-4 rounded-lg shadow">
              <h3 class="text-lg font-semibold mb-2">Active Projects</h3>
              <p class="text-3xl font-bold text-green-600">37</p>
              <p class="text-sm text-gray-500 mt-1">+5 new this week</p>
            </div>
            
            <div class="bg-purple-50 p-4 rounded-lg shadow">
              <h3 class="text-lg font-semibold mb-2">Data Sources</h3>
              <p class="text-3xl font-bold text-purple-600">89</p>
              <p class="text-sm text-gray-500 mt-1">12 pending connections</p>
            </div>
          </div>
          
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4">Recent Activity</h3>
            <div class="bg-gray-50 rounded-lg p-4">
              <ul class="divide-y divide-gray-200">
                <li class="py-3 flex justify-between">
                  <span>New data source connected: <strong>MySQL Database</strong></span>
                  <span class="text-gray-500">2 hours ago</span>
                </li>
                <li class="py-3 flex justify-between">
                  <span>Dashboard <strong>Sales Overview</strong> shared with team</span>
                  <span class="text-gray-500">Yesterday</span>
                </li>
                <li class="py-3 flex justify-between">
                  <span>New visualization created: <strong>Customer Retention</strong></span>
                  <span class="text-gray-500">2 days ago</span>
                </li>
                <li class="py-3 flex justify-between">
                  <span>API usage limit increased to <strong>10,000 requests/day</strong></span>
                  <span class="text-gray-500">3 days ago</span>
                </li>
              </ul>
            </div>
          </div>
          
          <div>
            <h3 class="text-xl font-semibold mb-4">System Status</h3>
            <div class="bg-gray-50 rounded-lg p-4">
              <div class="flex items-center mb-3">
                <div class="w-3 h-3 bg-green-500 rounded-full mr-2"></div>
                <span>All systems operational</span>
              </div>
              <div class="text-sm text-gray-600">
                <p>Last incident: 15 days ago - API Latency Issues (Resolved)</p>
                <p class="mt-2">Scheduled maintenance: June 15, 2023 - 2:00 AM UTC</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Documentation Section -->
      <div v-else-if="activeSection === 'documentation'" class="w-full">
        <div class="bg-white rounded-lg shadow-md p-6">
          <h2 class="text-2xl font-bold mb-6 text-blue-600">Documentation</h2>
          
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4">Getting Started</h3>
            <div class="prose max-w-none">
              <p class="mb-4">Welcome to DataFlow! This guide will help you get started with our platform and make the most of its powerful features.</p>
              
              <h4 class="text-lg font-medium mt-6 mb-2">1. Creating Your Account</h4>
              <p>To begin using DataFlow, you'll need to create an account. Visit our signup page and follow the instructions to set up your account. You'll need to provide your email address and create a password.</p>
              
              <h4 class="text-lg font-medium mt-6 mb-2">2. Connecting Data Sources</h4>
              <p>DataFlow supports a wide range of data sources, including databases, APIs, and file uploads. To connect a data source:</p>
              <ul class="list-disc pl-6 my-3">
                <li>Navigate to the Data Sources section in your dashboard</li>
                <li>Click "Add New Data Source"</li>
                <li>Select your data source type from the list</li>
                <li>Follow the connection wizard to establish the connection</li>
              </ul>
              
              <h4 class="text-lg font-medium mt-6 mb-2">3. Creating Your First Visualization</h4>
              <p>Once your data source is connected, you can start creating visualizations:</p>
              <ul class="list-disc pl-6 my-3">
                <li>Go to the Visualizations section</li>
                <li>Click "New Visualization"</li>
                <li>Select your data source</li>
                <li>Choose a visualization type (chart, table, etc.)</li>
                <li>Configure your visualization settings</li>
                <li>Save and add to a dashboard</li>
              </ul>
            </div>
          </div>
          
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4">API Reference</h3>
            <div class="bg-gray-50 rounded-lg p-4">
              <p class="mb-4">DataFlow provides a comprehensive API for integrating with your applications. Here's a quick overview:</p>
              
              <div class="mb-4">
                <h4 class="text-lg font-medium mb-2">Authentication</h4>
                <pre class="bg-gray-800 text-green-400 p-3 rounded overflow-x-auto">curl -X POST https://api.dataflow.com/v1/auth/token \
  -H "Content-Type: application/json" \
  -d '{"apiKey": "YOUR_API_KEY"}'</pre>
              </div>
              
              <div>
                <h4 class="text-lg font-medium mb-2">Fetching Data</h4>
                <pre class="bg-gray-800 text-green-400 p-3 rounded overflow-x-auto">curl -X GET https://api.dataflow.com/v1/data/query \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query": "SELECT * FROM sales LIMIT 10"}'</pre>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Contact Section -->
      <div v-else-if="activeSection === 'contact'" class="w-full">
        <div class="bg-white rounded-lg shadow-md p-6">
          <h2 class="text-2xl font-bold mb-6 text-blue-600">Contact Us</h2>
          
          <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div>
              <h3 class="text-xl font-semibold mb-4">Get in Touch</h3>
              <p class="mb-6">We're here to help with any questions or concerns you may have about DataFlow. Our support team is available 24/7.</p>
              
              <div class="space-y-4">
                <div class="flex items-start">
                  <div class="bg-blue-100 p-2 rounded-full mr-3">
                    <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                    </svg>
                  </div>
                  <div>
                    <h4 class="font-medium">Email</h4>
                    <p class="text-blue-600">boggavarapumohanmahesh@gmail.com</p>
                  </div>
                </div>
                
                <div class="flex items-start">
                  <div class="bg-blue-100 p-2 rounded-full mr-3">
                    <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
                    </svg>
                  </div>
                  <div>
                    <h4 class="font-medium">Phone</h4>
                    <p class="text-blue-600">+91 8919601172</p>
                  </div>
                </div>
                
                <div class="flex items-start">
                  <div class="bg-blue-100 p-2 rounded-full mr-3">
                    <svg class="w-5 h-5 text-blue-600" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                    </svg>
                  </div>
                  <div>
                    <h4 class="font-medium">Address</h4>
                    <p>123 Data Street<br>Nellore, Andhra Pradesh 94107<br>India</p>
                  </div>
                </div>
              </div>
            </div>
            
            <div>
              <h3 class="text-xl font-semibold mb-4">Send a Message</h3>
              <form class="space-y-4">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-700 mb-1">Name</label>
                  <input type="text" id="name" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Your name">
                </div>
                
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email</label>
                  <input type="email" id="email" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Your email">
                </div>
                
                <div>
                  <label for="subject" class="block text-sm font-medium text-gray-700 mb-1">Subject</label>
                  <input type="text" id="subject" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Message subject">
                </div>
                
                <div>
                  <label for="message" class="block text-sm font-medium text-gray-700 mb-1">Message</label>
                  <textarea id="message" rows="4" class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Your message"></textarea>
                </div>
                
                <button type="submit" class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500">
                  Send Message
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Chat Interface (Default) -->
      <div v-else class="flex flex-col md:flex-row gap-6 w-full">
        <div class="md:w-1/3 lg:w-1/4">
          <div class="bg-white rounded-lg shadow-md p-4 mb-6">
            <h2 class="text-lg font-semibold mb-4">Popular Topics</h2>
            <ul class="space-y-2">
              <li v-for="topic in popularTopics" :key="topic.id" 
                  class="p-2 hover:bg-blue-50 rounded cursor-pointer transition-colors"
                  @click="suggestQuestion(topic.question)">
                {{ topic.title }}
              </li>
            </ul>
          </div>
          
          <div class="bg-white rounded-lg shadow-md p-4">
            <h2 class="text-lg font-semibold mb-4">Chat Analytics</h2>
            <ChatAnalytics :analytics="analytics" />
          </div>
        </div>

        <div class="md:w-2/3 lg:w-3/4 flex flex-col">
          <div class="bg-white rounded-lg shadow-md flex-grow flex flex-col">
            <div class="p-4 border-b">
              <h2 class="text-lg font-semibold">DataFlow AI Assistant</h2>
              <p class="text-sm text-gray-500">Ask me anything about DataFlow</p>
            </div>
            
            <div class="flex-grow overflow-y-auto p-4" ref="chatContainer">
              <div class="space-y-4">
                <ChatMessage 
                  v-for="(message, index) in chatHistory" 
                  :key="index"
                  :message="message" />
              </div>
            </div>
            
            <div class="border-t p-4">
              <form @submit.prevent="sendMessage" class="flex gap-2">
                <input 
                  v-model="userInput" 
                  type="text" 
                  placeholder="Type your question here..." 
                  class="flex-grow px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
                  :disabled="isProcessing"
                />
                <button 
                  type="submit" 
                  class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 disabled:opacity-50 disabled:cursor-not-allowed"
                  :disabled="isProcessing || !userInput.trim()"
                >
                  <span v-if="isProcessing">Processing...</span>
                  <span v-else>Send</span>
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </main>

    <footer class="bg-gray-100 py-4 border-t">
      <div class="container mx-auto px-4 text-center text-gray-600 text-sm">
        &copy; {{ new Date().getFullYear() }} MOHAN MAHESH All rights reserved.
      </div>
    </footer>
    
    <!-- Floating Chat Toggle Bar -->
    <div class="fixed bottom-6 right-6 z-50">
      <div v-if="!isChatOpen" 
           @click="toggleChat"
           class="bg-blue-600 text-white p-4 rounded-full shadow-lg cursor-pointer hover:bg-blue-700 transition-all duration-300 flex items-center justify-center">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
        </svg>
      </div>
      
      <div v-if="isChatOpen" 
           class="bg-white rounded-lg shadow-xl overflow-hidden transition-all duration-300 flex flex-col"
           :class="{'w-96 h-[450px]': isChatOpen, 'w-0 h-0': !isChatOpen}">
        <div class="bg-blue-600 text-white p-3 flex justify-between items-center">
          <h3 class="font-semibold">DataFlow AI Assistant</h3>
          <div class="flex items-center space-x-2">
            <button @click="showApiSettings = !showApiSettings" class="text-white hover:text-blue-200">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
            </button>
            <button @click="toggleChat" class="text-white hover:text-blue-200">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
              </svg>
            </button>
          </div>
        </div>
        
        <div v-if="showApiSettings" class="p-3 border-b">
          <ApiKeyForm @api-key-updated="handleApiKeyUpdate" />
        </div>
        
        <div class="flex-grow overflow-y-auto p-4" ref="floatingChatContainer">
          <div class="space-y-4">
            <ChatMessage 
              v-for="(message, index) in floatingChatHistory" 
              :key="index"
              :message="message" />
          </div>
        </div>
        
        <div class="border-t p-3">
          <form @submit.prevent="sendFloatingMessage" class="flex gap-2">
            <input 
              v-model="floatingUserInput" 
              type="text" 
              placeholder="Type your question here..." 
              class="flex-grow px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 text-sm"
              :disabled="isFloatingProcessing"
            />
            <button 
              type="submit" 
              class="bg-blue-600 text-white px-3 py-2 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 disabled:opacity-50 disabled:cursor-not-allowed text-sm"
              :disabled="isFloatingProcessing || !floatingUserInput.trim()"
            >
              <span v-if="isFloatingProcessing">...</span>
              <span v-else>
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
                </svg>
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, nextTick, computed, watch } from 'vue';
import ChatMessage from './components/ChatMessage.vue';
import ChatAnalytics from './components/ChatAnalytics.vue';
import ApiKeyForm from './components/ApiKeyForm.vue';
import { knowledgeBase } from './data/knowledgeBase';
import { format } from 'date-fns';
import { aiService } from './services/aiService';

export default {
  name: 'App',
  components: {
    ChatMessage,
    ChatAnalytics,
    ApiKeyForm
  },
  setup() {
    const userInput = ref('');
    const chatHistory = ref([]);
    const chatContainer = ref(null);
    const isProcessing = ref(false);
    const activeSection = ref('dashboard'); // Default to dashboard interface
    
    // Floating chat variables
    const isChatOpen = ref(false);
    const floatingUserInput = ref('');
    const floatingChatHistory = ref([]);
    const floatingChatContainer = ref(null);
    const isFloatingProcessing = ref(false);
    const showApiSettings = ref(false);
    
    // Handle API key update
    const handleApiKeyUpdate = (success) => {
      if (success) {
        // Add a system message to indicate API key was updated
        floatingChatHistory.value.push({
          type: 'bot',
          text: 'Google AI Studio API key has been updated successfully! You can now use the AI-powered assistant.',
          timestamp: new Date()
        });
        scrollToFloatingBottom();
        showApiSettings.value = false;
      }
    };
    const analytics = ref({
      totalQuestions: 0,
      answeredQuestions: 0,
      fallbackResponses: 0,
      topQuestions: [
        { question: 'What is DataFlow?', count: 12 },
        { question: 'How much does it cost?', count: 8 },
        { question: 'How do I connect my data?', count: 5 }
      ],
      dailyInteractions: [
        { date: '2023-06-01', count: 24 },
        { date: '2023-06-02', count: 18 },
        { date: '2023-06-03', count: 32 },
        { date: '2023-06-04', count: 28 },
        { date: '2023-06-05', count: 42 },
        { date: '2023-06-06', count: 38 },
        { date: '2023-06-07', count: 45 }
      ]
    });

    const popularTopics = [
      { id: 1, title: 'Getting Started', question: 'How do I get started with DataFlow?' },
      { id: 2, title: 'Pricing Plans', question: 'What are the pricing plans for DataFlow?' },
      { id: 3, title: 'Data Integration', question: 'How can I connect my data sources?' },
      { id: 4, title: 'Security', question: 'How secure is DataFlow?' },
      { id: 5, title: 'Mobile Access', question: 'Can I use DataFlow on my phone?' }
    ];

    // Add welcome message
    onMounted(() => {
      chatHistory.value.push({
        type: 'bot',
        text: 'Hello! I\'m your DataFlow AI assistant. How can I help you today?',
        timestamp: new Date()
      });
    });

    // Scroll to bottom of chat
    const scrollToBottom = async () => {
      await nextTick();
      if (chatContainer.value) {
        chatContainer.value.scrollTop = chatContainer.value.scrollHeight;
      }
    };

    // Find best matching document from knowledge base
    const findBestMatch = (query) => {
      const normalizedQuery = query.toLowerCase();
      let bestMatch = null;
      let highestScore = 0;
      
      // First try to match by keywords
      for (const doc of knowledgeBase) {
        const keywordMatches = doc.keywords.filter(keyword => 
          normalizedQuery.includes(keyword.toLowerCase())
        ).length;
        
        if (keywordMatches > highestScore) {
          highestScore = keywordMatches;
          bestMatch = doc;
        }
      }
      
      // If no good keyword match, try content matching
      if (highestScore === 0) {
        for (const doc of knowledgeBase) {
          const words = normalizedQuery.split(/\s+/);
          let score = 0;
          
          for (const word of words) {
            if (word.length > 3 && doc.content.toLowerCase().includes(word)) {
              score++;
            }
          }
          
          if (score > highestScore) {
            highestScore = score;
            bestMatch = doc;
          }
        }
      }
      
      return { bestMatch, score: highestScore };
    };

    // Generate response based on user input
    const generateResponse = async (query) => {
      // Update analytics
      analytics.value.totalQuestions++;
      
      try {
        // First try to find a match in the knowledge base
        const { bestMatch, score } = findBestMatch(query);
        
        // If we have a good match in our knowledge base
        if (bestMatch && (score > 0)) {
          analytics.value.answeredQuestions++;
          return bestMatch.content;
        } else {
          // If no good match, use the AI service
          const aiResponse = await aiService.generateResponse(query);
          return aiResponse;
        }
      } catch (error) {
        console.error('Error in generateResponse:', error);
        
        // Fallback response
        analytics.value.fallbackResponses++;
        return "I'm sorry, I don't have specific information about that. Would you like to know about our features, pricing, or how to get started with DataFlow?";
      }
    };

    // Send message
    const sendMessage = async () => {
      if (!userInput.value.trim() || isProcessing.value) return;
      
      const userMessage = userInput.value;
      userInput.value = '';
      isProcessing.value = true;
      
      // Add user message to chat
      chatHistory.value.push({
        type: 'user',
        text: userMessage,
        timestamp: new Date()
      });
      
      await scrollToBottom();
      
      try {
        // Generate response using AI service
        const botResponse = await generateResponse(userMessage);
        
        // Add bot response to chat
        chatHistory.value.push({
          type: 'bot',
          text: botResponse,
          timestamp: new Date()
        });
        
        // Update analytics with the current date
        const today = format(new Date(), 'yyyy-MM-dd');
        const dailyIndex = analytics.value.dailyInteractions.findIndex(item => item.date === today);
        
        if (dailyIndex >= 0) {
          analytics.value.dailyInteractions[dailyIndex].count++;
        } else {
          analytics.value.dailyInteractions.push({ date: today, count: 1 });
        }
      } catch (error) {
        console.error('Error in sendMessage:', error);
        
        // Add error message to chat
        chatHistory.value.push({
          type: 'bot',
          text: 'Sorry, there was an error processing your request. Please try again.',
          timestamp: new Date()
        });
      } finally {
        isProcessing.value = false;
        scrollToBottom();
      }
    };

    // Suggest a question
    const suggestQuestion = (question) => {
      userInput.value = question;
    };
    
    // Toggle floating chat
    const toggleChat = () => {
      isChatOpen.value = !isChatOpen.value;
      
      // Add welcome message if chat history is empty
      if (isChatOpen.value && floatingChatHistory.value.length === 0) {
        floatingChatHistory.value.push({
          type: 'bot',
          text: 'Hello! I\'m your DataFlow AI assistant. How can I help you today?',
          timestamp: new Date()
        });
        
        // Scroll to bottom after chat opens
        nextTick(() => {
          if (floatingChatContainer.value) {
            floatingChatContainer.value.scrollTop = floatingChatContainer.value.scrollHeight;
          }
        });
      }
    };
    
    // Scroll to bottom of floating chat
    const scrollToFloatingBottom = async () => {
      await nextTick();
      if (floatingChatContainer.value) {
        floatingChatContainer.value.scrollTop = floatingChatContainer.value.scrollHeight;
      }
    };
    
    // Send message in floating chat
    const sendFloatingMessage = async () => {
      if (!floatingUserInput.value.trim() || isFloatingProcessing.value) return;
      
      const userMessage = floatingUserInput.value;
      floatingUserInput.value = '';
      isFloatingProcessing.value = true;
      
      // Add user message to chat
      floatingChatHistory.value.push({
        type: 'user',
        text: userMessage,
        timestamp: new Date()
      });
      
      await scrollToFloatingBottom();
      
      try {
        // Generate response using AI service
        const botResponse = await generateResponse(userMessage);
        
        // Add bot response to chat
        floatingChatHistory.value.push({
          type: 'bot',
          text: botResponse,
          timestamp: new Date()
        });
        
        // Update analytics with the current date
        const today = format(new Date(), 'yyyy-MM-dd');
        const dailyIndex = analytics.value.dailyInteractions.findIndex(item => item.date === today);
        
        if (dailyIndex >= 0) {
          analytics.value.dailyInteractions[dailyIndex].count++;
        } else {
          analytics.value.dailyInteractions.push({ date: today, count: 1 });
        }
      } catch (error) {
        console.error('Error in sendFloatingMessage:', error);
        
        // Add error message to chat
        floatingChatHistory.value.push({
          type: 'bot',
          text: 'Sorry, there was an error processing your request. Please try again.',
          timestamp: new Date()
        });
      } finally {
        isFloatingProcessing.value = false;
        scrollToFloatingBottom();
      }
    };

    return {
      userInput,
      chatHistory,
      chatContainer,
      isProcessing,
      analytics,
      popularTopics,
      sendMessage,
      suggestQuestion,
      // Floating chat
      isChatOpen,
      toggleChat,
      floatingUserInput,
      floatingChatHistory,
      floatingChatContainer,
      isFloatingProcessing,
      sendFloatingMessage,
      showApiSettings,
      handleApiKeyUpdate
    };
  }
};
</script>

<style>
/* Any additional styles can go here */
</style>