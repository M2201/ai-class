<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- THE WIDE OPEN SECURITY FIX -->
    <!-- This allows connections to googleusercontent.com which acts as the redirect handler -->
    <meta http-equiv="Content-Security-Policy" content="default-src * 'unsafe-inline' 'unsafe-eval'; script-src * 'unsafe-inline' 'unsafe-eval'; connect-src * 'unsafe-inline'; img-src * data: blob: 'unsafe-inline'; frame-src *; style-src * 'unsafe-inline';">

    <title>AI Class Registration</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 min-h-screen flex items-center justify-center py-10 px-4">

    <div class="max-w-xl w-full bg-white rounded-xl shadow-2xl overflow-hidden border border-gray-200">
        <div class="bg-blue-700 p-6 text-white text-center">
            <h1 class="text-xl font-bold uppercase tracking-wider">AI Class Registration</h1>
            <p class="text-blue-200 text-sm mt-1">Introductory Workshop</p>
        </div>

        <form id="classForm" class="p-8 space-y-6">
            <!-- 1. Identity -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase">Full Name</label>
                    <input type="text" name="full_name" required class="w-full mt-1 p-3 border rounded-lg bg-gray-50 focus:bg-white focus:ring-2 focus:ring-blue-500 outline-none">
                </div>
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase">Email Address</label>
                    <input type="email" name="email" required class="w-full mt-1 p-3 border rounded-lg bg-gray-50 focus:bg-white focus:ring-2 focus:ring-blue-500 outline-none">
                </div>
            </div>

            <!-- 2. Organization -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase">Company / Organization</label>
                    <input type="text" name="company" class="w-full mt-1 p-3 border rounded-lg bg-gray-50 outline-none">
                </div>
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase">Title & Industry</label>
                    <input type="text" name="role" class="w-full mt-1 p-3 border rounded-lg bg-gray-50 outline-none">
                </div>
            </div>

            <!-- 3. AI Tools -->
            <div>
                <label class="block text-xs font-bold text-gray-500 uppercase mb-2">Which AI tools have you used?</label>
                <input type="text" name="ai_tools" placeholder="ChatGPT, Claude, Gemini, etc." class="w-full p-3 border rounded-lg bg-gray-50 focus:bg-white focus:ring-2 focus:ring-blue-500 outline-none">
            </div>

            <!-- 4. Primary Goal -->
            <div>
                <label class="block text-xs font-bold text-gray-500 uppercase mb-2">What is your primary goal?</label>
                <div class="flex flex-col gap-2">
                    <label class="flex items-center p-3 border rounded-lg hover:bg-blue-50 cursor-pointer transition-colors">
                        <input type="radio" name="motivation" value="Productivity" class="mr-3 text-blue-600">
                        <span class="text-sm">Save time & work faster</span>
                    </label>
                    <label class="flex items-center p-3 border rounded-lg hover:bg-blue-50 cursor-pointer transition-colors">
                        <input type="radio" name="motivation" value="App Building" class="mr-3 text-blue-600">
                        <span class="text-sm">Build apps (Vibe Coding)</span>
                    </label>
                    <label class="flex items-center p-3 border rounded-lg hover:bg-blue-50 cursor-pointer transition-colors">
                        <input type="radio" name="motivation" value="Exploration" class="mr-3 text-blue-600">
                        <span class="text-sm">Understand AI capabilities</span>
                    </label>
                </div>
            </div>

            <!-- 5. Confidence & Background -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase mb-2">How confident are you? (1-5)</label>
                    <select name="tech_comfort" class="w-full p-3 border rounded-lg bg-white">
                        <option value="1">1 - New to this</option>
                        <option value="2">2</option>
                        <option value="3">3 - Comfortable</option>
                        <option value="4">4</option>
                        <option value="5">5 - Very Confident</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-bold text-gray-500 uppercase mb-2">Coding background?</label>
                    <select name="no_code" class="w-full p-3 border rounded-lg bg-white">
                        <option value="None">None</option>
                        <option value="Vibe Coding">Vibe Coding / Low Code</option>
                        <option value="Traditional">Traditional Coding</option>
                    </select>
                </div>
            </div>

            <!-- 6. The Mission -->
            <div>
                <label class="block text-xs font-bold text-gray-500 uppercase mb-2">The Mission (What do you hope to automate?)</label>
                <textarea name="open_response" rows="3" placeholder="Tell us briefly about your goal..." class="w-full p-3 border rounded-lg bg-gray-50 focus:bg-white focus:ring-2 focus:ring-blue-500 outline-none"></textarea>
            </div>

            <!-- Button -->
            <button type="submit" id="submitBtn" class="w-full bg-blue-700 text-white font-bold py-4 rounded-lg hover:bg-blue-800 transition-colors shadow-lg">
                Register Now
            </button>

            <!-- Status Message -->
            <div id="statusMessage" class="hidden p-4 rounded-lg text-center font-bold text-sm mt-4"></div>
        </form>
    </div>

    <script>
        // ------------------------------------------------------------------
        // YOUR NEW URL IS PASTED BELOW:
        // ------------------------------------------------------------------
        const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbx2784ooAKB_OR5h2fvY7uGL0Me41tM54KoHNTdg1tbukn2oNeVCspiJ_dCjXs6_nUNnA/exec";

        const form = document.getElementById('classForm');
        const btn = document.getElementById('submitBtn');
        const msg = document.getElementById('statusMessage');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            btn.disabled = true;
            btn.innerText = "Processing...";
            msg.classList.add('hidden');

            const payload = new FormData(form);
            payload.append('source', 'Web-Form');

            fetch(SCRIPT_URL, {
                method: 'POST',
                mode: 'no-cors',
                body: payload
            })
            .then(() => {
                msg.innerText = "Success! Your data has been sent to the Raw Intake tab.";
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-green-100 text-green-700 block";
                btn.innerText = "Registered!";
            })
            .catch(error => {
                console.error(error);
                msg.innerText = "Error: Check your Internet connection.";
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-red-100 text-red-700 block";
                btn.disabled = false;
                btn.innerText = "Try Again";
            });
        });
    </script>
</body>
</html>
