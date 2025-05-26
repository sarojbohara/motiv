<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ZenMotiv - Daily Motivation Quotes</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #6366f1;
            --secondary: #f59e0b;
            --dark: #1e293b;
            --light: #f8fafc;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--dark);
            color: var(--light);
            overflow-x: hidden;
        }
        
        .quote-font {
            font-family: 'Playfair Display', serif;
        }
        
        @keyframes fadeIn {
            0% { opacity: 0; transform: translateY(20px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        @keyframes progress {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .animate-fadeIn {
            animation: fadeIn 0.8s ease-out forwards;
        }
        
        .animate-float {
            animation: float 6s ease-in-out infinite;
        }
        
        .animate-pulse {
            animation: pulse 2s ease-in-out infinite;
        }
        
        .gradient-bg {
            background: linear-gradient(-45deg, #6366f1, #8b5cf6, #ec4899, #f59e0b);
            background-size: 300% 300%;
            animation: gradientBG 15s ease infinite;
        }
        
        .glass-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
        }
        
        .progress-bar {
            height: 6px;
            background: rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
            border-radius: 3px;
        }
        
        .progress-bar::after {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            width: 100%;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            animation: progress 60s linear forwards;
        }
        
        .floating-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
            pointer-events: none;
        }
        
        .floating-element {
            position: absolute;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 50%;
            animation: float 15s linear infinite;
        }
        
        .refresh-btn {
            transition: all 0.3s ease;
        }
        
        .refresh-btn:hover {
            animation: rotate 0.6s ease-in-out;
        }
        
        .action-btn {
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .action-btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 5px;
            height: 5px;
            background: rgba(255, 255, 255, 0.5);
            opacity: 0;
            border-radius: 100%;
            transform: scale(1, 1) translate(-50%, -50%);
            transform-origin: 50% 50%;
        }
        
        .action-btn:focus:not(:active)::after {
            animation: ripple 1s ease-out;
        }
        
        @keyframes ripple {
            0% {
                transform: scale(0, 0);
                opacity: 0.5;
            }
            100% {
                transform: scale(20, 20);
                opacity: 0;
            }
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            transform: translateX(150%);
            transition: transform 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .streak-flame {
            animation: pulse 1.5s infinite;
        }
        
        @media (max-width: 640px) {
            .quote-text {
                font-size: 1.5rem;
            }
            .quote-author {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body class="min-h-screen flex flex-col items-center justify-center p-4 relative overflow-hidden">
    <!-- Floating background elements -->
    <div class="floating-elements">
        <div class="floating-element" style="width: 300px; height: 300px; top: -50px; left: -50px; animation-delay: 0s;"></div>
        <div class="floating-element" style="width: 200px; height: 200px; bottom: -30px; right: -30px; animation-delay: 2s;"></div>
        <div class="floating-element" style="width: 150px; height: 150px; top: 30%; right: -30px; animation-delay: 4s;"></div>
        <div class="floating-element" style="width: 250px; height: 250px; bottom: 20%; left: -50px; animation-delay: 6s;"></div>
    </div>
    
    <!-- Main Content -->
    <div class="max-w-3xl w-full mx-auto z-10">
        <!-- Header -->
        <div class="flex justify-between items-center mb-6">
            <div class="gradient-bg px-4 py-2 rounded-full shadow-lg">
                <h1 class="text-xl font-bold flex items-center">
                    <i class="fas fa-spa mr-2 animate-spin" style="animation-duration: 10s;"></i>
                    ZenMotiv
                </h1>
            </div>
            <div class="flex items-center space-x-2">
                <div class="glass-card px-3 py-1 rounded-full text-sm flex items-center">
                    <i class="fas fa-fire streak-flame text-orange-400 mr-1"></i>
                    <span id="streakCount">0</span> day streak
                </div>
                <button id="settingsBtn" class="glass-card p-2 rounded-full">
                    <i class="fas fa-cog"></i>
                </button>
            </div>
        </div>
        
        <!-- Quote Card -->
        <div class="glass-card rounded-2xl p-6 md:p-8 mb-6 relative overflow-hidden animate-fadeIn">
            <div class="absolute inset-0 gradient-bg opacity-10"></div>
            <div class="relative z-10">
                <div class="flex justify-between items-start mb-6">
                    <div class="text-amber-300">
                        <i class="fas fa-quote-left text-3xl opacity-50"></i>
                    </div>
                    <div class="flex items-center space-x-3">
                        <div class="glass-card px-3 py-1 rounded-full text-sm hidden sm:block">
                            <span id="timer">60</span>s until refresh
                        </div>
                        <button id="refreshBtn" class="refresh-btn glass-card p-3 rounded-full">
                            <i class="fas fa-sync-alt"></i>
                        </button>
                    </div>
                </div>
                
                <div id="quoteContainer" class="mb-8 min-h-40">
                    <p id="quoteText" class="quote-text quote-font text-2xl md:text-3xl font-medium mb-6 leading-relaxed">
                        "The only way to do great work is to love what you do."
                    </p>
                    <p id="quoteAuthor" class="quote-author text-xl text-right italic text-amber-300">
                        — Steve Jobs
                    </p>
                </div>
                
                <div class="progress-bar mb-6"></div>
                
                <div class="flex flex-wrap justify-center gap-3">
                    <button id="shareTwitter" class="action-btn bg-blue-500 hover:bg-blue-600 px-4 py-2 rounded-full flex items-center">
                        <i class="fab fa-twitter mr-2"></i> Tweet
                    </button>
                    <button id="copyQuote" class="action-btn bg-slate-700 hover:bg-slate-600 px-4 py-2 rounded-full flex items-center">
                        <i class="fas fa-copy mr-2"></i> Copy
                    </button>
                    <button id="saveFavorite" class="action-btn bg-rose-500 hover:bg-rose-600 px-4 py-2 rounded-full flex items-center">
                        <i class="fas fa-heart mr-2"></i> Save
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Daily Challenge -->
        <div class="glass-card rounded-2xl p-6 mb-6 animate-fadeIn" style="animation-delay: 0.2s;">
            <div class="flex justify-between items-center mb-4">
                <h2 class="text-lg font-semibold flex items-center">
                    <i class="fas fa-trophy text-amber-300 mr-2"></i>
                    Daily Challenge
                </h2>
                <div class="flex items-center text-sm">
                    <i class="fas fa-bolt text-purple-300 mr-1"></i>
                    <span id="xpCount">0</span> XP
                </div>
            </div>
            <p id="dailyChallenge" class="text-lg mb-4">
                Practice gratitude by writing down 3 things you're thankful for today.
            </p>
            <div class="flex justify-between items-center">
                <div class="text-sm text-slate-300">
                    Complete to earn 10 XP
                </div>
                <button id="completeChallenge" class="action-btn bg-emerald-500 hover:bg-emerald-600 px-4 py-2 rounded-full text-sm">
                    Mark Complete
                </button>
            </div>
        </div>
        
        <!-- Quote Categories -->
        <div class="glass-card rounded-2xl p-6 animate-fadeIn" style="animation-delay: 0.4s;">
            <h2 class="text-lg font-semibold mb-4 flex items-center">
                <i class="fas fa-tags text-amber-300 mr-2"></i>
                Categories
            </h2>
            <div class="flex flex-wrap gap-2">
                <button class="category-btn action-btn bg-slate-700 hover:bg-slate-600 px-3 py-1 rounded-full text-sm" data-category="all">
                    All Quotes
                </button>
                <button class="category-btn action-btn bg-slate-700 hover:bg-slate-600 px-3 py-1 rounded-full text-sm" data-category="motivation">
                    Motivation
                </button>
                <button class="category-btn action-btn bg-slate-700 hover:bg-slate-600 px-3 py-1 rounded-full text-sm" data-category="success">
                    Success
                </button>
                <button class="category-btn action-btn bg-slate-700 hover:bg-slate-600 px-3 py-1 rounded-full text-sm" data-category="life">
                    Life
                </button>
                <button class="category-btn action-btn bg-slate-700 hover:bg-slate-600 px-3 py-1 rounded-full text-sm" data-category="wisdom">
                    Wisdom
                </button>
            </div>
        </div>
    </div>
    
    <!-- Floating Action Button -->
    <div class="fixed bottom-6 right-6 z-20">
        <button id="inspireMe" class="gradient-bg p-4 rounded-full shadow-xl animate-float hover:shadow-2xl transition-all duration-300">
            <i class="fas fa-bolt text-white text-xl"></i>
        </button>
    </div>
    
    <!-- Notification -->
    <div id="notification" class="notification glass-card px-4 py-3 rounded-lg flex items-center">
        <i class="fas fa-check-circle text-emerald-400 mr-2"></i>
        <span>Quote copied to clipboard!</span>
    </div>
    
    <!-- Settings Modal (hidden by default) -->
    <div id="settingsModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-30 opacity-0 invisible transition-all duration-300">
        <div class="glass-card rounded-2xl p-6 max-w-md w-full mx-4 transform translate-y-10 transition-all duration-300">
            <div class="flex justify-between items-center mb-4">
                <h2 class="text-xl font-bold">Settings</h2>
                <button id="closeSettings" class="p-2 rounded-full hover:bg-slate-700">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            <div class="space-y-4">
                <div>
                    <label class="block mb-2">Auto-refresh interval</label>
                    <select id="refreshInterval" class="w-full bg-slate-800 border border-slate-700 rounded-lg px-4 py-2">
                        <option value="30">30 seconds</option>
                        <option value="60" selected>60 seconds</option>
                        <option value="120">2 minutes</option>
                        <option value="300">5 minutes</option>
                        <option value="0">Off</option>
                    </select>
                </div>
                <div>
                    <label class="flex items-center space-x-2">
                        <input type="checkbox" id="darkModeToggle" class="rounded bg-slate-700 border-slate-600">
                        <span>Dark Mode</span>
                    </label>
                </div>
                <div>
                    <label class="flex items-center space-x-2">
                        <input type="checkbox" id="dailyChallengeToggle" class="rounded bg-slate-700 border-slate-600" checked>
                        <span>Show Daily Challenge</span>
                    </label>
                </div>
                <button id="saveSettings" class="w-full bg-indigo-600 hover:bg-indigo-700 px-4 py-2 rounded-lg mt-4">
                    Save Settings
                </button>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // DOM Elements
            const quoteText = document.getElementById('quoteText');
            const quoteAuthor = document.getElementById('quoteAuthor');
            const quoteContainer = document.getElementById('quoteContainer');
            const refreshBtn = document.getElementById('refreshBtn');
            const inspireMe = document.getElementById('inspireMe');
            const timer = document.getElementById('timer');
            const shareTwitter = document.getElementById('shareTwitter');
            const copyQuote = document.getElementById('copyQuote');
            const saveFavorite = document.getElementById('saveFavorite');
            const dailyChallenge = document.getElementById('dailyChallenge');
            const streakCount = document.getElementById('streakCount');
            const xpCount = document.getElementById('xpCount');
            const completeChallenge = document.getElementById('completeChallenge');
            const notification = document.getElementById('notification');
            const settingsBtn = document.getElementById('settingsBtn');
            const settingsModal = document.getElementById('settingsModal');
            const closeSettings = document.getElementById('closeSettings');
            const saveSettings = document.getElementById('saveSettings');
            const refreshInterval = document.getElementById('refreshInterval');
            const categoryBtns = document.querySelectorAll('.category-btn');
            
            // App State
            let currentQuoteIndex = 0;
            let currentChallengeIndex = 0;
            let countdown = 60;
            let countdownInterval;
            let currentCategory = 'all';
            let autoRefreshEnabled = true;
            
            // Quote data
            const quotes = {
                all: [
                    { text: "The only way to do great work is to love what you do.", author: "Steve Jobs", category: "success" },
                    { text: "Success is not final, failure is not fatal: It is the courage to continue that counts.", author: "Winston Churchill", category: "motivation" },
                    { text: "Your time is limited, don't waste it living someone else's life.", author: "Steve Jobs", category: "life" },
                    { text: "The future belongs to those who believe in the beauty of their dreams.", author: "Eleanor Roosevelt", category: "motivation" },
                    { text: "Don't watch the clock; do what it does. Keep going.", author: "Sam Levenson", category: "motivation" },
                    { text: "The only limit to our realization of tomorrow will be our doubts of today.", author: "Franklin D. Roosevelt", category: "wisdom" },
                    { text: "What you get by achieving your goals is not as important as what you become by achieving your goals.", author: "Zig Ziglar", category: "success" },
                    { text: "The best way to predict the future is to create it.", author: "Peter Drucker", category: "wisdom" },
                    { text: "You are never too old to set another goal or to dream a new dream.", author: "C.S. Lewis", category: "motivation" },
                    { text: "Believe in yourself and all that you are. Know that there is something inside you that is greater than any obstacle.", author: "Christian D. Larson", category: "motivation" }
                ],
                motivation: [
                    { text: "The only way to do great work is to love what you do.", author: "Steve Jobs" },
                    { text: "Success is not final, failure is not fatal: It is the courage to continue that counts.", author: "Winston Churchill" },
                    { text: "The future belongs to those who believe in the beauty of their dreams.", author: "Eleanor Roosevelt" },
                    { text: "Don't watch the clock; do what it does. Keep going.", author: "Sam Levenson" },
                    { text: "You are never too old to set another goal or to dream a new dream.", author: "C.S. Lewis" },
                    { text: "Believe in yourself and all that you are. Know that there is something inside you that is greater than any obstacle.", author: "Christian D. Larson" }
                ],
                success: [
                    { text: "The only way to do great work is to love what you do.", author: "Steve Jobs" },
                    { text: "What you get by achieving your goals is not as important as what you become by achieving your goals.", author: "Zig Ziglar" }
                ],
                life: [
                    { text: "Your time is limited, don't waste it living someone else's life.", author: "Steve Jobs" }
                ],
                wisdom: [
                    { text: "The only limit to our realization of tomorrow will be our doubts of today.", author: "Franklin D. Roosevelt" },
                    { text: "The best way to predict the future is to create it.", author: "Peter Drucker" }
                ]
            };
            
            // Challenges data
            const challenges = [
                "Practice gratitude by writing down 3 things you're thankful for today.",
                "Start your day with 5 minutes of meditation.",
                "Compliment 3 people today.",
                "Take a 30-minute walk in nature.",
                "Learn something new for 15 minutes.",
                "Do one thing that scares you today.",
                "Drink 8 glasses of water today.",
                "Express appreciation to someone important in your life.",
                "Spend 30 minutes without screens before bed.",
                "Perform one random act of kindness."
            ];
            
            // Initialize
            loadUserData();
            updateChallenge();
            startCountdown();
            createFloatingParticles();
            
            // Functions
            function getRandomQuote() {
                let quoteList = currentCategory === 'all' ? quotes.all : quotes[currentCategory];
                
                if (quoteList.length === 0) {
                    quoteList = quotes.all; // Fallback to all quotes if category is empty
                }
                
                let newIndex;
                do {
                    newIndex = Math.floor(Math.random() * quoteList.length);
                } while (newIndex === currentQuoteIndex && quoteList.length > 1);
                
                currentQuoteIndex = newIndex;
                return quoteList[currentQuoteIndex];
            }
            
            function displayQuote(quote) {
                quoteContainer.classList.remove('animate-fadeIn');
                void quoteContainer.offsetWidth; // Trigger reflow
                quoteContainer.classList.add('animate-fadeIn');
                
                quoteText.textContent = `"${quote.text}"`;
                quoteAuthor.textContent = `— ${quote.author}`;
            }
            
            function updateChallenge() {
                currentChallengeIndex = Math.floor(Math.random() * challenges.length);
                dailyChallenge.textContent = challenges[currentChallengeIndex];
            }
            
            function startCountdown() {
                clearInterval(countdownInterval);
                
                if (!autoRefreshEnabled) {
                    timer.textContent = "Off";
                    return;
                }
                
                countdown = parseInt(refreshInterval.value) || 60;
                timer.textContent = countdown;
                
                countdownInterval = setInterval(() => {
                    countdown--;
                    timer.textContent = countdown;
                    
                    if (countdown <= 0) {
                        loadNewQuote();
                        countdown = parseInt(refreshInterval.value) || 60;
                    }
                }, 1000);
            }
            
            function loadNewQuote() {
                const quote = getRandomQuote();
                displayQuote(quote);
                
                // Reset progress bar animation
                const progressBar = document.querySelector('.progress-bar');
                progressBar.innerHTML = '';
                const progress = document.createElement('div');
                progress.className = 'progress-bar';
                progress.innerHTML = '<div class="progress-bar-inner"></div>';
                progress.querySelector('.progress-bar-inner').style.animation = `progress ${countdown}s linear forwards`;
                progressBar.replaceWith(progress);
            }
            
            function showNotification(message, type = 'success') {
                const icon = type === 'success' ? 'fa-check-circle' : 'fa-exclamation-circle';
                const color = type === 'success' ? 'text-emerald-400' : 'text-amber-400';
                
                notification.innerHTML = `
                    <i class="fas ${icon} ${color} mr-2"></i>
                    <span>${message}</span>
                `;
                
                notification.classList.add('show');
                
                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }
            
            function loadUserData() {
                // Load streak from localStorage
                const streak = localStorage.getItem('motivationStreak') || 0;
                streakCount.textContent = streak;
                
                // Load XP from localStorage
                const xp = localStorage.getItem('motivationXP') || 0;
                xpCount.textContent = xp;
                
                // Load settings from localStorage
                const settings = JSON.parse(localStorage.getItem('motivationSettings')) || {
                    refreshInterval: 60,
                    darkMode: false,
                    showChallenge: true
                };
                
                refreshInterval.value = settings.refreshInterval;
                document.getElementById('darkModeToggle').checked = settings.darkMode;
                document.getElementById('dailyChallengeToggle').checked = settings.showChallenge;
                
                // Apply dark mode if enabled
                if (settings.darkMode) {
                    document.documentElement.classList.add('dark');
                }
                
                // Show/hide challenge based on setting
                document.querySelector('#dailyChallenge').parentElement.style.display = 
                    settings.showChallenge ? 'block' : 'none';
                
                autoRefreshEnabled = settings.refreshInterval !== '0';
            }
            
            function saveUserData() {
                const settings = {
                    refreshInterval: refreshInterval.value,
                    darkMode: document.getElementById('darkModeToggle').checked,
                    showChallenge: document.getElementById('dailyChallengeToggle').checked
                };
                
                localStorage.setItem('motivationSettings', JSON.stringify(settings));
                
                // Apply settings immediately
                autoRefreshEnabled = settings.refreshInterval !== '0';
                startCountdown();
                
                // Show/hide challenge
                document.querySelector('#dailyChallenge').parentElement.style.display = 
                    settings.showChallenge ? 'block' : 'none';
                
                // Toggle dark mode
                if (settings.darkMode) {
                    document.documentElement.classList.add('dark');
                } else {
                    document.documentElement.classList.remove('dark');
                }
                
                showNotification('Settings saved successfully!');
                closeSettingsModal();
            }
            
            function openSettingsModal() {
                settingsModal.classList.remove('invisible', 'opacity-0');
                settingsModal.querySelector('div').classList.remove('translate-y-10');
            }
            
            function closeSettingsModal() {
                settingsModal.classList.add('invisible', 'opacity-0');
                settingsModal.querySelector('div').classList.add('translate-y-10');
            }
            
            function createFloatingParticles() {
                const container = document.querySelector('.floating-elements');
                
                // Create more floating particles
                for (let i = 0; i < 15; i++) {
                    const particle = document.createElement('div');
                    particle.className = 'floating-element';
                    
                    // Random size between 10px and 80px
                    const size = Math.random() * 70 + 10;
                    particle.style.width = `${size}px`;
                    particle.style.height = `${size}px`;
                    
                    // Random position
                    particle.style.top = `${Math.random() * 100}%`;
                    particle.style.left = `${Math.random() * 100}%`;
                    
                    // Random animation duration and delay
                    const duration = Math.random() * 20 + 10;
                    const delay = Math.random() * 10;
                    particle.style.animation = `float ${duration}s linear infinite`;
                    particle.style.animationDelay = `${delay}s`;
                    
                    // Random opacity
                    particle.style.opacity = Math.random() * 0.1;
                    
                    // Random border radius for variety
                    if (Math.random() > 0.7) {
                        particle.style.borderRadius = '10%';
                    }
                    
                    container.appendChild(particle);
                }
            }
            
            // Event Listeners
            refreshBtn.addEventListener('click', () => {
                loadNewQuote();
                startCountdown();
            });
            
            inspireMe.addEventListener('click', () => {
                loadNewQuote();
                startCountdown();
            });
            
            shareTwitter.addEventListener('click', () => {
                const currentQuote = currentCategory === 'all' ? 
                    quotes.all[currentQuoteIndex] : 
                    quotes[currentCategory][currentQuoteIndex];
                    
                const text = `"${currentQuote.text}" - ${currentQuote.author}`;
                const url = `https://twitter.com/intent/tweet?text=${encodeURIComponent(text)}&hashtags=motivation,quote`;
                window.open(url, '_blank');
            });
            
            copyQuote.addEventListener('click', () => {
                const currentQuote = currentCategory === 'all' ? 
                    quotes.all[currentQuoteIndex] : 
                    quotes[currentCategory][currentQuoteIndex];
                    
                const text = `"${currentQuote.text}" - ${currentQuote.author}`;
                navigator.clipboard.writeText(text)
                    .then(() => {
                        showNotification('Quote copied to clipboard!');
                    })
                    .catch(err => {
                        showNotification('Failed to copy quote', 'error');
                        console.error('Failed to copy: ', err);
                    });
            });
            
            saveFavorite.addEventListener('click', () => {
                // In a real app, you would save to localStorage or a database
                showNotification('Quote saved to favorites!');
            });
            
            completeChallenge.addEventListener('click', () => {
                const currentStreak = parseInt(localStorage.getItem('motivationStreak') || 0);
                const newStreak = currentStreak + 1;
                localStorage.setItem('motivationStreak', newStreak);
                streakCount.textContent = newStreak;
                
                const currentXP = parseInt(localStorage.getItem('motivationXP') || 0);
                const newXP = currentXP + 10;
                localStorage.setItem('motivationXP', newXP);
                xpCount.textContent = newXP;
                
                showNotification('Challenge completed! +10 XP');
                updateChallenge();
            });
            
            settingsBtn.addEventListener('click', openSettingsModal);
            closeSettings.addEventListener('click', closeSettingsModal);
            saveSettings.addEventListener('click', saveUserData);
            
            // Close modal when clicking outside
            settingsModal.addEventListener('click', (e) => {
                if (e.target === settingsModal) {
                    closeSettingsModal();
                }
            });
            
            // Category buttons
            categoryBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    currentCategory = btn.dataset.category;
                    
                    // Update active state
                    categoryBtns.forEach(b => b.classList.remove('bg-indigo-600'));
                    btn.classList.add('bg-indigo-600');
                    
                    loadNewQuote();
                    startCountdown();
                });
            });
            
            // Initial quote load
            loadNewQuote();
        });
    </script>
</body>
</html>
