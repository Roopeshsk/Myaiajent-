<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>X Gen - All-in-One AI</title>
    <!-- Tailwind CSS (CDN) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/dompurify/3.0.5/purify.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;500;700&display=swap" rel="stylesheet">
    
    <style>
        :root { --accent: #00f2ff; --bg-dark: #050505; }
        body { background-color: var(--bg-dark); font-family: 'Outfit', sans-serif; color: #fff; min-height: 100dvh; }
        .glass { background: rgba(30, 30, 35, 0.7); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1); }
        .markdown-body { font-size: 1rem; line-height: 1.6; }
        .markdown-body pre { background: #1e1e1e; padding: 1rem; border-radius: 0.5rem; overflow-x: auto; margin: 10px 0; }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-thumb { background: #475569; border-radius: 4px; }
        .spinner { border: 4px solid rgba(255,255,255,0.1); width: 40px; height: 40px; border-radius: 50%; border-top: 4px solid var(--accent); animation: spin 1s linear infinite; }
        @keyframes spin { 100% { transform: rotate(360deg); } }
        .tab-btn.active { border-bottom: 2px solid var(--accent); color: var(--accent); }
    </style>
</head>
<body class="flex flex-col h-[100dvh]">

    <!-- Header -->
    <header class="p-4 border-b border-white/10 flex flex-col items-center glass sticky top-0 z-50">
        <h1 class="text-2xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-white to-cyan-400 mb-4">X GEN AI</h1>
        <div class="flex gap-4">
            <button onclick="switchMode('chat')" id="chatTab" class="tab-btn active px-4 py-2 font-medium">Chat</button>
            <button onclick="switchMode('image')" id="imageTab" class="tab-btn px-4 py-2 font-medium">Image</button>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-1 overflow-hidden flex flex-col max-w-3xl mx-auto w-full">
        
        <!-- CHAT AREA -->
        <div id="chatView" class="flex-1 flex flex-col overflow-hidden">
            <div id="chatMessages" class="flex-1 overflow-y-auto p-4 space-y-4"></div>
            <div class="p-4 glass rounded-t-2xl">
                <div class="flex gap-2">
                    <textarea id="chatInput" rows="1" class="flex-1 bg-white/5 border border-white/10 rounded-xl p-3 outline-none focus:border-cyan-400" placeholder="Ask anything..."></textarea>
                    <button onclick="sendChat()" class="bg-cyan-500 text-black px-6 rounded-xl font-bold hover:bg-cyan-400">Send</button>
                </div>
                <button onclick="openSettings()" class="text-xs text-gray-500 mt-2 hover:text-white">Settings (API Keys)</button>
            </div>
        </div>

        <!-- IMAGE AREA -->
        <div id="imageView" class="flex-1 overflow-y-auto p-4 hidden">
            <div class="glass p-6 rounded-2xl">
                <textarea id="imgPrompt" rows="3" class="w-full bg-white/5 border border-white/10 rounded-xl p-4 outline-none mb-4" placeholder="Describe your image..."></textarea>
                <div class="flex gap-2">
                    <select id="ratio" class="bg-black/50 border border-white/10 rounded-lg p-2 flex-1">
                        <option value="1:1">Square</option>
                        <option value="16:9">Wide</option>
                    </select>
                    <button onclick="generateImage()" class="bg-cyan-500 text-black px-6 rounded-lg font-bold flex-[2]">Generate ✨</button>
                </div>
            </div>
            <div class="result-area mt-8 flex flex-col items-center">
                <div id="imgLoader" class="spinner hidden mb-4"></div>
                <img id="resultImage" class="w-full rounded-2xl border border-white/10 hidden">
            </div>
        </div>
    </main>

    <!-- Settings Modal -->
    <div id="settings" class="fixed inset-0 bg-black/80 z-[100] hidden flex items-center justify-center p-4">
        <div class="glass p-6 rounded-2xl w-full max-w-sm">
            <h2 class="text-lg font-bold mb-4">API Settings</h2>
            
            <label class="block text-xs text-gray-400 mb-1">Chat API Key (OpenRouter)</label>
            <input type="password" id="chatApiKey" placeholder="sk-or-v1-..." class="w-full bg-white/5 p-3 rounded-lg mb-4 border border-white/10">
            
            <label class="block text-xs text-gray-400 mb-1">Image API Key (Optional)</label>
            <input type="password" id="imgApiKey" placeholder="Enter key if required" class="w-full bg-white/5 p-3 rounded-lg mb-6 border border-white/10">
            
            <button onclick="saveSettings()" class="w-full bg-cyan-500 text-black py-2 rounded-lg font-bold">Save & Close</button>
        </div>
    </div>

    <script>
        // --- Shared State ---
        let config = { 
            chatKey: localStorage.getItem('chat_key') || '',
            imgKey: localStorage.getItem('img_key') || ''
        };

        function switchMode(mode) {
            document.getElementById('chatView').classList.toggle('hidden', mode !== 'chat');
            document.getElementById('imageView').classList.toggle('hidden', mode !== 'image');
            document.getElementById('chatTab').classList.toggle('active', mode === 'chat');
            document.getElementById('imageTab').classList.toggle('active', mode === 'image');
        }

        function openSettings() { 
            document.getElementById('chatApiKey').value = config.chatKey;
            document.getElementById('imgApiKey').value = config.imgKey;
            document.getElementById('settings').classList.remove('hidden'); 
        }

        function saveSettings() { 
            config.chatKey = document.getElementById('chatApiKey').value;
            config.imgKey = document.getElementById('imgApiKey').value;
            localStorage.setItem('chat_key', config.chatKey);
            localStorage.setItem('img_key', config.imgKey);
            document.getElementById('settings').classList.add('hidden');
        }

        // --- IMAGE LOGIC ---
        async function generateImage() {
            const prompt = document.getElementById('imgPrompt').value;
            if(!prompt) return alert("Enter a prompt!");
            const loader = document.getElementById('imgLoader');
            const img = document.getElementById('resultImage');
            
            loader.classList.remove('hidden');
            img.classList.add('hidden');
            
            // Note: If you use a custom key for images, you might need to add it to headers.
            // For now, it builds the standard URL.
            const url = `https://image.pollinations.ai/prompt/${encodeURIComponent(prompt)}?nologo=true&seed=${Math.random()}`;
            img.src = url;
            img.onload = () => { loader.classList.add('hidden'); img.classList.remove('hidden'); };
        }

        // --- CHAT LOGIC ---
        async function sendChat() {
            const input = document.getElementById('chatInput');
            const msgBox = document.getElementById('chatMessages');
            if(!config.chatKey) return alert("Please set Chat API Key in settings!");
            
            const userText = input.value;
            if(!userText) return;
            
            msgBox.innerHTML += `<div class="p-3 bg-white/10 rounded-xl self-end max-w-[80%]">${userText}</div>`;
            input.value = '';
            
            const aiId = 'ai-' + Date.now();
            msgBox.innerHTML += `<div id="${aiId}" class="p-3 bg-cyan-900/30 rounded-xl max-w-[80%]">Thinking...</div>`;

            try {
                const response = await fetch('https://openrouter.ai/api/v1/chat/completions', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json', 'Authorization': `Bearer ${config.chatKey}` },
                    body: JSON.stringify({
                        model: "deepseek/deepseek-r1:free",
                        messages: [{ role: 'user', content: userText }]
                    })
                });
                const data = await response.json();
                document.getElementById(aiId).innerHTML = DOMPurify.sanitize(marked.parse(data.choices[0].message.content));
            } catch (e) {
                document.getElementById(aiId).innerText = "Error: " + e.message;
            }
        }
    </script>
</body>
</html>
