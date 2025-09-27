<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> Google Clicker</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.js"></script>
    <style>
        body {
            font-family: sans-serif;
            transition: background-color 0.3s ease;
        }
        /* Dark mode styles using the dark: prefix from Tailwind CSS */
        .dark body {
            background-color: #1a202c; /* A dark gray background */
        }
        .dark .bg-white {
            background-color: #2d3748; /* Darker gray for the card */
            color: #e2e8f0; /* Light text */
        }
        .dark .text-gray-700 {
            color: #e2e8f0;
        }
        .dark .text-gray-500 {
            color: #a0aec0;
        }
        .dark .bg-gray-200 {
            background-color: #4a5568; /* Darker gray for upgrade boxes */
        }
        .dark .text-gray-600 {
            color: #e2e8f0;
        }
        .dark .bg-green-500 {
            background-color: #48bb78;
        }
        /* Bounce animation for the main button */
        @keyframes bounce-animation {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        .animate-bounce {
            animation: bounce-animation 0.3s ease-in-out;
        }
        
        /* Prevent the image from being selected on double-click */
        #mainButton {
            -webkit-user-select: none; /* Safari */
            -ms-user-select: none; /* IE 10+ */
            user-select: none; /* Standard syntax */
        }
    </style>
</head>
<body class="bg-gray-100 min-h-screen flex items-center justify-center p-4 dark:bg-gray-800">

    <div class="absolute top-4 right-4 flex space-x-2">
        <button id="musicToggle" class="p-2 rounded-full bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 transition-colors duration-300">
            sound on
        </button>
        <button id="themeToggle" class="p-2 rounded-full bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 transition-colors duration-300">
            ☀️ / 🌙
        </button>
    </div>

    <div class="bg-white rounded-xl shadow-lg p-6 w-full max-w-sm flex flex-col items-center dark:bg-gray-700 dark:text-gray-200">
        <h1 class="text-3xl font-bold mb-4 text-center">Google Clicker</h1>

        <!-- Score Display -->
        <div class="mb-6">
            <p class="text-xl text-gray-700 dark:text-gray-200">Clicks: <span id="clicks" class="font-bold text-blue-600 text-3xl">0</span></p>
            <p class="text-md text-gray-500 dark:text-gray-400 text-center">Clicks/sec: <span id="clicksPerSecondDisplay">0</span></p>
            <p class="text-md text-gray-500 dark:text-gray-400 text-center">Prestige Multiplier: <span id="prestigeMultiplierDisplay">x1</span></p>
        </div>

        <!-- Main Click Button (now an image) -->
        <div class="flex flex-col items-center mb-6">
            <img id="mainButton" src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Google logo" class="cursor-pointer w-40 h-auto transform hover:scale-105 transition-transform duration-200">
            <p id="clicksPerClickDisplay" class="text-sm text-gray-500 dark:text-gray-400 mt-2"></p>
        </div>

        <!-- Upgrades Section -->
        <div class="mt-8 w-full">
            <h2 class="text-2xl font-semibold mb-4 text-center">Upgrades</h2>
            <div id="upgrades-container" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <!-- Upgrades will be generated dynamically here -->
            </div>
        </div>

        <section class="mt-8 w-full">
            <h2 class="text-2xl font-semibold mb-4 text-center">Achievements</h2>
            <div id="achievement-list" class="grid grid-cols-1 gap-2">
                <!-- Achievements will be populated here by JavaScript -->
            </div>
        </section>

        <!-- Prestige Section -->
        <section class="mt-8 w-full border-t-2 border-gray-300 dark:border-gray-600 pt-4">
            <h2 class="text-2xl font-semibold mb-2 text-center">Prestige</h2>
            <p class="text-center text-sm mb-4 text-gray-600 dark:text-gray-400">
                Prestige to reset your game and gain a permanent multiplier to Clicks per Second!
            </p>
            <div id="prestige-info" class="text-center mb-4">
                <p>You have <span id="prestigePointsDisplay" class="font-bold text-lg text-yellow-500">0</span> Prestige Points.</p>
                <p>You will earn <span id="prestigeGainDisplay" class="font-bold text-lg text-yellow-500">0</span> more points.</p>
                <p>Requires: <span id="prestigeCostDisplay" class="font-bold text-lg text-red-500">100,000,000</span> Clicks</p>
            </div>
            <button id="prestigeButton" class="w-full bg-red-500 hover:bg-red-600 text-white font-bold py-3 px-4 rounded-lg transition duration-200 disabled:opacity-50" disabled>
                Prestige
            </button>
        </section>

    </div>

    <!-- Achievement notification container -->
    <div id="achievement-notification" class="fixed bottom-4 right-4 bg-yellow-400 text-gray-900 px-4 py-2 rounded-lg shadow-lg hidden">
        <p class="font-bold text-center"></p>
    </div>

    <script>
        // Game State
        let clicks = 0;
        let clicksPerSecond = 0;
        let clicksPerClick = 1;
        let totalManualClicks = 0;
        let totalUpgrades = 0;
        let prestigePoints = 0;
        const PRESTIGE_COST = 100000000;
        let soundState = 0; // 0: off, 1: music only, 2: all sounds

        // Upgrades data
        const upgrades = [
            { id: 'cursor', name: 'Cursor', description: 'Generates 1 click/sec.', cost: 10, initialCost: 10, count: 0, baseCps: 1, type: 'cps' },
            { id: 'superClicker', name: 'Super Clicker', description: 'Increases manual clicks by 1.', cost: 100, initialCost: 100, count: 0, baseCpc: 1, type: 'cpc' },
            { id: 'farm', name: 'Click Farm', description: 'Generates 10 clicks/sec.', cost: 500, initialCost: 500, count: 0, baseCps: 10, type: 'cps' },
            { id: 'megaClicker', name: 'Mega Clicker', description: 'Increases manual clicks by 10.', cost: 1000, initialCost: 1000, count: 0, baseCpc: 10, type: 'cpc' },
            { id: 'factory', name: 'Click Factory', description: 'Generates 50 clicks/sec.', cost: 5000, initialCost: 5000, count: 0, baseCps: 50, type: 'cps' },
            { id: 'ultraClicker', name: 'Ultra Clicker', description: 'Increases manual clicks by 50.', cost: 10000, initialCost: 10000, count: 0, baseCpc: 50, type: 'cpc' },
            { id: 'quantumProcessor', name: 'Quantum Processor', description: 'Generates 100 clicks/sec.', cost: 25000, initialCost: 25000, count: 0, baseCps: 100, type: 'cps' },
            { id: 'nanobotSwarm', name: 'Nanobot Swarm', description: 'Generates 500 clicks/sec.', cost: 100000, initialCost: 100000, count: 0, baseCps: 500, type: 'cps' },
            { id: 'fusionReactor', name: 'Fusion Reactor', description: 'Generates 1,000 clicks/sec.', cost: 500000, initialCost: 500000, count: 0, baseCps: 1000, type: 'cps' },
            { id: 'blackHole', name: 'Black Hole', description: 'Generates 5,000 clicks/sec.', cost: 2500000, initialCost: 2500000, count: 0, baseCps: 5000, type: 'cps' },
            { id: 'cosmicRay', name: 'Cosmic Ray', description: 'Generates 10,000 clicks/sec.', cost: 10000000, initialCost: 10000000, count: 0, baseCps: 10000, type: 'cps' },
            { id: 'timeLoop', name: 'Time Loop', description: 'Generates 50,000 clicks/sec.', cost: 50000000, initialCost: 50000000, count: 0, baseCps: 50000, type: 'cps' },
            { id: 'dimensionShift', name: 'Dimension Shift', description: 'Generates 100,000 clicks/sec.', cost: 100000000, initialCost: 100000000, count: 0, baseCps: 100000, type: 'cps' },
            { id: 'parallelUniverse', name: 'Parallel Universe', description: 'Generates 500,000 clicks/sec.', cost: 500000000, initialCost: 500000000, count: 0, baseCps: 500000, type: 'cps' },
            { id: 'multiverseEngine', name: 'Multiverse Engine', description: 'Generates 1,000,000 clicks/sec.', cost: 1000000000, initialCost: 1000000000, count: 0, baseCps: 1000000, type: 'cps' },
            { id: 'hyperClicker', name: 'Hyper Clicker', description: 'Increases manual clicks by 100.', cost: 50000, initialCost: 50000, count: 0, baseCpc: 100, type: 'cpc' },
            { id: 'godhand', name: 'God Hand', description: 'Increases manual clicks by 1,000.', cost: 250000, initialCost: 250000, count: 0, baseCpc: 1000, type: 'cpc' },
            { id: 'singularity', name: 'Singularity', description: 'Increases manual clicks by 10,000.', cost: 1000000, initialCost: 1000000, count: 0, baseCpc: 10000, type: 'cpc' },
            { id: 'omnibot', name: 'Omnibot', description: 'Increases manual clicks by 50,000.', cost: 5000000, initialCost: 5000000, count: 0, baseCpc: 50000, type: 'cpc' },
            { id: 'cosmicConductor', name: 'Cosmic Conductor', description: 'Increases manual clicks by 100,000.', cost: 10000000, initialCost: 10000000, count: 0, baseCpc: 100000, type: 'cpc' },
            { id: 'chronos', name: 'Chronos', description: 'Increases manual clicks by 500,000.', cost: 50000000, initialCost: 50000000, count: 0, baseCpc: 500000, type: 'cpc' },
            { id: 'realityBender', name: 'Reality Bender', description: 'Increases manual clicks by 1,000,000.', cost: 100000000, initialCost: 100000000, count: 0, baseCpc: 1000000, type: 'cpc' },
        ];

        // Achievements data
        const achievements = [
            { id: 'firstClick', name: 'First Step', description: 'Click the button for the first time.', condition: () => totalManualClicks >= 1, unlocked: false },
            { id: 'centenary', name: 'Centenary Clicker', description: 'Click the button 100 times.', condition: () => totalManualClicks >= 100, unlocked: false },
            { id: 'thousandClicks', name: 'Grand Clicker', description: 'Reach 1,000 total clicks.', condition: () => clicks >= 1000, unlocked: false },
            { id: 'tenThousandClicks', name: 'Mega Clicker', description: 'Reach 10,000 total clicks.', condition: () => clicks >= 10000, unlocked: false },
            { id: 'firstUpgrade', name: 'Starter Kit', description: 'Buy your first upgrade.', condition: () => totalUpgrades >= 1, unlocked: false },
            { id: 'powerUser', name: 'Power User', description: 'Buy 5 upgrades.', condition: () => totalUpgrades >= 5, unlocked: false },
            { id: 'automated', name: 'Automated', description: 'Reach 10 clicks per second.', condition: () => clicksPerSecond >= 10, unlocked: false },
            { id: 'clickMaster', name: 'Click Master', description: 'Get 20 clicks per manual click.', condition: () => clicksPerClick >= 20, unlocked: false },
            { id: 'tycoon', name: 'Tycoon', description: 'Reach 100 clicks per second.', condition: () => clicksPerSecond >= 100, unlocked: false },
            { id: 'ultimateClicker', name: 'Ultimate Clicker', description: 'Reach 1,000 clicks per second.', condition: () => clicksPerSecond >= 1000, unlocked: false },
            { id: 'prestigeReady', name: 'Prestige Ready', description: `Reach ${formatNumber(PRESTIGE_COST)} clicks.`, condition: () => clicks >= PRESTIGE_COST, unlocked: false },
        ];

        // HTML Elements
        const clicksEl = document.getElementById('clicks');
        const clicksPerSecondDisplay = document.getElementById('clicksPerSecondDisplay');
        const prestigeMultiplierDisplay = document.getElementById('prestigeMultiplierDisplay');
        const mainButton = document.getElementById('mainButton');
        const clicksPerClickDisplay = document.getElementById('clicksPerClickDisplay');
        const upgradesContainer = document.getElementById('upgrades-container');
        const themeToggle = document.getElementById('themeToggle');
        const musicToggle = document.getElementById('musicToggle');
        const html = document.documentElement;
        const achievementList = document.getElementById('achievement-list');
        const achievementNotification = document.getElementById('achievement-notification');
        const prestigeButton = document.getElementById('prestigeButton');
        const prestigePointsDisplay = document.getElementById('prestigePointsDisplay');
        const prestigeGainDisplay = document.getElementById('prestigeGainDisplay');
        const prestigeCostDisplay = document.getElementById('prestigeCostDisplay');
        
        const soundStates = ['🔇', '🎶', '🔊'];

        // Dark Mode Logic
        const savedTheme = localStorage.getItem('theme');
        if (savedTheme) {
            html.classList.add(savedTheme);
        } else if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
            html.classList.add('dark');
        }

        themeToggle.addEventListener('click', () => {
            if (html.classList.contains('dark')) {
                html.classList.remove('dark');
                localStorage.setItem('theme', '');
            } else {
                html.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        });

        // --- Sound and Music Logic ---
        // Background music: A simple synth loop
        const bgmSynth = new Tone.Synth({
            oscillator: { type: "triangle" },
            envelope: {
                attack: 0.05,
                decay: 0.1,
                sustain: 0.3,
                release: 0.5
            }
        }).toDestination();

        const melody = ["C4", "E4", "G4", "A4", "G4", "E4", "C4", null];
        let melodyIndex = 0;
        const bgmLoop = new Tone.Loop(() => {
            if (soundState > 0) { // Play music if state is music only or all sounds
                const note = melody[melodyIndex % melody.length];
                if (note) {
                    bgmSynth.triggerAttackRelease(note, "8n");
                }
                melodyIndex++;
            }
        }, "4n").start(0);

        // Click sound effect: A short, high-pitched synth tone
        const clickSynth = new Tone.Synth({
            oscillator: { type: "square" },
            envelope: {
                attack: 0.001,
                decay: 0.05,
                sustain: 0.0,
                release: 0.01
            }
        }).toDestination();

        // New synth for upgrade purchase sound: A quick, ascending two-note arpeggio
        // Changed to a PolySynth to handle multiple notes
        const upgradeSynth = new Tone.PolySynth(Tone.Synth, {
            oscillator: { type: "sawtooth" },
            envelope: {
                attack: 0.01,
                decay: 0.1,
                sustain: 0.0,
                release: 0.1
            }
        }).toDestination();

        // New synth for achievement unlock: A short, celebratory chime
        const achievementSynth = new Tone.MetalSynth({
            frequency: 200,
            envelope: {
                attack: 0.001,
                decay: 0.5,
                release: 0.2
            },
            harmonicity: 3.1,
            modulationIndex: 1,
            resonance: 4000,
            octaves: 1.5
        }).toDestination();


        musicToggle.addEventListener('click', async () => {
            // Need to start the Tone.js audio context on the first user interaction
            await Tone.start();
            
            // Cycle through the states
            soundState = (soundState + 1) % soundStates.length;
            
            if (soundState === 0) {
                bgmLoop.stop();
            } else if (soundState === 1) {
                 bgmLoop.start();
            }

            musicToggle.textContent = soundStates[soundState];
        });

        // --- Game Logic Functions ---
        function formatNumber(num) {
            if (num >= 1000000000) return (num / 1000000000).toFixed(1).replace(/\.0$/, '') + 'B';
            if (num >= 1000000) return (num / 1000000).toFixed(1).replace(/\.0$/, '') + 'M';
            if (num >= 1000) return (num / 1000).toFixed(1).replace(/\.0$/, '') + 'K';
            return Math.floor(num);
        }

        function updateDisplay() {
            const baseCps = upgrades.filter(u => u.type === 'cps').reduce((sum, u) => sum + (u.count * u.baseCps), 0);
            clicksPerSecond = baseCps * (1 + prestigePoints);

            clicksEl.textContent = formatNumber(clicks);
            clicksPerSecondDisplay.textContent = formatNumber(clicksPerSecond);
            clicksPerClickDisplay.textContent = `+${formatNumber(clicksPerClick)} per click`;
            prestigePointsDisplay.textContent = formatNumber(prestigePoints);
            prestigeMultiplierDisplay.textContent = `x${formatNumber(1 + prestigePoints)}`;
            prestigeCostDisplay.textContent = formatNumber(PRESTIGE_COST);
            
            const potentialGain = Math.floor(clicks / (PRESTIGE_COST / 10)); // Example gain formula
            prestigeGainDisplay.textContent = formatNumber(potentialGain);

            prestigeButton.disabled = clicks < PRESTIGE_COST;
            
            upgrades.forEach(upgrade => {
                const upgradeEl = document.getElementById(upgrade.id);
                if (upgradeEl) {
                    const costSpan = upgradeEl.querySelector('.cost');
                    const countSpan = upgradeEl.querySelector('.count');
                    const buyBtn = upgradeEl.querySelector('.buy-button');

                    costSpan.textContent = formatNumber(upgrade.cost);
                    countSpan.textContent = upgrade.count;
                    buyBtn.disabled = clicks < upgrade.cost;
                }
            });
            
            checkAchievements();
        }

        function checkAchievements() {
            achievements.forEach(achievement => {
                if (!achievement.unlocked && achievement.condition()) {
                    achievement.unlocked = true;
                    showAchievementNotification(achievement.name);
                    renderAchievements();
                }
            });
        }

        function renderUpgrades() {
            upgradesContainer.innerHTML = '';
            upgrades.forEach(upgrade => {
                const upgradeCard = document.createElement('div');
                upgradeCard.id = upgrade.id;
                upgradeCard.className = 'bg-gray-200 rounded-lg p-4 mb-4 dark:bg-gray-600';
                upgradeCard.innerHTML = `
                    <div class="flex justify-between items-center mb-2">
                        <p class="text-lg font-medium">${upgrade.name}</p>
                        <p class="text-sm text-gray-600 dark:text-gray-200">You have <span class="count">${upgrade.count}</span></p>
                    </div>
                    <p class="text-xs text-gray-500 dark:text-gray-400 mb-2">${upgrade.description}</p>
                    <button class="buy-button w-full bg-green-500 hover:bg-green-600 text-white font-bold py-2 px-4 rounded-lg transition duration-200 disabled:opacity-50" data-upgrade-id="${upgrade.id}">
                        Buy for <span class="cost">${formatNumber(upgrade.cost)}</span> Clicks
                    </button>
                `;
                upgradesContainer.appendChild(upgradeCard);
            });
        }

        upgradesContainer.addEventListener('click', (event) => {
            const button = event.target.closest('.buy-button');
            if (button) {
                const upgradeId = button.dataset.upgradeId;
                buyUpgrade(upgradeId);
            }
        });

        async function buyUpgrade(upgradeId) {
            const upgrade = upgrades.find(up => up.id === upgradeId);
            if (clicks >= upgrade.cost) {
                // Play upgrade sound if all sounds are enabled
                if (soundState === 2) {
                    await Tone.start();
                    upgradeSynth.triggerAttackRelease(["C5", "E5"], "8n");
                }
                
                clicks -= upgrade.cost;
                upgrade.count++;
                totalUpgrades++;
                upgrade.cost = Math.round(upgrade.initialCost * Math.pow(1.15, upgrade.count)); // Exponential cost increase

                updateDisplay();
                renderUpgrades(); // Re-render to update the cost and count
            }
        }
        
        function renderAchievements() {
            achievementList.innerHTML = '';
            achievements.forEach(achievement => {
                const achievementEl = document.createElement('div');
                achievementEl.className = `p-2 rounded-lg ${achievement.unlocked ? 'bg-yellow-200 dark:bg-yellow-700' : 'bg-gray-200 dark:bg-gray-600'} transition-colors duration-300`;
                achievementEl.innerHTML = `
                    <p class="font-bold">${achievement.unlocked ? '✅' : '🔒'} ${achievement.name}</p>
                    <p class="text-sm text-gray-600 dark:text-gray-400">${achievement.description}</p>
                `;
                achievementList.appendChild(achievementEl);
            });
        }

        async function showAchievementNotification(name) {
            achievementNotification.querySelector('p').textContent = `Achievement Unlocked: ${name}`;
            achievementNotification.classList.remove('hidden');

            // Play achievement sound if all sounds are enabled
            if (soundState === 2) {
                await Tone.start();
                achievementSynth.triggerAttackRelease("C4", "16n");
            }

            setTimeout(() => {
                achievementNotification.classList.add('hidden');
            }, 3000);
        }

        // Prestige button click handler
        prestigeButton.addEventListener('click', () => {
            if (clicks >= PRESTIGE_COST) {
                const gain = Math.floor(clicks / (PRESTIGE_COST / 10)); // Example gain
                prestigePoints += gain;
                resetGame();
                updateDisplay();
                saveGame(); // Save after prestiging
            }
        });

        function resetGame() {
            clicks = 0;
            clicksPerSecond = 0;
            clicksPerClick = 1;
            totalManualClicks = 0;
            totalUpgrades = 0;
            upgrades.forEach(upgrade => {
                upgrade.count = 0;
                upgrade.cost = upgrade.initialCost;
            });
            achievements.forEach(achievement => achievement.unlocked = false);
            renderUpgrades();
            renderAchievements();
        }

        // Refactored click logic into a single function
        async function handleButtonClick() {
            clicks += clicksPerClick;
            totalManualClicks++;
            mainButton.classList.add('animate-bounce');
            setTimeout(() => {
                mainButton.classList.remove('animate-bounce');
            }, 300);

            // Play the click sound if all sounds are enabled
            if (soundState === 2) {
                await Tone.start();
                clickSynth.triggerAttackRelease("C5", "8n");
            }
            
            updateDisplay();
        }

        // Main button click handler
        mainButton.addEventListener('click', handleButtonClick);

        // --- Save and Load Game Functions ---
        function saveGame() {
            const gameState = {
                clicks,
                clicksPerSecond,
                clicksPerClick,
                totalManualClicks,
                totalUpgrades,
                prestigePoints,
                soundState,
                upgrades: upgrades.map(u => ({ id: u.id, count: u.count, cost: u.cost })),
                achievements: achievements.map(a => ({ id: a.id, unlocked: a.unlocked }))
            };
            localStorage.setItem('idleClickerSave', JSON.stringify(gameState));
        }

        function loadGame() {
            const savedState = localStorage.getItem('idleClickerSave');
            if (savedState) {
                const gameState = JSON.parse(savedState);
                clicks = gameState.clicks;
                clicksPerSecond = gameState.clicksPerSecond;
                clicksPerClick = gameState.clicksPerClick;
                totalManualClicks = gameState.totalManualClicks;
                totalUpgrades = gameState.totalUpgrades;
                prestigePoints = gameState.prestigePoints || 0;
                soundState = gameState.soundState || 0;

                // Load upgrades
                gameState.upgrades.forEach(loadedUpgrade => {
                    const upgrade = upgrades.find(u => u.id === loadedUpgrade.id);
                    if (upgrade) {
                        upgrade.count = loadedUpgrade.count;
                        upgrade.cost = loadedUpgrade.cost;
                    }
                });

                // Load achievements
                gameState.achievements.forEach(loadedAchievement => {
                    const achievement = achievements.find(a => a.id === loadedAchievement.id);
                    if (achievement) {
                        achievement.unlocked = loadedAchievement.unlocked;
                    }
                });
            }
            // Set initial button state
            musicToggle.textContent = soundStates[soundState];
        }
        
        // Auto-increment clicks per second
        setInterval(() => {
            clicks += clicksPerSecond;
            updateDisplay();
        }, 1000);

        // Auto-save game every 5 seconds
        setInterval(saveGame, 5000);

        // Initial calls to set up the display
        document.addEventListener('DOMContentLoaded', () => {
            loadGame();
            renderUpgrades();
            renderAchievements();
            updateDisplay();

            // Disable the right-click context menu
            document.addEventListener('contextmenu', (e) => {
                e.preventDefault();
            });

            // Add the keydown event listener for the space bar
            document.addEventListener('keydown', (e) => {
                if (e.key === ' ') {
                    e.preventDefault(); // Prevents the page from scrolling
                    handleButtonClick();
                } else if (e.key === 's') {
                    e.preventDefault();
                    musicToggle.click();
                }
            });
        });
    </script>
</body>
</html>
