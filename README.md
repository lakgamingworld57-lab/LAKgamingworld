<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LakGamingWorld - Video Editing Services</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .animate-fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }
        
        .animate-slide-up {
            animation: slideUp 0.5s ease-out;
        }
        
        .animate-stars {
            animation: twinkle 3s infinite;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideUp {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.5); }
        }
        
        .bg-gradient-custom {
            background: linear-gradient(135deg, #3b82f6, #8b5cf6);
        }
        
        .star {
            position: absolute;
            width: 4px;
            height: 4px;
            background-color: #60a5fa;
            border-radius: 50%;
            animation: twinkle 2s infinite;
            animation-delay: calc(var(--delay) * 1s);
        }
    </style>
</head>
<body class="min-h-screen bg-gray-900 text-white overflow-hidden">
    <!-- Animated background stars -->
    <div class="fixed inset-0 overflow-hidden pointer-events-none" id="stars-container"></div>

    <!-- Navigation -->
    <nav class="relative z-10 bg-gray-800 bg-opacity-80 backdrop-blur-md border-b border-blue-500">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2 animate-fade-in">
                <div class="w-8 h-8 bg-blue-500 rounded-lg flex items-center justify-center">
                    <span class="text-white font-bold">L</span>
                </div>
                <h1 class="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-purple-500">
                    LakGamingWorld
                </h1>
            </div>
            
            <div class="flex space-x-4">
                <button onclick="setActiveSection('home')" class="px-3 py-2 rounded-lg transition-all duration-300 bg-blue-600 text-white">
                    Home
                </button>
                <button onclick="setActiveSection('about')" class="px-3 py-2 rounded-lg transition-all duration-300 text-gray-300 hover:text-white hover:bg-gray-700">
                    About
                </button>
                <button onclick="setActiveSection('gallery')" class="px-3 py-2 rounded-lg transition-all duration-300 text-gray-300 hover:text-white hover:bg-gray-700">
                    Gallery
                </button>
                
                <div id="auth-buttons" class="flex space-x-2">
                    <button onclick="showModal('login')" class="px-4 py-2 bg-blue-600 rounded-lg hover:bg-blue-700 transition-colors">
                        Login
                    </button>
                    <button onclick="showModal('signup')" class="px-4 py-2 bg-green-600 rounded-lg hover:bg-green-700 transition-colors">
                        Sign Up
                    </button>
                </div>
                
                <button id="logout-button" class="hidden px-4 py-2 bg-red-600 rounded-lg hover:bg-red-700 transition-colors" onclick="handleLogout()">
                    Logout
                </button>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="relative z-10 container mx-auto px-4 py-8">
        <!-- Home Section -->
        <section id="home-section" class="space-y-12">
            <!-- Hero Section -->
            <div class="text-center py-12 animate-slide-up">
                <h2 class="text-5xl font-bold mb-6">
                    Premium <span class="text-blue-400">Video Editing</span> Services
                </h2>
                <p class="text-xl text-gray-300 max-w-2xl mx-auto mb-8">
                    Transform your raw footage into professional-quality videos with our expert editing team
                </p>
                
                <div id="hero-buttons" class="flex justify-center space-x-4">
                    <button onclick="showModal('signup')" class="px-6 py-3 bg-blue-600 rounded-lg hover:bg-blue-700 transition-colors font-semibold">
                        Get Started
                    </button>
                    <button onclick="setActiveSection('about')" class="px-6 py-3 border border-blue-500 text-blue-400 rounded-lg hover:bg-blue-500 hover:text-white transition-colors">
                        Learn More
                    </button>
                </div>
            </div>

            <!-- Request Form -->
            <div id="request-form" class="hidden max-w-2xl mx-auto bg-gray-800 bg-opacity-50 backdrop-blur-md rounded-xl p-8 border border-blue-500 border-opacity-30">
                <h3 class="text-2xl font-bold mb-6 text-center">Video Editing Request</h3>
                
                <div id="success-message" class="hidden bg-green-500 bg-opacity-20 border border-green-500 text-green-300 p-4 rounded-lg mb-6">
                    Your request has been submitted successfully!
                </div>
                
                <form onsubmit="handleSubmit(event)" class="space-y-4">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-2">Full Name</label>
                            <input
                                type="text"
                                name="name"
                                required
                                class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                            />
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-gray-300 mb-2">Contact Number</label>
                            <input
                                type="tel"
                                name="contact"
                                required
                                class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                            />
                        </div>
                    </div>
                    
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Email Address</label>
                        <input
                            type="email"
                            name="email"
                            required
                            class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                        />
                    </div>
                    
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Address</label>
                        <input
                            type="text"
                            name="address"
                            required
                            class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                        />
                    </div>
                    
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Project Description</label>
                        <textarea
                            name="message"
                            required
                            rows="4"
                            class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                        ></textarea>
                    </div>
                    
                    <button type="submit" class="w-full bg-blue-600 hover:bg-blue-700 py-3 rounded-lg font-semibold transition-colors">
                        Submit Request
                    </button>
                </form>
            </div>
        </section>

        <!-- About Section -->
        <section id="about-section" class="hidden max-w-4xl mx-auto">
            <h2 class="text-3xl font-bold mb-8 text-center">About LakGamingWorld</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="bg-gray-800 bg-opacity-50 backdrop-blur-md rounded-xl p-6 border border-blue-500 border-opacity-30 hover:-translate-y-1 transition-transform">
                    <h3 class="text-xl font-semibold mb-4 text-blue-400">Our Mission</h3>
                    <p class="text-gray-300">
                        At LakGamingWorld, we're passionate about transforming your video content into 
                        professional-grade productions. Founded by Lakshay, our team brings years of 
                        expertise in video editing, motion graphics, and visual storytelling.
                    </p>
                </div>
                
                <div class="bg-gray-800 bg-opacity-50 backdrop-blur-md rounded-xl p-6 border border-blue-500 border-opacity-30 hover:-translate-y-1 transition-transform">
                    <h3 class="text-xl font-semibold mb-4 text-blue-400">Why Choose Us</h3>
                    <ul class="text-gray-300 space-y-2">
                        <li>• Premium quality editing with fast turnaround</li>
                        <li>• Secure data handling and confidentiality</li>
                        <li>• Custom solutions for gaming content</li>
                        <li>• Professional color grading and audio enhancement</li>
                    </ul>
                </div>
                
                <div class="bg-gray-800 bg-opacity-50 backdrop-blur-md rounded-xl p-6 border border-blue-500 border-opacity-30 md:col-span-2 hover:-translate-y-1 transition-transform">
                    <h3 class="text-xl font-semibold mb-4 text-blue-400">Security & Privacy</h3>
                    <p class="text-gray-300">
                        Your data security is our top priority. We use advanced encryption methods to protect 
                        your personal information and video content. All requests are stored securely, and we 
                        never share your data with third parties.
                    </p>
                </div>
            </div>
        </section>

        <!-- Gallery Section -->
        <section id="gallery-section" class="hidden">
            <h2 class="text-3xl font-bold mb-8 text-center">Our Work</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="bg-gray-800 rounded-xl overflow-hidden border border-blue-500 border-opacity-30 hover:scale-103 transition-transform">
                    <div class="h-48 bg-gradient-to-br from-blue-600 to-purple-600 flex items-center justify-center">
                        <span class="text-white font-bold">Gaming Montage</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold mb-2">Action-Packed Gameplay</h3>
                        <p class="text-gray-400 text-sm">Dynamic editing with seamless transitions</p>
                    </div>
                </div>
                
                <div class="bg-gray-800 rounded-xl overflow-hidden border border-blue-500 border-opacity-30 hover:scale-103 transition-transform">
                    <div class="h-48 bg-gradient-to-br from-purple-600 to-pink-600 flex items-center justify-center">
                        <span class="text-white font-bold">Vlog Editing</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold mb-2">Travel Vlog Series</h3>
                        <p class="text-gray-400 text-sm">Engaging storytelling with beautiful visuals</p>
                    </div>
                </div>
                
                <div class="bg-gray-800 rounded-xl overflow-hidden border border-blue-500 border-opacity-30 hover:scale-103 transition-transform">
                    <div class="h-48 bg-gradient-to-br from-green-600 to-blue-600 flex items-center justify-center">
                        <span class="text-white font-bold">Product Review</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold mb-2">Tech Product Showcase</h3>
                        <p class="text-gray-400 text-sm">Professional presentation with clear messaging</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Login Modal -->
    <div id="login-modal" class="fixed inset-0 bg-black bg-opacity-70 hidden items-center justify-center z-50">
        <div class="bg-gray-800 rounded-xl p-8 w-full max-w-md border border-blue-500">
            <h3 class="text-2xl font-bold mb-6 text-center">Login</h3>
            <form onsubmit="handleLogin(event)" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Email</label>
                    <input
                        type="email"
                        name="email"
                        required
                        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                    />
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Password</label>
                    <input
                        type="password"
                        name="password"
                        required
                        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                    />
                </div>
                <div class="flex space-x-4 pt-4">
                    <button type="submit" class="flex-1 bg-blue-600 hover:bg-blue-700 py-2 rounded-lg font-semibold transition-colors">
                        Login
                    </button>
                    <button type="button" onclick="hideModal('login')" class="flex-1 bg-gray-600 hover:bg-gray-700 py-2 rounded-lg font-semibold transition-colors">
                        Cancel
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Signup Modal -->
    <div id="signup-modal" class="fixed inset-0 bg-black bg-opacity-70 hidden items-center justify-center z-50">
        <div class="bg-gray-800 rounded-xl p-8 w-full max-w-md border border-blue-500">
            <h3 class="text-2xl font-bold mb-6 text-center">Create Account</h3>
            <form onsubmit="handleSignup(event)" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Email</label>
                    <input
                        type="email"
                        name="email"
                        required
                        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                    />
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Password</label>
                    <input
                        type="password"
                        name="password"
                        required
                        class="w-full bg-gray-700 border border-gray-600 rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                    />
                </div>
                <div class="flex space-x-4 pt-4">
                    <button type="submit" class="flex-1 bg-green-600 hover:bg-green-700 py-2 rounded-lg font-semibold transition-colors">
                        Sign Up
                    </button>
                    <button type="button" onclick="hideModal('signup')" class="flex-1 bg-gray-600 hover:bg-gray-700 py-2 rounded-lg font-semibold transition-colors">
                        Cancel
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Footer -->
    <footer class="relative z-10 bg-gray-800 bg-opacity-80 backdrop-blur-md border-t border-blue-500 mt-12">
        <div class="container mx-auto px-4 py-8 text-center">
            <p class="text-gray-400">© 2023 LakGamingWorld. All rights reserved.</p>
            <p class="text-gray-500 text-sm mt-2">Secure video editing services by Lakshay</p>
        </div>
    </footer>

    <script>
        // State management
        let isLoggedIn = false;
        let activeSection = 'home';
        let requests = [];

        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            createStars();
            checkLoggedInStatus();
            loadRequests();
            setActiveSection('home');
        });

        // Create animated stars
        function createStars() {
            const container = document.getElementById('stars-container');
            for (let i = 0; i < 20; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = `${Math.random() * 100}%`;
                star.style.top = `${Math.random() * 100}%`;
                star.style.setProperty('--delay', Math.random() * 2);
                container.appendChild(star);
            }
        }

        // Check if user is logged in
        function checkLoggedInStatus() {
            const savedUser = localStorage.getItem('videoEditUser');
            if (savedUser) {
                isLoggedIn = true;
                updateUIForLoggedIn();
            }
        }

        // Load saved requests
        function loadRequests() {
            const savedRequests = localStorage.getItem('videoEditRequests');
            if (savedRequests) {
                requests = JSON.parse(savedRequests);
            }
        }

        // Update UI for logged in state
        function updateUIForLoggedIn() {
            document.getElementById('auth-buttons').classList.add('hidden');
            document.getElementById('logout-button').classList.remove('hidden');
            document.getElementById('hero-buttons').classList.add('hidden');
            document.getElementById('request-form').classList.remove('hidden');
        }

        // Update UI for logged out state
        function updateUIForLoggedOut() {
            document.getElementById('auth-buttons').classList.remove('hidden');
            document.getElementById('logout-button').classList.add('hidden');
            document.getElementById('hero-buttons').classList.remove('hidden');
            document.getElementById('request-form').classList.add('hidden');
        }

        // Set active section
        function setActiveSection(section) {
            activeSection = section;
            
            // Hide all sections
            document.getElementById('home-section').classList.add('hidden');
            document.getElementById('about-section').classList.add('hidden');
            document.getElementById('gallery-section').classList.add('hidden');
            
            // Show active section
            document.getElementById(section + '-section').classList.remove('hidden');
            
            // Update navigation buttons
            const buttons = document.querySelectorAll('nav button');
            buttons.forEach(btn => {
                if (btn.textContent.toLowerCase().includes(section)) {
                    btn.classList.add('bg-blue-600', 'text-white');
                    btn.classList.remove('text-gray-300', 'hover:text-white', 'hover:bg-gray-700');
                } else if (!btn.id) {
                    btn.classList.remove('bg-blue-600', 'text-white');
                    btn.classList.add('text-gray-300', 'hover:text-white', 'hover:bg-gray-700');
                }
            });
        }

        // Show modal
        function showModal(type) {
            document.getElementById(type + '-modal').classList.remove('hidden');
            document.getElementById(type + '-modal').classList.add('flex');
        }

        // Hide modal
        function hideModal(type) {
            document.getElementById(type + '-modal').classList.add('hidden');
            document.getElementById(type + '-modal').classList.remove('flex');
        }

        // Handle signup
        function handleSignup(event) {
            event.preventDefault();
            const formData = new FormData(event.target);
            const email = formData.get('email');
            const password = formData.get('password');
            
            if (email && password) {
                localStorage.setItem('videoEditUser', JSON.stringify({ email, password }));
                isLoggedIn = true;
                updateUIForLoggedIn();
                hideModal('signup');
                event.target.reset();
            }
        }

        // Handle login
        function handleLogin(event) {
            event.preventDefault();
            const formData = new FormData(event.target);
            const email = formData.get('email');
            const password = formData.get('password');
            
            const savedUser = localStorage.getItem('videoEditUser');
            if (savedUser) {
                const user = JSON.parse(savedUser);
                if (user.email === email && user.password === password) {
                    isLoggedIn = true;
                    updateUIForLoggedIn();
                    hideModal('login');
                    event.target.reset();
                }
            }
        }

        // Handle logout
        function handleLogout() {
            localStorage.removeItem('videoEditUser');
            isLoggedIn = false;
            updateUIForLoggedOut();
        }

        // Handle form submission
        function handleSubmit(event) {
            event.preventDefault();
            const formData = new FormData(event.target);
            const request = {
                name: formData.get('name'),
                address: formData.get('address'),
                email: formData.get('email'),
                message: formData.get('message'),
                contact: formData.get('contact'),
                id: Date.now(),
                date: new Date().toLocaleDateString()
            };
            
            requests.push(request);
            localStorage.setItem('videoEditRequests', JSON.stringify(requests));
            
            // Show success message
            const successMessage = document.getElementById('success-message');
            successMessage.classList.remove('hidden');
            setTimeout(() => {
                successMessage.classList.add('hidden');
            }, 3000);
            
            // Reset form
            event.target.reset();
        }
    </script>
</body>
</html>
