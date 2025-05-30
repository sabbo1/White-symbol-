<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>White Symbol</title>
  <script src="https://telegram.org/js/telegram-web-app.js"></script>
  <style>
    /* Main App Styles */
    #main-app {
      display: block;
      background: #000;
      color: #fff;
      min-height: 100vh;
      overflow: hidden;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Arial', sans-serif;
    }

    .header {
      padding: 20px;
      text-align: center;
      border-bottom: 1px solid #333;
      position: relative;
    }

    .logo {
      font-size: 2.5rem;
      font-weight: bold;
      color: #fff;
      margin-bottom: 10px;
      text-transform: uppercase;
    }

    .logo-highlight {
      color: #ff0000;
    }

    .community-buttons {
      display: flex;
      gap: 10px;
      justify-content: center;
      margin-bottom: 15px;
    }

    .community-btn {
      background: #2eaddc;
      color: #000;
      padding: 8px 15px;
      border-radius: 20px;
      font-weight: bold;
      font-size: 0.9rem;
      text-decoration: none;
      transition: transform 0.2s;
    }

    .community-btn:hover {
      transform: scale(1.05);
    }

    .tab-content {
      flex: 1;
      padding: 20px;
      display: none;
      padding-bottom: 70px;
      height: calc(100vh - 180px);
      overflow-y: auto;
    }

    .tab-content::-webkit-scrollbar {
      display: none;
    }

    .tab-content {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }

    .tab-content.active {
      display: block;
    }

    .tab-bar {
      display: flex;
      background: #111;
      padding: 10px 0;
      position: fixed;
      bottom: 0;
      width: 100%;
      border-top: 1px solid #333;
    }

    .tab {
      flex: 1;
      text-align: center;
      cursor: pointer;
      font-weight: bold;
      font-size: 12px;
      text-transform: uppercase;
      color: #888;
      transition: all 0.3s;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
    }

    .tab.active {
      color: #2eaddc;
    }

    .tab-icon {
      font-size: 18px;
    }

    h2 {
      color: #2eaddc;
      margin-bottom: 20px;
      font-size: 22px;
      text-transform: uppercase;
    }

    p {
      color: #ccc;
      line-height: 1.6;
      margin-bottom: 20px;
    }

    .welcome-container {
      display: flex;
      justify-content: center;
      align-items: flex-start;
      height: auto;
      margin-top: 20px;
      text-align: center;
    }

    .welcome-text {
      color: #2eaddc;
      font-size: 2rem;
      font-weight: bold;
      text-transform: uppercase;
      padding: 20px;
      border: 2px solid #2eaddc;
      border-radius: 10px;
      background-color: rgba(46, 173, 220, 0.1);
      max-width: 90%;
      margin-top: 0;
    }

    .task {
      background: #222;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 15px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .task.hidden {
      display: none;
    }

    .task-info {
      flex: 1;
    }

    .task-title {
      font-weight: bold;
      margin-bottom: 5px;
      color: #2eaddc;
    }

    .task-reward {
      color: #4CAF50;
      font-size: 0.9rem;
    }

    .task-btn {
      background: #2eaddc;
      color: #000;
      border: none;
      padding: 8px 15px;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
      white-space: nowrap;
    }

    .task-btn:hover {
      background: #1d8cb5;
    }

    .task-btn.completed {
      background: #4CAF50;
      cursor: default;
    }

    .task-btn.verify {
      background: #FF9800;
    }

    .balance-box {
      background: #222;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 15px;
      text-align: center;
    }

    .balance-title {
      font-size: 1rem;
      color: #aaa;
      margin-bottom: 5px;
    }

    .balance-amount {
      font-size: 1.5rem;
      color: #2eaddc;
      font-weight: bold;
    }

    .referral-container {
      background: #222;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .referral-title {
      color: #2eaddc;
      font-weight: bold;
      margin-bottom: 15px;
      font-size: 1.2rem;
    }

    .referral-code {
      background: #333;
      padding: 15px;
      border-radius: 5px;
      font-family: monospace;
      font-size: 1.2rem;
      text-align: center;
      margin-bottom: 15px;
      word-break: break-all;
    }

    .invite-btn {
      background: #2eaddc;
      color: #000;
      border: none;
      padding: 12px 20px;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
      width: 100%;
      margin-bottom: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      font-size: 1rem;
    }

    .invite-btn:hover {
      background: #1d8cb5;
    }

    .invite-icon {
      font-size: 1.2rem;
    }

    .referral-stats {
      display: flex;
      justify-content: space-between;
      margin-top: 15px;
    }

    .stat-box {
      background: #333;
      padding: 10px;
      border-radius: 5px;
      text-align: center;
      flex: 1;
      margin: 0 5px;
    }

    .stat-number {
      font-size: 1.3rem;
      font-weight: bold;
      color: #2eaddc;
    }

    .stat-label {
      font-size: 0.8rem;
      color: #aaa;
    }

    .invited-friends {
      margin-top: 20px;
    }

    .friend-item {
      background: #222;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .friend-name {
      font-weight: bold;
    }

    .friend-date {
      color: #aaa;
      font-size: 0.8rem;
    }

    .friend-tokens {
      color: #4CAF50;
      font-weight: bold;
    }

    .verification-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.8);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .verification-content {
      background: #222;
      padding: 20px;
      border-radius: 10px;
      width: 90%;
      max-width: 400px;
      text-align: center;
    }

    .verification-title {
      color: #2eaddc;
      font-size: 1.2rem;
      margin-bottom: 15px;
    }

    .verification-btn {
      background: #2eaddc;
      color: #000;
      border: none;
      padding: 10px 15px;
      border-radius: 5px;
      font-weight: bold;
      cursor: pointer;
      margin: 10px 5px;
    }

    .verification-btn.cancel {
      background: #f44336;
    }

    .admin-panel {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.9);
      z-index: 2000;
      overflow-y: auto;
      padding: 20px;
    }

    .admin-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .admin-title {
      color: #2eaddc;
      font-size: 1.5rem;
    }

    .close-admin {
      background: #f44336;
      color: white;
      border: none;
      padding: 8px 15px;
      border-radius: 5px;
      cursor: pointer;
    }

    .user-table {
      width: 100%;
      border-collapse: collapse;
    }

    .user-table th, .user-table td {
      padding: 12px 15px;
      text-align: left;
      border-bottom: 1px solid #333;
    }

    .user-table th {
      background-color: #222;
      color: #2eaddc;
    }

    .user-table tr:hover {
      background-color: #222;
    }

    .admin-btn {
      position: fixed;
      top: 10px;
      left: 10px;
      background: #ff0000;
      color: white;
      border: none;
      padding: 8px 15px;
      border-radius: 5px;
      cursor: pointer;
      z-index: 1000;
    }

    .spinner {
      border: 4px solid rgba(0, 0, 0, 0.1);
      border-radius: 50%;
      border-top: 4px solid #2eaddc;
      width: 30px;
      height: 30px;
      animation: spin 1s linear infinite;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .verification-steps {
      margin-bottom: 15px;
      text-align: left;
    }

    .verification-step {
      display: flex;
      align-items: center;
      margin-bottom: 8px;
    }

    .step-number {
      background: #2eaddc;
      color: #000;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 10px;
      font-weight: bold;
      font-size: 12px;
    }

    .step-text {
      color: #ccc;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <!-- Main App -->
  <div id="main-app">
    <button class="admin-btn" id="adminBtn" style="display:none;">ADMIN</button>
    
    <div class="header">
      <div class="logo">WH<span class="logo-highlight">I</span>TE SYMBOL</div>
      <div class="community-buttons">
        <a href="https://t.me/whitesymbo" class="community-btn" target="_blank">JOIN OUR COMMUNITY</a>
        <a href="https://x.com/whitesymbol15?t=DmMQSl8PtoEb4AfRKYjlig&s=09" class="community-btn" target="_blank">JOIN OUR X COMMUNITY</a>
      </div>
    </div>

    <div id="home" class="tab-content active">
      <h2>Welcome</h2>
      <p>WHITE SYMBOL community platform</p>
      <div class="welcome-container">
        <div class="welcome-text">WELCOME TO WHITE SYMBOL MINI APP</div>
      </div>
    </div>

    <div id="earn" class="tab-content">
      <h2>EARN TOKENS</h2>
      <p>Complete tasks to earn 100 SYM tokens each</p>
      
      <div class="task" id="telegramTask">
        <div class="task-info">
          <div class="task-title">Join Telegram Community</div>
          <div class="task-reward">Reward: 100 SYM</div>
        </div>
        <button class="task-btn verify" id="telegramTaskBtn">Verify</button>
      </div>
      
      <div class="task" id="twitterTask">
        <div class="task-info">
          <div class="task-title">Follow on X (Twitter)</div>
          <div class="task-reward">Reward: 100 SYM</div>
        </div>
        <button class="task-btn verify" id="twitterTaskBtn">Verify</button>
      </div>
      
      <div class="task" id="shareTask">
        <div class="task-info">
          <div class="task-title">Share on Social Media</div>
          <div class="task-reward">Reward: 100 SYM</div>
        </div>
        <button class="task-btn verify" id="shareTaskBtn">Verify</button>
      </div>
      
      <div class="task" id="inviteTask">
        <div class="task-info">
          <div class="task-title">Invite Friends</div>
          <div class="task-reward">Reward: 100 SYM per friend</div>
        </div>
        <button class="task-btn" id="inviteTaskBtn">Invite</button>
      </div>
    </div>

    <div id="balance" class="tab-content">
      <h2>YOUR BALANCE</h2>
      
      <div class="balance-box">
        <div class="balance-title">Total Balance</div>
        <div class="balance-amount" id="tokenBalance">0 SYM</div>
      </div>
      
      <div class="balance-box">
        <div class="balance-title">Earned from Tasks</div>
        <div class="balance-amount" id="earnedFromTasks">0 SYM</div>
      </div>
      
      <div class="balance-box">
        <div class="balance-title">Friends Joined</div>
        <div class="balance-amount" id="totalReferrals">0</div>
      </div>
      
      <div class="balance-box">
        <div class="balance-title">Earned from Referrals</div>
        <div class="balance-amount" id="earnedFromReferrals">0 SYM</div>
      </div>
    </div>

    <div id="friends" class="tab-content">
      <h2>FRIENDS</h2>
      <p>Invite friends and earn 100 SYM tokens when they participate</p>
      
      <div class="referral-container">
        <div class="referral-title">Invite Friends & Earn Tokens</div>
        <div class="referral-code" id="referralCode">https://t.me/whitesymbol_bot?start=USER123</div>
        <button class="invite-btn" id="inviteBtn">
          <span class="invite-icon">📩</span> INVITE FRIEND
        </button>
        
        <div class="referral-stats">
          <div class="stat-box">
            <div class="stat-number" id="totalReferrals2">0</div>
            <div class="stat-label">Friends Joined</div>
          </div>
          <div class="stat-box">
            <div class="stat-number" id="earnedFromReferrals2">0</div>
            <div class="stat-label">Earned SYM</div>
          </div>
        </div>
      </div>
      
      <div class="invited-friends">
        <h3>Your Invited Friends</h3>
        <div id="friendsList">
          <div class="friend-item">
            <div class="friend-info">
              <div class="friend-name">No friends joined yet</div>
              <div class="friend-date">Tokens earned when friends participate</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="tab-bar">
      <div class="tab active" data-tab="home">
        <div class="tab-icon">🏠</div>
        <div>HOME</div>
      </div>
      <div class="tab" data-tab="earn">
        <div class="tab-icon">💰</div>
        <div>EARN</div>
      </div>
      <div class="tab" data-tab="balance">
        <div class="tab-icon">💎</div>
        <div>BALANCE</div>
      </div>
      <div class="tab" data-tab="friends">
        <div class="tab-icon">👥</div>
        <div>FRIENDS</div>
      </div>
    </div>

    <div class="verification-modal" id="verificationModal">
      <div class="verification-content">
        <div class="verification-title" id="verificationTitle">Verify Task</div>
        <div class="verification-steps" id="verificationSteps">
          <!-- Steps will be added dynamically -->
        </div>
        <p id="verificationText">Please complete the steps above to verify</p>
        <div>
          <button class="verification-btn" id="verifyActionBtn">Verify</button>
          <button class="verification-btn cancel" onclick="closeVerificationModal()">Cancel</button>
        </div>
      </div>
    </div>
  </div>

  <div class="admin-panel" id="adminPanel">
    <div class="admin-header">
      <h2 class="admin-title">Admin Dashboard - User Management</h2>
      <button class="close-admin" onclick="closeAdminPanel()">Close</button>
    </div>
    
    <table class="user-table">
      <thead>
        <tr>
          <th>Username</th>
          <th>Tokens</th>
          <th>Referrals</th>
          <th>Tasks Completed</th>
          <th>Join Date</th>
        </tr>
      </thead>
      <tbody id="userTableBody">
      </tbody>
    </table>
  </div>

  <script>
    let tokenBalance = 0;
    let totalReferrals = 0;
    let earnedFromReferrals = 0;
    let earnedFromTasks = 0;
    let currentVerificationTask = null;
    let completedTasks = {
      telegram: false,
      twitter: false,
      share: false,
      invite: false
    };
    
    let currentUser = {
      id: '',
      username: 'You',
      tokens: 0
    };

    const SOCIAL_LINKS = {
      telegram: "https://t.me/whitesymbo",
      twitter: "https://x.com/whitesymbol15?t=DmMQSl8PtoEb4AfRKYjlig&s=09",
      share: "https://t.me/share/url?url=https://t.me/whitesymbol_bot?start=USER123&text=Join%20WHITE%20SYMBOL%20Community%20and%20earn%20tokens!"
    };

    document.addEventListener('DOMContentLoaded', function() {
      const tg = window.Telegram.WebApp;
      tg.expand();
      
      // Load user data
      loadUserData();
      
      document.getElementById('main-app').style.display = 'block';
      
      const tgUser = tg.initDataUnsafe?.user;
      currentUser.id = tgUser?.id ? "tg_" + tgUser.id.toString() : "user_" + Math.random().toString(36).substring(2, 10);
      currentUser.username = tgUser?.username ? `@${tgUser.username}` : "You";
      
      // Set referral link
      document.getElementById('referralCode').textContent = `https://t.me/whitesymbol_bot?start=${currentUser.id}`;
      SOCIAL_LINKS.share = `https://t.me/share/url?url=https://t.me/whitesymbol_bot?start=${currentUser.id}&text=Join%20WHITE%20SYMBOL%20Community%20and%20earn%20tokens!`;

      // Event listeners
      document.getElementById('telegramTaskBtn').addEventListener('click', function() {
        startTaskVerification('telegram');
      });
      
      document.getElementById('twitterTaskBtn').addEventListener('click', function() {
        startTaskVerification('twitter');
      });
      
      document.getElementById('shareTaskBtn').addEventListener('click', function() {
        startTaskVerification('share');
      });
      
      document.getElementById('inviteBtn').addEventListener('click', function() {
        inviteFriend();
      });
      
      document.querySelectorAll('.tab').forEach(tab => {
        tab.addEventListener('click', function() {
          const tabName = this.getAttribute('data-tab');
          openTab(tabName);
        });
      });
      
      // Check for admin
      const ADMIN_USER_ID = "YOUR_TELEGRAM_USER_ID";
      const isAdmin = tgUser?.id === ADMIN_USER_ID;
      if (isAdmin) {
        document.getElementById('adminBtn').style.display = 'block';
        document.getElementById('adminBtn').addEventListener('click', openAdminPanel);
      }
      
      // Check referral
      checkReferral();
      
      // Update UI
      updateTokenBalance();
      updateTaskButtons();
    });
    
    function loadUserData() {
      try {
        const tg = window.Telegram.WebApp;
        const tgUser = tg.initDataUnsafe?.user;
        const userId = tgUser?.id ? "tg_" + tgUser.id.toString() : null;
        
        let savedData = null;
        
        if (userId) {
          savedData = localStorage.getItem(`userData_${userId}`);
        }
        
        if (!savedData) {
          const keys = Object.keys(localStorage);
          for (const key of keys) {
            if (key.startsWith("userData_")) {
              savedData = localStorage.getItem(key);
              break;
            }
          }
        }
        
        if (savedData) {
          const data = JSON.parse(savedData);
          
          if (userId && data.userId && data.userId !== userId) {
            console.log("Data belongs to different user, ignoring");
            resetUserData();
            return;
          }
          
          if (typeof data.tokenBalance === 'number') {
            tokenBalance = data.tokenBalance;
            currentUser.tokens = data.tokenBalance;
          }
          
          if (typeof data.totalReferrals === 'number') {
            totalReferrals = data.totalReferrals;
          }
          
          if (typeof data.earnedFromReferrals === 'number') {
            earnedFromReferrals = data.earnedFromReferrals;
          }
          
          if (typeof data.earnedFromTasks === 'number') {
            earnedFromTasks = data.earnedFromTasks;
          }
          
          if (data.completedTasks) {
            completedTasks = {
              telegram: !!data.completedTasks.telegram,
              twitter: !!data.completedTasks.twitter,
              share: !!data.completedTasks.share,
              invite: !!data.completedTasks.invite
            };
          }
          
          console.log("User data loaded successfully");
        } else {
          console.log("No saved data found, initializing new user");
          resetUserData();
        }
      } catch (e) {
        console.error("Error loading user data:", e);
        resetUserData();
      }
    }
    
    function saveUserData() {
      try {
        const data = {
          tokenBalance: tokenBalance,
          totalReferrals: totalReferrals,
          earnedFromReferrals: earnedFromReferrals,
          earnedFromTasks: earnedFromTasks,
          completedTasks: completedTasks,
          lastUpdated: new Date().toISOString(),
          userId: currentUser.id
        };
        
        localStorage.setItem(`userData_${currentUser.id}`, JSON.stringify(data));
        console.log("User data saved");
      } catch (e) {
        console.error("Error saving user data:", e);
      }
    }
    
    function resetUserData() {
      tokenBalance = 0;
      totalReferrals = 0;
      earnedFromReferrals = 0;
      earnedFromTasks = 0;
      completedTasks = {
        telegram: false,
        twitter: false,
        share: false,
        invite: false
      };
      saveUserData();
    }

    function openTab(tabName) {
      document.querySelectorAll('.tab-content').forEach(tab => {
        tab.classList.remove('active');
      });
      
      document.querySelectorAll('.tab').forEach(tab => {
        tab.classList.remove('active');
      });
      
      document.getElementById(tabName).classList.add('active');
      
      const clickedTab = document.querySelector(`.tab[data-tab="${tabName}"]`);
      if (clickedTab) {
        clickedTab.classList.add('active');
      }
    }
    
    function startTaskVerification(taskType) {
      if (completedTasks[taskType]) {
        alert("You've already completed this task!");
        return;
      }
      
      currentVerificationTask = taskType;
      const modal = document.getElementById('verificationModal');
      const title = document.getElementById('verificationTitle');
      const text = document.getElementById('verificationText');
      const actionBtn = document.getElementById('verifyActionBtn');
      const stepsContainer = document.getElementById('verificationSteps');
      
      stepsContainer.innerHTML = '';
      
      switch(taskType) {
        case 'telegram':
          title.textContent = "Verify Telegram Join";
          
          // Add verification steps
          addVerificationStep(stepsContainer, 1, "Join our Telegram channel");
          addVerificationStep(stepsContainer, 2, "Stay in the channel for verification");
          
          text.textContent = "We'll manually verify your membership";
          actionBtn.textContent = "Join Channel";
          actionBtn.onclick = function() {
            window.open(SOCIAL_LINKS.telegram, '_blank');
            startManualVerification('telegram');
          };
          break;
          
        case 'twitter':
          title.textContent = "Verify Twitter Follow";
          
          // Add verification steps
          addVerificationStep(stepsContainer, 1, "Follow our Twitter page");
          addVerificationStep(stepsContainer, 2, "Wait for manual verification");
          
          text.textContent = "We'll manually verify your follow";
          actionBtn.textContent = "Follow Us";
          actionBtn.onclick = function() {
            window.open(SOCIAL_LINKS.twitter, '_blank');
            startManualVerification('twitter');
          };
          break;
          
        case 'share':
          title.textContent = "Verify Social Share";
          
          // Add verification steps
          addVerificationStep(stepsContainer, 1, "Share our community link");
          addVerificationStep(stepsContainer, 2, "Provide proof of sharing if needed");
          
          text.textContent = "Share on your social media to complete";
          actionBtn.textContent = "Share Now";
          actionBtn.onclick = function() {
            window.open(SOCIAL_LINKS.share, '_blank');
            startManualVerification('share');
          };
          break;
      }
      
      modal.style.display = 'flex';
    }

    function addVerificationStep(container, number, text) {
      const stepDiv = document.createElement('div');
      stepDiv.className = 'verification-step';
      stepDiv.innerHTML = `
        <div class="step-number">${number}</div>
        <div class="step-text">${text}</div>
      `;
      container.appendChild(stepDiv);
    }
    
    function startManualVerification(taskType) {
      const btn = document.getElementById(`${taskType}TaskBtn`);
      btn.innerHTML = '<div class="spinner"></div>';
      btn.disabled = true;
      
      // Simulate manual verification (in real app, this would be done by admin)
      setTimeout(() => {
        completeTask(taskType);
        btn.textContent = "Completed";
        btn.classList.remove('verify');
        btn.classList.add('completed');
        btn.disabled = false;
        closeVerificationModal();
        alert("Verification complete! 100 SYM tokens added to your balance.");
      }, 3000);
    }
    
    function closeVerificationModal() {
      document.getElementById('verificationModal').style.display = 'none';
      currentVerificationTask = null;
    }
    
    function completeTask(taskType) {
      if (completedTasks[taskType]) {
        alert("You've already completed this task!");
        return;
      }
      
      completedTasks[taskType] = true;
      
      const tokensToAdd = 100;
      tokenBalance += tokensToAdd;
      
      if (taskType !== 'invite') {
        earnedFromTasks += tokensToAdd;
      }
      
      updateTokenBalance();
      updateTaskButtons();
      saveUserData();
    }
    
    function updateTaskButtons() {
      const telegramTask = document.getElementById('telegramTask');
      const telegramBtn = document.getElementById('telegramTaskBtn');
      if (completedTasks.telegram) {
        telegramTask.classList.add('hidden');
      }
      
      const twitterTask = document.getElementById('twitterTask');
      const twitterBtn = document.getElementById('twitterTaskBtn');
      if (completedTasks.twitter) {
        twitterTask.classList.add('hidden');
      }
      
      const shareTask = document.getElementById('shareTask');
      const shareBtn = document.getElementById('shareTaskBtn');
      if (completedTasks.share) {
        shareTask.classList.add('hidden');
      }
      
      const inviteTask = document.getElementById('inviteTask');
      const inviteBtn = document.getElementById('inviteTaskBtn');
      if (completedTasks.invite) {
        inviteTask.classList.add('hidden');
      }
    }
    
    function updateTokenBalance() {
      document.getElementById('tokenBalance').textContent = `${tokenBalance} SYM`;
      document.getElementById('earnedFromTasks').textContent = `${earnedFromTasks} SYM`;
      document.getElementById('earnedFromReferrals').textContent = `${earnedFromReferrals} SYM`;
      document.getElementById('totalReferrals').textContent = totalReferrals;
      document.getElementById('earnedFromReferrals2').textContent = earnedFromReferrals;
      document.getElementById('totalReferrals2').textContent = totalReferrals;
    }
    
    function inviteFriend() {
      const tg = window.Telegram.WebApp;
      const referralLink = `https://t.me/whitesymbol_bot?start=${currentUser.id}`;
      
      const message = `Join WHITE SYMBOL and earn tokens with me! 🚀\n\n` +
                     `Use my referral link to get started:\n${referralLink}\n\n` +
                     `Let's build the community together! 💎`;
      
      if (tg.platform !== "unknown") {
          tg.openTelegramLink(`https://t.me/share/url?url=${encodeURIComponent(referralLink)}&text=${encodeURIComponent(message)}`);
      } else {
          window.open(`https://t.me/share/url?url=${encodeURIComponent(referralLink)}&text=${encodeURIComponent(message)}`, '_blank');
      }
      
      if (!completedTasks.invite) {
        completedTasks.invite = true;
        updateTaskButtons();
        saveUserData();
      }
    }

    function checkReferral() {
      const urlParams = new URLSearchParams(window.location.search);
      const refParam = urlParams.get('start');
      
      if (refParam && refParam !== currentUser.id) {
        setTimeout(() => {
          handleFriendParticipation(refParam);
        }, 3000);
      }
    }

    function handleFriendParticipation(referrerId) {
      // Check if this referral was already processed
      if (localStorage.getItem(`referral_processed_${referrerId}_${currentUser.id}`)) {
        return;
      }
      
      const referrerData = localStorage.getItem(`userData_${referrerId}`);
      
      if (referrerData) {
        try {
          const data = JSON.parse(referrerData);
          
          // Verify friend actually started earning
          if (hasFriendStartedEarning()) {
            data.totalReferrals = (data.totalReferrals || 0) + 1;
            data.earnedFromReferrals = (data.earnedFromReferrals || 0) + 100;
            data.tokenBalance = (data.tokenBalance || 0) + 100;
            
            localStorage.setItem(`userData_${referrerId}`, JSON.stringify(data));
            localStorage.setItem(`referral_processed_${referrerId}_${currentUser.id}`, 'true');
            
            if (referrerId === currentUser.id) {
              totalReferrals = data.totalReferrals;
              earnedFromReferrals = data.earnedFromReferrals;
              tokenBalance = data.tokenBalance;
              updateTokenBalance();
              
              updateFriendsList();
            }
          }
        } catch (e) {
          console.error("Error updating referrer data:", e);
        }
      }
    }

    function hasFriendStartedEarning() {
      // In a real implementation, you would check if the friend
      // has actually started earning coins in the game
      // For demo purposes, we'll simulate a 80% chance of real participation
      return Math.random() < 0.8;
    }

    function updateFriendsList() {
      const friendsList = document.getElementById('friendsList');
      if (friendsList.children.length === 1 && 
          friendsList.children[0].querySelector('.friend-name').textContent === "No friends joined yet") {
        friendsList.innerHTML = '';
      }
      
      const friendItem = document.createElement('div');
      friendItem.className = 'friend-item';
      friendItem.innerHTML = `
        <div class="friend-info">
          <div class="friend-name">New Friend</div>
          <div class="friend-date">Joined just now</div>
        </div>
        <div class="friend-tokens">+100 SYM</div>
      `;
      friendsList.prepend(friendItem);
    }

    function openAdminPanel() {
      const tableBody = document.getElementById('userTableBody');
      tableBody.innerHTML = '';
      
      const row = document.createElement('tr');
      row.innerHTML = `
        <td>${currentUser.username}</td>
        <td>${currentUser.tokens}</td>
        <td>${totalReferrals}</td>
        <td>${Object.values(completedTasks).filter(Boolean).length}</td>
        <td>${new Date().toLocaleDateString()}</td>
      `;
      tableBody.appendChild(row);
      
      document.getElementById('adminPanel').style.display = 'block';
    }
    
    function closeAdminPanel() {
      document.getElementById('adminPanel').style.display = 'none';
    }
  </script>
</body>
</html>
