# panel-key
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>API Anahtar Yönetim Paneli</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"></link>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
</head>
<body class="bg-gradient-to-r from-blue-500 to-purple-600 font-roboto min-h-screen flex items-center justify-center">
    <div class="container mx-auto p-4">
        <!-- Authentication Section -->
        <div id="auth-section" class="bg-white shadow-lg rounded-lg p-6 mb-6 max-w-md mx-auto">
            <h1 class="text-3xl font-bold mb-4 text-center text-blue-600">Giriş Yap</h1>
            <div class="mb-4">
                <label for="loginEmail" class="block text-sm font-medium text-gray-700">E-posta</label>
                <input type="email" id="loginEmail" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="E-posta adresinizi girin">
            </div>
            <div class="mb-4">
                <label for="loginPassword" class="block text-sm font-medium text-gray-700">Şifre</label>
                <input type="password" id="loginPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Şifrenizi girin">
            </div>
            <div class="flex justify-end">
                <button onclick="login()" class="bg-blue-600 text-white px-4 py-2 rounded-md shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
                    Giriş Yap
                </button>
            </div>
            <div class="mt-4 text-sm text-center">
                <span>Hesabınız yok mu? </span>
                <button onclick="showSignup()" class="text-blue-600 hover:underline">Kayıt Ol</button>
            </div>
        </div>

        <div id="signup-section" class="bg-white shadow-lg rounded-lg p-6 mb-6 max-w-md mx-auto hidden">
            <h1 class="text-3xl font-bold mb-4 text-center text-green-600">Kayıt Ol</h1>
            <div class="mb-4">
                <label for="signupEmail" class="block text-sm font-medium text-gray-700">E-posta</label>
                <input type="email" id="signupEmail" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="E-posta adresinizi girin">
            </div>
            <div class="mb-4">
                <label for="signupPassword" class="block text-sm font-medium text-gray-700">Şifre</label>
                <input type="password" id="signupPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="Şifrenizi girin">
            </div>
            <div class="mb-4">
                <label for="signupConfirmPassword" class="block text-sm font-medium text-gray-700">Şifreyi Onayla</label>
                <input type="password" id="signupConfirmPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="Şifrenizi onaylayın">
            </div>
            <div class="flex justify-end">
                <button onclick="signup()" class="bg-green-600 text-white px-4 py-2 rounded-md shadow-sm hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                    Kayıt Ol
                </button>
            </div>
            <div class="mt-4 text-sm text-center">
                <span>Zaten hesabınız var mı? </span>
                <button onclick="showLogin()" class="text-green-600 hover:underline">Giriş Yap</button>
            </div>
        </div>

        <!-- Main Dashboard Section -->
        <div id="dashboard-section" class="hidden">
            <div class="flex">
                <!-- Sidebar -->
                <div class="w-1/4 bg-white shadow-lg rounded-lg p-6">
                    <h2 class="text-xl font-bold mb-4 text-blue-600">Menü</h2>
                    <ul class="space-y-4">
                        <li>
                            <button onclick="showKeyCreationSection()" class="w-full text-left text-gray-700 hover:text-blue-500">Anahtar Oluşturma</button>
                        </li>
                    </ul>
                </div>

                <!-- Content Area -->
                <div class="w-3/4 ml-4">
                    <!-- Key Creation Section -->
                    <div id="key-creation-section" class="bg-white shadow-lg rounded-lg p-6 hidden">
                        <h1 class="text-2xl font-bold mb-4 text-blue-600">Anahtar Oluşturma</h1>
                        <div class="mb-4">
                            <label for="keyDuration" class="block text-sm font-medium text-gray-700">Anahtar Süresi (Gün)</label>
                            <select id="keyDuration" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                                <option value="15">15 Gün</option>
                                <option value="30">30 Gün</option>
                                <option value="60">60 Gün</option>
                            </select>
                        </div>
                        <div class="mb-4">
                            <label for="keyUsers" class="block text-sm font-medium text-gray-700">Kullanıcı Sayısı</label>
                            <input type="number" id="keyUsers" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Kaç kullanıcı girebilir">
                        </div>
                        <div class="flex justify-end">
                            <button onclick="generateApiKey()" class="bg-green-600 text-white px-4 py-2 rounded-md shadow-sm hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                                Rastgele Anahtar Oluştur
                            </button>
                        </div>
                    </div>
                    <div id="api-keys-list" class="bg-white shadow-lg rounded-lg p-6 mt-6 hidden">
                        <h2 class="text-xl font-bold mb-4 text-blue-600">Oluşturulan Anahtarlar</h2>
                        <ul id="apiKeys" class="space-y-4">
                            <!-- API keys will be dynamically added here -->
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        function showSignup() {
            document.getElementById('auth-section').classList.add('hidden');
            document.getElementById('signup-section').classList.remove('hidden');
        }

        function showLogin() {
            document.getElementById('signup-section').classList.add('hidden');
            document.getElementById('auth-section').classList.remove('hidden');
        }

        function login() {
            // Simulate login process
            document.getElementById('auth-section').classList.add('hidden');
            document.getElementById('dashboard-section').classList.remove('hidden');
            showKeyCreationSection();
        }

        function signup() {
            // Simulate signup process
            document.getElementById('signup-section').classList.add('hidden');
            document.getElementById('auth-section').classList.remove('hidden');
        }

        function showKeyCreationSection() {
            document.getElementById('key-creation-section').classList.remove('hidden');
            document.getElementById('api-keys-list').classList.remove('hidden');
        }

        function saveApiKey(apiKey, duration, users) {
            const apiKeysList = document.getElementById('apiKeys');
            const li = document.createElement('li');
            li.className = 'flex items-center justify-between p-4 bg-gray-50 rounded-md shadow-sm';
            li.innerHTML = `
                <span class="text-gray-700">${apiKey} - ${duration} Gün - ${users} Kullanıcı</span>
                <button class="text-red-500 hover:text-red-700 focus:outline-none" onclick="deleteApiKey(this)">
                    <i class="fas fa-trash-alt"></i>
                </button>
            `;
            apiKeysList.appendChild(li);
        }

        function deleteApiKey(button) {
            const li = button.parentElement;
            li.remove();
        }

        function generateApiKey() {
            const duration = document.getElementById('keyDuration').value;
            const users = document.getElementById('keyUsers').value;
            const apiKey = 'API-' + Math.random().toString(36).substr(2, 16).toUpperCase();
            saveApiKey(apiKey, duration, users);
            saveToLocalStorage(apiKey, duration, users);
        }

        function saveToLocalStorage(apiKey, duration, users) {
            const apiKeys = JSON.parse(localStorage.getItem('apiKeys')) || [];
            apiKeys.push({ apiKey, duration, users });
            localStorage.setItem('apiKeys', JSON.stringify(apiKeys));
        }

        function loadFromLocalStorage() {
            const apiKeys = JSON.parse(localStorage.getItem('apiKeys')) || [];
            apiKeys.forEach(({ apiKey, duration, users }) => {
                saveApiKey(apiKey, duration, users);
            });
        }

        window.onload = function() {
            loadFromLocalStorage();
        }
    </script>
</body>
</html>
