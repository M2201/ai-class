<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- WIDE OPEN SECURITY FOR FACEBOOK COMPATIBILITY -->
    <meta http-equiv="Content-Security-Policy" content="default-src * 'unsafe-inline' 'unsafe-eval'; script-src * 'unsafe-inline' 'unsafe-eval'; connect-src * 'unsafe-inline'; img-src * data: blob: 'unsafe-inline'; frame-src *; style-src * 'unsafe-inline';">
    <title>AI Class Registration</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col items-center py-10 px-4">

    <!-- FACEBOOK WARNING BANNER (Hidden by default) -->
    <div id="fb-warning" class="hidden w-full max-w-xl mb-6 bg-yellow-100 border-l-4 border-yellow-500 text-yellow-700 p-4 rounded shadow-md" role="alert">
        <p class="font-bold">⚠️ Facebook Browser Detected</p>
        <p>For the registration to work correctly, please tap the <span class="font-bold">•••</span> menu at the top or bottom right and select <span class="font-bold">"Open in Browser"</span> (Safari/Chrome).</p>
    </div>

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
      // Wrap in IIFE to prevent variable redeclaration errors in some environments
      (function() {
        // ==================================================================
        // URL CONFIGURATION
        // ==================================================================
        const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbx2784ooAKB_OR5h2fvY7uGL0Me41tM54KoHNTdg1tbukn2oNeVCspiJ_dCjXs6_nUNnA/exec";

        // ==================================================================
        // FACEBOOK / INSTAGRAM DETECTION
        // ==================================================================
        const ua = navigator.userAgent || navigator.vendor || window.opera;
        const isFacebook = (ua.indexOf("FBAN") > -1) || (ua.indexOf("FBAV") > -1) || (ua.indexOf("Instagram") > -1);
        
        if (isFacebook) {
            document.getElementById('fb-warning').classList.remove('hidden');
        }

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
                msg.innerText = "Success! Your registration is complete. Check your email.";
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-green-100 text-green-700 block";
                btn.innerText = "Registered!";
            })
            .catch(error => {
                console.error(error);
                // If it fails on Facebook, give a specific instruction
                if (isFacebook) {
                    msg.innerText = "Registration blocked by Facebook Browser. Please tap ••• above and 'Open in Browser'.";
                } else {
                    msg.innerText = "Error: Check your Internet connection.";
                }
                msg.className = "p-4 rounded-lg text-center font-bold text-sm mt-4 bg-red-100 text-red-700 block";
                btn.disabled = false;
                btn.innerText = "Try Again";
            });
        });
      })();
    </script>
</body>
</html>
