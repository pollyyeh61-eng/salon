<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>美髮經營課程</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
            padding: 1rem;
        }
        @media (min-width: 640px) {
            body {
                padding: 2rem;
            }
        }
        .container {
            max-width: 64rem;
            margin: auto;
            background-color: white;
            border-radius: 1.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            padding: 1.5rem;
            border-width: 4px;
            border-color: #a855f7;
        }
        @media (min-width: 640px) {
            .container {
                padding: 2.5rem;
            }
        }
        .text-center {
            text-align: center;
        }
        .title {
            font-size: 2.25rem;
            line-height: 2.5rem;
            font-weight: 800;
            background-image: linear-gradient(to right, #9333ea, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }
        @media (min-width: 640px) {
            .title {
                font-size: 3rem;
                line-height: 1;
            }
        }
        .subtitle {
            color: #6b7280;
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        @media (min-width: 640px) {
            .subtitle {
                font-size: 1rem;
                line-height: 1.5rem;
            }
        }
        .grid-container {
            display: grid;
            gap: 1rem;
            margin-bottom: 2rem;
            text-align: center;
        }
        @media (min-width: 640px) {
            .grid-container {
                grid-template-columns: repeat(3, minmax(0, 1fr));
            }
        }
        .data-card {
            background-color: #f3e8ff;
            border-radius: 0.75rem;
            padding: 1rem;
            box-shadow: inset 0 2px 4px 0 rgba(0, 0, 0, 0.06);
        }
        .data-label {
            color: #6b7280;
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        .data-value {
            font-size: 1.5rem;
            line-height: 2rem;
            font-weight: 700;
            color: #7e22ce;
            margin-top: 0.25rem;
        }
        .progress-bar {
            position: relative;
            padding-top: 0.25rem;
            margin-top: 0.5rem;
        }
        .progress-bar-bg {
            overflow: hidden;
            height: 1rem;
            margin-bottom: 1rem;
            font-size: 0.75rem;
            display: flex;
            border-radius: 9999px;
            background-color: #e9d5ff;
        }
        .progress-bar-inner {
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
            display: flex;
            flex-direction: column;
            text-align: center;
            white-space: nowrap;
            color: white;
            justify-content: center;
            background-image: linear-gradient(to right, #9333ea, #ec4899);
            border-radius: 9999px;
            transition: width 0.5s ease-in-out;
        }
        .modules-container {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }
        .module-card {
            padding: 1.5rem;
            border-radius: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            border-width: 2px;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
        }
        .module-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        .module-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }
        .module-title {
            font-size: 1.125rem;
            line-height: 1.75rem;
            font-weight: 700;
        }
        @media (min-width: 640px) {
            .module-title {
                font-size: 1.25rem;
                line-height: 1.75rem;
            }
        }
        .module-subtitle {
            font-size: 0.875rem;
            line-height: 1.25rem;
            font-style: italic;
            margin-bottom: 1rem;
        }
        .module-content {
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        .module-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 1rem;
        }
        .module-points {
            font-size: 0.875rem;
            line-height: 1.25rem;
            font-weight: 600;
        }
        .module-button {
            padding: 0.5rem 1rem;
            border-radius: 9999px;
            font-weight: 600;
            color: white;
            transition-property: background-color;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 150ms;
        }
        .locked {
            filter: grayscale(80%);
            cursor: not-allowed;
            background-color: #f3f4f6;
            color: #9ca3af;
            border-color: #d1d5db;
        }
        .locked .lock-icon {
            display: block;
        }
        .unlocked .lock-icon {
            display: none;
        }
        .locked button {
            background-color: #9ca3af;
        }
        .completed {
            background-color: #f0fdf4;
            color: #166534;
            border-color: #22c55e;
        }
        .completed button {
            background-color: #22c55e;
        }
        .uncompleted {
            background-color: #f5f3ff;
            color: #6b21a8;
            border-color: #8b5cf6;
        }
        .uncompleted button {
            background-color: #7c3aed;
        }
        .uncompleted button:hover {
            background-color: #6d28d9;
        }
        .message-container {
            margin-top: 2rem;
            display: none;
            background-color: #dcfce7;
            border-left-width: 4px;
            border-color: #22c55e;
            color: #15803d;
            padding: 1rem;
            border-radius: 0.75rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        .message-container.visible {
            display: block;
        }
        .message-title {
            font-weight: 700;
        }
        /* Video Modal Styles */
        .video-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            padding: 1rem;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0s, opacity 0.5s linear;
        }
        .video-modal.visible {
            visibility: visible;
            opacity: 1;
        }
        .video-modal-content {
            background-color: white;
            border-radius: 1.5rem;
            padding: 1.5rem;
            width: 100%;
            max-width: 768px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            position: relative;
        }
        .video-player-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            margin-bottom: 1rem;
            border-radius: 1rem;
            overflow: hidden;
        }
        .video-player-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 1rem;
        }
        .close-button {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background-color: #fca5a5;
            color: white;
            border: none;
            width: 2.5rem;
            height: 2.5rem;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            font-size: 1.5rem;
            line-height: 1;
        }
        /* 新增：用於隱藏/顯示按鈕 */
        .hidden {
            display: none;
        }
    </style>
</head>
<body class="p-4 sm:p-8">
    <div class="container">
        <div class="text-center mb-8">
            <h1 class="title">美髮經營策略家</h1>
            <p class="subtitle">美髮經營課程 | 讓您成為頂尖沙龍管理者！</p>
        </div>

        <div class="grid-container">
            <div class="data-card">
                <p class="data-label">當前等級</p>
                <p id="player-level" class="data-value">初階學徒</p>
            </div>
            <div class="data-card">
                <p class="data-label">學習點數</p>
                <p id="player-points" class="data-value">0</p>
            </div>
            <div class="data-card">
                <p class="data-label">課程進度</p>
                <div class="progress-bar">
                    <div class="progress-bar-bg">
                        <div id="progress-bar" style="width: 0%" class="progress-bar-inner"></div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="text-center text-sm text-gray-500 mb-8">
            <p id="user-id-display" class="break-words">使用者ID: 載入中...</p>
            <p id="status-display" class="font-bold text-blue-500">正在連接...</p>
        </div>

        <div class="modules-container" id="modules-container">
            <div id="loading-spinner" class="text-center py-10">
                <div class="animate-spin rounded-full h-12 w-12 border-t-4 border-b-4 border-purple-500 mx-auto"></div>
                <p class="text-gray-500 mt-4">載入進度中...</p>
            </div>
        </div>

        <div id="message-container" class="message-container">
            <p class="message-title">恭喜！</p>
            <p id="message-text">您已完成本模組！</p>
        </div>
    </div>

    <div id="video-modal" class="video-modal hidden">
        <div class="video-modal-content">
            <h3 id="video-modal-title" class="text-2xl font-bold text-center mb-4 text-gray-800">影片標題</h3>
            <div class="video-player-container">
                <video id="video-player" controls preload="metadata">
                    您的瀏覽器不支援影片播放。
                </video>
            </div>
            <div class="flex flex-col sm:flex-row justify-center space-y-4 sm:space-y-0 sm:space-x-4">
                <p id="video-complete-message" class="hidden text-center text-sm text-green-600 font-bold">影片已播放完畢，您可以領取點數了！</p>
                <button id="complete-task-btn" class="module-button w-full sm:w-auto bg-green-600 hover:bg-green-700 hidden">完成任務並領取點數</button>
                <button id="close-modal-btn" class="module-button w-full sm:w-auto bg-gray-500 hover:bg-gray-600">返回課程</button>
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "firebase/app";
        import { getAuth, signInAnonymously, onAuthStateChanged } from "firebase/analytics";
        import { getFirestore, doc, getDoc, setDoc } from "firebase/analytics";

        const firebaseConfig = {
            apiKey: "AIzaSyCOhBN9TH3UJSOSx5XVyQ08f_2RUckvXYU",
            authDomain: "holyhairsalon-f73bf.firebaseapp.com",
            projectId: "holyhairsalon-f73bf",
            storageBucket: "holyhairsalon-f73bf.firebasestorage.app",
            messagingSenderId: "960169055224",
            appId: "1:960169055224:web:4f8a45c0d3e31a93bf3c0d",
            measurementId: "G-BC8J4V9NLP"
        };
        
        let db, auth;
        let userId = '';
        const app_id = "hair_salon_course";

        try {
            const app = initializeApp(firebaseConfig);
            auth = getAuth(app);
            db = getFirestore(app);
        } catch (error) {
            console.error("Firebase initialization failed:", error);
            document.getElementById('status-display').textContent = '初始化失敗，請檢查設定。';
        }

        const gameDataCollection = `artifacts/${app_id}/users/`;

        const gameState = {
            points: 0,
            level: '初階學徒',
            currentModuleIndex: 0,
            modules: [
                {
                    title: '0. 為何要創業',
                    subtitle: '了解自己適合創業嗎?',
                    content: '要找工作還是自己當老闆',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1gbZn2DTvHiE2B_G06nERXb-Q7AuQvFIh/preview'
                },
                {
                    title: '1. 市場調查',
                    subtitle: '我的競爭對手是誰？',
                    content: '只有進行市場調查才能幫助我們找到答案',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1U8qQb6Ob_0pLR-KxtTLDnYcuh0fqqFtW/preview'
                },
                {
                    title: '2. 目標客群分析',
                    subtitle: '了解潛在顧客',
                    content: '目標客群分析是針對你的美髮創業展店來識別。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1K4_D47lq7gVnBl-OFApHuedFwgC3KAjV/preview'
                },
                {
                    title: '3.競爭者研究',
                    subtitle: '制定有效策略',
                    content: '競爭者研究是瞭解你的美髮創業展店在市場環境中的位置',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1O5YKOSNwJkiSZS_4sjJvEI0dwKD-CxnR/preview'
                },
                {
                    title: '4.行業趨勢與需求評估',
                    subtitle: '了解市場及需求者',
                    content: '針對市場環境及人口變化做綜合評估',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1cC2envJ3VySRqNahyUsLbST1U5Nw-T2I/preview'
                },
                {
                    title: '5.專業化美髮定位',
                    subtitle: '具備獨特性',
                    content: '沙龍如何在眾多競爭對手中脫穎而出',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1mx6dCQx22q7MVAMaiH3B5570xDGb8etg/preview'
                },
                {
                    title: '6.選址與佈置',
                    subtitle: '選址與佈置是沙龍創業的基石，也是成功的開始',
                    content: '一個好的店址不僅能吸引目標客群，更能提升品牌形象。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1kvB1EkXtp1xxtduubgPEPKtc_uJu7eK4/preview'
                },
                {
                    title: '7.服務專案',
                    subtitle: '品牌就像是你的臉',
                    content: '視覺吸引力、品牌故事、互動體驗。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/11M2Wpx8cTDlYxyzImPhtniOZUhLXtdiH/preview'
                },
                {
                    title: '8.供應鏈管理',
                    subtitle: '提升效率、降低成本',
                    content: '良好的供應鏈管理能確保沙龍穩定經營。',
                    points: 100,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1kvB1EkXtp1xxtduubgPEPKtc_uJu7eK4/preview'
                },
                {
                    title: '9.人力資源規劃',
                    subtitle: '人員招聘到團隊管理策略',
                    content: '開設一間成功的沙龍，不僅需要好的地點和產品，還需要一支高效且團結的團隊。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/16yrBQAjmQYj5fwOPvvZ5m8LRE287YWQ2/preview'
                },
                {
                    title: '10.高端客戶服務',
                    subtitle: '為高端客戶提供專屬的服務體驗',
                    content: '高端客戶不僅帶來穩定的收入，更能提升品牌形象。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1kXaekwIciXsdwGy4pKnCyuMkohfOzvo_/preview'
                },
                {
                    title: '11.法律與合規',
                    subtitle: '開設沙龍所需的法律知識與合規要求',
                    content: '合法經營不僅能避免潛在風險，更能建立客戶與員工的信任。',
                    points: 50,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1LmhYPbc-jUBJhtUWv11kIBoXy60yizrJ/preview'
                },
                {
                    title: '12.財務管理流程',
                    subtitle: '財務管理流程',
                    content: '財務管理是每一位創業者都需要重視的核心環節。',
                    points: 100,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/18GQ8LguusbO7nKHRNl9dwdzFmRi1H-Be/preview'
                },
                {
                    title: '13.低成本創業',
                    subtitle: '低成本創業',
                    content: '如何做低成本創業。',
                    points: 100,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1gY-HmrC_qWmHTOJJ3vV_lnMiN32_RpEH/preview'
                },
                {
                    title: '14.獲客變現',
                    subtitle: '獲客變現',
                    content: '低成本行銷也能獲客變現。',
                    points: 100,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1XWDIlKWw_ueGTIhfW8tld2KPp1jD_TBt/preview'
                }
            ]
        };

        const playerLevelMap = [
            { threshold: 0, name: '初階學徒' },
            { threshold: 300, name: '中階經營者' },
            { threshold: 600, name: '高階策略師' },
            { threshold: 1000, name: '課程畢業生' }
        ];

        // UI Elements
        const modulesContainer = document.getElementById('modules-container');
        const playerPointsEl = document.getElementById('player-points');
        const playerLevelEl = document.getElementById('player-level');
        const progressBarEl = document.getElementById('progress-bar');
        const messageContainer = document.getElementById('message-container');
        const messageTextEl = document.getElementById('message-text');
        const loadingSpinner = document.getElementById('loading-spinner');
        const statusDisplay = document.getElementById('status-display');
        const userIdDisplay = document.getElementById('user-id-display');

        // Video Modal Elements
        const videoModal = document.getElementById('video-modal');
        const videoModalTitle = document.getElementById('video-modal-title');
        const videoPlayer = document.getElementById('video-player');
        const completeTaskBtn = document.getElementById('complete-task-btn');
        const closeModalBtn = document.getElementById('close-modal-btn');
        const videoCompleteMessage = document.getElementById('video-complete-message');
        let currentModuleIndex = -1;

        // --- Firebase Integration Functions ---
        async function loadGameState() {
            if (!userId) {
                console.error("User ID is not set. Cannot load game state.");
                return;
            }
            statusDisplay.textContent = '正在載入進度...';
            try {
                const docRef = doc(db, gameDataCollection, userId);
                const docSnap = await getDoc(docRef);

                if (docSnap.exists()) {
                    const savedState = docSnap.data();
                    gameState.points = savedState.points || 0;
                    gameState.currentModuleIndex = savedState.currentModuleIndex || 0;
                    if (savedState.modules) {
                        gameState.modules.forEach((module, index) => {
                            if (savedState.modules[index]) {
                                module.completed = savedState.modules[index].completed;
                            }
                        });
                    }
                    console.log("Game state loaded from Firestore.");
                    statusDisplay.textContent = '進度載入完成！';
                } else {
                    console.log("No saved game state found. Starting new game.");
                    statusDisplay.textContent = '新遊戲已啟動。';
                }
            } catch (e) {
                console.error("Error loading game state:", e);
                statusDisplay.textContent = '載入進度失敗，請重新整理。';
            } finally {
                loadingSpinner.style.display = 'none';
                updateUI();
            }
        }

        async function saveGameState() {
            if (!userId) {
                console.error("User ID is not set. Cannot save game state.");
                return;
            }
            try {
                const docRef = doc(db, gameDataCollection, userId);
                await setDoc(docRef, {
                    points: gameState.points,
                    currentModuleIndex: gameState.currentModuleIndex,
                    modules: gameState.modules.map(m => ({ completed: m.completed }))
                });
                console.log("Game state saved to Firestore.");
            } catch (e) {
                console.error("Error saving game state:", e);
            }
        }

        // --- UI and Game Logic Functions ---

        // Update UI state
        function updateUI() {
            playerPointsEl.textContent = gameState.points;
            const currentLevel = playerLevelMap.find(level => gameState.points >= level.threshold) || playerLevelMap[0];
            playerLevelEl.textContent = currentLevel.name;

            const totalModules = gameState.modules.length;
            const completedModules = gameState.modules.filter(m => m.completed).length;
            const progressPercentage = (completedModules / totalModules) * 100;
            progressBarEl.style.width = `${progressPercentage}%`;

            renderModules();
        }

        // Render module cards
        function renderModules() {
            modulesContainer.innerHTML = '';
            loadingSpinner.style.display = 'none';
            gameState.modules.forEach((module, index) => {
                const isLocked = index > gameState.currentModuleIndex;
                const isCompleted = module.completed;
                
                let cardClass = 'module-card';
                let buttonText = '';

                if (isLocked) {
                    cardClass += ' locked';
                    buttonText = '鎖定中';
                } else if (isCompleted) {
                    cardClass += ' completed';
                    buttonText = '已完成';
                } else {
                    cardClass += ' uncompleted';
                    buttonText = '開始學習';
                }

                const cardHtml = `
                    <div class="${cardClass}" data-index="${index}">
                        <div class="module-header">
                            <h2 class="module-title">${module.title}</h2>
                            <div class="lock-icon text-xl text-gray-400">🔒</div>
                            <div class="completion-icon text-xl text-green-500 ${isCompleted ? '' : 'hidden'}">✅</div>
                        </div>
                        <p class="module-subtitle">${module.subtitle}</p>
                        <p class="module-content">${module.content}</p>
                        <div class="module-footer">
                            <span class="module-points">獲得點數: +${module.points}</span>
                            <button class="module-button" ${isLocked || isCompleted ? 'disabled' : ''}>
                                ${buttonText}
                            </button>
                        </div>
                    </div>
                `;
                modulesContainer.innerHTML += cardHtml;
            });

            document.querySelectorAll('.module-card button').forEach(button => {
                button.addEventListener('click', handleModuleClick);
            });
        }

        function handleModuleClick(event) {
            const card = event.currentTarget.closest('.module-card');
            const index = parseInt(card.dataset.index);
            const module = gameState.modules[index];

            if (index > gameState.currentModuleIndex || module.completed) {
                return;
            }
            
            currentModuleIndex = index;
            openVideoModal(module.videoUrl, module.title);
        }

        function openVideoModal(videoUrl, title) {
            videoModalTitle.textContent = title;
            videoPlayer.src = videoUrl;
            videoModal.classList.add('visible');
            videoModal.classList.remove('hidden');
            
            completeTaskBtn.classList.add('hidden');
            videoCompleteMessage.classList.add('hidden');
            videoPlayer.load();
        }

        function closeVideoModal() {
            videoPlayer.pause();
            videoPlayer.src = '';
            videoModal.classList.remove('visible');
            videoModal.classList.add('hidden');
        }

        async function completeTask() {
            const module = gameState.modules[currentModuleIndex];
            if (!module) return;

            // Prevent duplicate clicks
            if (module.completed) {
                showMessage("此模組已完成，請勿重複領取點數。");
                return;
            }

            gameState.points += module.points;
            module.completed = true;

            if (currentModuleIndex < gameState.modules.length - 1) {
                gameState.currentModuleIndex = currentModuleIndex + 1;
            }

            await saveGameState();
            showMessage(`恭喜完成《${module.title}》！獲得 ${module.points} 點數。`);
            updateUI();
            closeVideoModal();
        }
        
        videoPlayer.addEventListener('ended', () => {
            completeTaskBtn.classList.remove('hidden');
            videoCompleteMessage.classList.remove('hidden');
        });

        completeTaskBtn.addEventListener('click', completeTask);
        closeModalBtn.addEventListener('click', closeVideoModal);

        function showMessage(text) {
            messageContainer.classList.add('visible');
            messageTextEl.textContent = text;
            
            setTimeout(() => {
                messageContainer.classList.remove('visible');
            }, 3000);
        }

        onAuthStateChanged(auth, async (user) => {
            if (user) {
                userId = user.uid;
                userIdDisplay.textContent = `使用者ID: ${userId}`;
                statusDisplay.textContent = '已連接。';
                await loadGameState();
            } else {
                try {
                    await signInAnonymously(auth);
                } catch (error) {
                    console.error("Authentication error: ", error);
                    userIdDisplay.textContent = '使用者ID: 認證失敗';
                    statusDisplay.textContent = '認證失敗，請重新載入。';
                    loadingSpinner.style.display = 'none';
                    renderModules();
                }
            }
        });
    </script>
</body>
</html>
