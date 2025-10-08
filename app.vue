<script setup>
useHead({
  title: "Kerisi AI Assistant",
  description: "Home page",
  htmlAttrs: {
    lang: "en",
  },
  script: [
    {
      type: "module",
      innerHTML: `
        import Chatbot from 'https://cdn.jsdelivr.net/npm/flowise-embed/dist/web.js';
        Chatbot.init({
          chatflowid: 'your-chatflowid-here',
          apiHost: 'your-apihost-here',
          theme: {
            button: {
              backgroundColor: '#f5d142',
              right: 20,
              bottom: 20,
              size: 90, // small | medium | large | number
              dragAndDrop: true,
              iconColor: 'white',
              customIconSrc: '/img/avatar_kerisi.png',
              autoWindowOpen: {
                autoOpen: true, //parameter to control automatic window opening
                openDelay: 2, // Optional parameter for delay time in seconds
                autoOpenOnMobile: false, //parameter to control automatic window opening in mobile
              },
            },
            tooltip: {
              showTooltip: true,
              tooltipMessage: '',
              tooltipBackgroundColor: 'transparent',
              tooltipTextColor: 'white',
              tooltipFontSize: 16,
            },
            disclaimer: {
              title: 'Disclaimer',
              message: 'By using this chatbot, you agree to the <a target="_blank" href="https://flowiseai.com/terms">Terms & Condition</a>',
              textColor: 'black',
              buttonColor: '#3b82f6',
              buttonText: 'Start Chatting',
              buttonTextColor: 'white',
              blurredBackgroundColor: 'rgba(0, 0, 0, 0.4)', //The color of the blurred background that overlays the chat interface
              backgroundColor: 'white',
            },
            customCSS: \`\`, // Add custom CSS styles. Use !important to override default styles
            chatWindow: {
              showTitle: true,
              showAgentMessages: true,
              title: 'AINA',
              titleAvatarSrc: '/img/avatar_kerisi.png',
              titleBackgroundColor: '#f5d142',
              welcomeMessage: 'Hi! Im AINA, your Accounting & Navigation Intelligence Assistant. How can I help you today?',
              errorMessage: 'Oops! Something went wrong. Please try again.',
              backgroundColor: '#ffffff',
              backgroundImage: 'enter image path or link', // If set, this will overlap the background color of the chat window.
              height: 700,
              width: 400,
              fontSize: 16,
              starterPrompts: ['What is a bot?', 'Who are you?'], // It overrides the starter prompts set by the chat flow passed
              starterPromptFontSize: 15,
              clearChatOnReload: false, // If set to true, the chat will be cleared when the page reloads
              sourceDocsTitle: 'Sources:',
              renderHTML: true,
              botMessage: {
                backgroundColor: '#f7f8ff',
                textColor: '#303235',
                showAvatar: true,
                avatarSrc: '/img/avatar_kerisi.png',
              },
              userMessage: {
                backgroundColor: '#3B81F6',
                textColor: '#ffffff',
                showAvatar: true,
                avatarSrc: 'https://raw.githubusercontent.com/zahidkhawaja/langchain-chat-nextjs/main/public/usericon.png',
              },
              textInput: {
                placeholder: 'Type your question',
                backgroundColor: '#ffffff',
                textColor: '#303235',
                sendButtonColor: '#3B81F6',
                maxChars: 50,
                maxCharsWarningMessage: 'You exceeded the characters limit. Please input less than 50 characters.',
                autoFocus: true, // If not used, autofocus is disabled on mobile and enabled on desktop. true enables it on both, false disables it on both.
                sendMessageSound: true,
                // sendSoundLocation: "send_message.mp3", // If this is not used, the default sound effect will be played if sendSoundMessage is true.
                receiveMessageSound: true,
                // receiveSoundLocation: "receive_message.mp3", // If this is not used, the default sound effect will be played if receiveSoundMessage is true.
              },
              feedback: {
                color: '#303235',
              },
              dateTimeToggle: {
                date: true,
                time: true,
              },
              footer: {
                textColor: '#303235',
                text: 'Powered by',
                company: 'Flowise',
                companyLink: 'https://flowiseai.com',
              },
            },
          },
        });
      `
    }
  ]
});

const loading = ref(true);

onMounted(() => {
  // Hide loading indicator if not hydrating
  setTimeout(() => {
    loading.value = false;
  }, 1000);

  // Get theme from localStorage
  let theme = localStorage.getItem("theme") || "default";
  document.documentElement.setAttribute("data-theme", theme);
});
</script>

<template>
  <div>
    <NuxtLoadingIndicator />
    <NuxtLayout>
      <Loading v-if="loading" />
      <NuxtPage :key="$route.fullPath" v-else />
    </NuxtLayout>
  </div>
</template>
