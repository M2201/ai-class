<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Class Registration</title>
    <!-- Load Tailwind CSS for styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Load Inter font for professional look -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #f3f4f6; }
        .glass-panel { background: white; border: 1px solid #e5e7eb; }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center py-10 px-4">

    <div class="max-w-xl w-full glass-panel rounded-2xl shadow-xl overflow-hidden">
        <!-- Header -->
        <div class="bg-indigo-600 p-8 text-center">
            <h1 class="text-2xl font-extrabold text-white uppercase tracking-wider">AI Class Registration</h1>
            <p class="text-indigo-200 text-sm mt-2 font-medium">Introductory Workshop & Application</p>
        </div>

        <form id="classForm" class="p-8 space-y-8">
            
            <!-- Section 1: Identity -->
            <div class="space-y-4">
                <h3 class="text-xs font-bold text-gray-400 uppercase tracking-widest border-b pb-2">01. Identity</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">Full Name</label>
                        <input type="text" name="full_name" required placeholder="Jane Doe" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">Email Address</label>
                        <input type="email" name="email" required placeholder="name@email.com" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                    </div>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">Company</label>
                        <input type="text" name="company" placeholder="Acme Corp" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-1">Title / Industry</label>
                        <input type="text" name="role" placeholder="Marketing Director" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                    </div>
                </div>
            </div>

            <!-- Section 2: Experience -->
            <div class="space-y-4">
                <h3 class="text-xs font-bold text-gray-400 uppercase tracking-widest border-b pb-2">02. Experience</h3>
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-2">Which AI tools have you used?</label>
                    <input type="text" name="ai_tools" placeholder="ChatGPT, Claude, Midjourney..." class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-2">Confidence (1-5)</label>
                        <select name="tech_comfort" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none">
                            <option value="1">1 - New to this</option>
                            <option value="2">2 - Beginner</option>
                            <option value="3">3 - Comfortable</option>
                            <option value="4">4 - Advanced</option>
                            <option value="5">5 - Very Confident</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-gray-700 mb-2">Coding Background</label>
                        <select name="no_code" class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none">
                            <option value="None">None</option>
                            <option value="Vibe Coding">Vibe Coding / Low Code</option>
                            <option value="Traditional">Traditional Coding</option>
                        </select>
                    </div>
                </div>
            </div>

            <!-- Section 3: Goals -->
            <div class="space-y-4">
                <h3 class="text-xs font-bold text-gray-400 uppercase tracking-widest border-b pb-2">03. Goals</h3>
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-3">Primary Goal</label>
                    <div class="space-y-3">
                        <label class="flex items-center p-3 border border-gray-200 rounded-lg hover:bg-indigo-50 hover:border-indigo-200 cursor-pointer transition-all">
                            <input type="radio" name="motivation" value="Productivity" class="w-4 h-4 text-indigo-600 focus:ring-indigo-500">
                            <span class="ml-3 text-sm text-gray-600">Save time & work faster (Productivity)</span>
                        </label>
                        <label class="flex items-center p-3 border border-gray-200 rounded-lg hover:bg-indigo-50 hover:border-indigo-200 cursor-pointer transition-all">
                            <input type="radio" name="motivation" value="App Building" class="w-4 h-4 text-indigo-600 focus:ring-indigo-500">
                            <span class="ml-3 text-sm text-gray-600">Build apps & tools (Vibe Coding)</span>
                        </label>
                        <label class="flex items-center p-3 border border-gray-200 rounded-lg hover:bg-indigo-50 hover:border-indigo-200 cursor-pointer transition-all">
                            <input type="radio" name="motivation" value="Exploration" class="w-4 h-4 text-indigo-600 focus:ring-indigo-500">
                            <span class="ml-3 text-sm text-gray-600">Understand capabilities (The "Ins & Outs")</span>
                        </label>
                    </div>
                </div>
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-2">The Mission (What do you hope to automate?)</label>
                    <textarea name="open_response" rows="3" placeholder="Tell us briefly about your goal..." class="w-full p-3 bg-gray-50 border border-gray-200 rounded-lg focus:bg-white focus:ring-2 focus:ring-indigo-500 outline-none transition-all"></textarea>
                </div>
            </div>

            <!-- Submit Button -->
            <button type="submit" id="submitBtn" class="w-full bg-indigo-600 text-white font-bold py-4 rounded-xl hover:bg-indigo-700 transition-all shadow-lg transform active:scale-95">
                Register for Class
            </button>

            <!-- Status Messages -->
            <div id="statusMessage" class="hidden p-4 rounded-lg text-center font-bold text-sm mt-4"></div>
            
            <p class="text-center text-xs text-gray-400 mt-6">Powered by AI & Vibe Coding</p>
        </form>
    </div>

    <script>
        // =================================================================
        // YOUR GOOGLE WEB APP URL
        // =================================================================
        const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbx2784ooAKB_OR5h2fvY7uGL0Me41tM54KoHNTdg1tbukn2oNeVCspiJ_dCjXs6_nUNnA/exec";

        const form = document.getElementById('classForm');
        const btn = document.getElementById('submitBtn');
        const msg = document.getElementById('statusMessage');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            btn.disabled = true;
            btn.innerText = "Connecting to Database...";
            msg.classList.add('hidden');

            const payload = new FormData(form);
            payload.append('source', 'Web-Form-Final');

            fetch(SCRIPT_URL, {
                method: 'POST',
                mode: 'no-cors',
                body: payload
            })
            .then(() => {
                msg.innerText = "Success! Your registration is confirmed. Please check your email.";
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-green-50 text-green-700 border border-green-200 block";
                btn.innerText = "Registered!";
            })
            .catch(error => {
                console.error(error);
                msg.innerText = "Connection Error. Please try again.";
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-red-50 text-red-700 border border-red-200 block";
                btn.disabled = false;
                btn.innerText = "Try Again";
            });
        });
    </script>
</body>
</html>


