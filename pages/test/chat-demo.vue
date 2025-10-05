<template>
  <div class="min-h-screen bg-gray-50 p-6">
    <div class="max-w-4xl mx-auto">
      <!-- Header -->
      <div class="bg-white rounded-lg shadow-sm p-6 mb-6">
        <h1 class="text-2xl font-bold text-gray-900 mb-2">AINA Chat Demo</h1>
        <p class="text-gray-600">Test the chat modal with API responses. Click the button below to open the chat interface.</p>
      </div>

      <!-- Chat Button -->
      <div class="bg-white rounded-lg shadow-sm p-6 mb-6 text-center">
        <button
          @click="openChatModal"
          class="px-6 py-3 bg-[#f5d142] text-black rounded-lg hover:bg-[#e6c23a] transition-colors flex items-center gap-3 mx-auto text-lg font-medium"
        >
          <Icon name="ic:outline-chat" size="24" />
          Start Chatting with AINA
        </button>
        <p class="text-sm text-gray-500 mt-3">Ask questions and see real-time API responses</p>
      </div>

      <!-- Features -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
        <div class="bg-white rounded-lg shadow-sm p-6">
          <div class="text-center">
            <Icon name="ic:outline-api" size="32" class="text-blue-600 mx-auto mb-3" />
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Real-time API</h3>
            <p class="text-gray-600 text-sm">Connects to live API endpoint for instant responses</p>
          </div>
        </div>
        
        <div class="bg-white rounded-lg shadow-sm p-6">
          <div class="text-center">
            <Icon name="ic:outline-message" size="32" class="text-green-600 mx-auto mb-3" />
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Smart Responses</h3>
            <p class="text-gray-600 text-sm">AI-powered answers with context awareness</p>
          </div>
        </div>
        
        <div class="bg-white rounded-lg shadow-sm p-6">
          <div class="text-center">
            <Icon name="ic:outline-history" size="32" class="text-purple-600 mx-auto mb-3" />
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Chat History</h3>
            <p class="text-gray-600 text-sm">Full conversation history maintained in session</p>
          </div>
        </div>
      </div>

      <!-- Instructions -->
      <div class="bg-white rounded-lg shadow-sm p-6">
        <h2 class="text-lg font-semibold text-gray-900 mb-4">How to Use</h2>
        <div class="space-y-3 text-sm text-gray-600">
          <div class="flex items-start gap-3">
            <div class="w-6 h-6 bg-[#f5d142] text-black rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0 mt-0.5">1</div>
            <p>Click the "Start Chatting with AINA" button above</p>
          </div>
          <div class="flex items-start gap-3">
            <div class="w-6 h-6 bg-[#f5d142] text-black rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0 mt-0.5">2</div>
            <p>Type your question in the chat input field</p>
          </div>
          <div class="flex items-start gap-3">
            <div class="w-6 h-6 bg-[#f5d142] text-black rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0 mt-0.5">3</div>
            <p>Press Enter or click Send to get an AI response</p>
          </div>
          <div class="flex items-start gap-3">
            <div class="w-6 h-6 bg-[#f5d142] text-black rounded-full flex items-center justify-center text-xs font-bold flex-shrink-0 mt-0.5">4</div>
            <p>View the response in the chat interface</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Chat Modal -->
    <RsChatModal 
      v-model="showChatModal"
      title="AINA Assistant"
      assistant-name="AINA"
      @send-message="handleChatMessage"
    />
  </div>
</template>

<script setup>
definePageMeta({
  title: 'Chat Demo',
  layout: 'default'
});

// Chat modal state
const showChatModal = ref(false);

// Chat modal functions
const openChatModal = () => {
  showChatModal.value = true;
};

const handleChatMessage = (message) => {
  console.log('Chat message received:', message);
  // You can add additional handling here if needed
};
</script>
