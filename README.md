<!DOCTYPE html>  <html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>ChatBhig - Connect & Chat</title>  
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>💬</text></svg>">  
    <style>  
        * {  
            margin: 0;  
            padding: 0;  
            box-sizing: border-box;  
        }  :root {  
        --primary: #6366f1;  
        --primary-dark: #4f46e5;  
        --secondary: #ec4899;  
        --bg-dark: #0f172a;  
        --bg-card: #1e293b;  
        --text-primary: #f8fafc;  
        --text-secondary: #94a3b8;  
        --border: #334155;  
        --success: #10b981;  
        --warning: #f59e0b;  
        --chatbhig: #8b5cf6;  
    }  

    body {  
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;  
        background: var(--bg-dark);  
        color: var(--text-primary);  
        height: 100vh;  
        overflow: hidden;  
    }  

    /* Animated Background */  
    .bg-animation {  
        position: fixed;  
        top: 0;  
        left: 0;  
        width: 100%;  
        height: 100%;  
        z-index: -1;  
        background:   
            radial-gradient(circle at 20% 50%, rgba(139, 92, 246, 0.15) 0%, transparent 50%),  
            radial-gradient(circle at 80% 80%, rgba(236, 72, 153, 0.15) 0%, transparent 50%),  
            radial-gradient(circle at 40% 20%, rgba(99, 102, 241, 0.1) 0%, transparent 50%);  
        animation: bgPulse 15s ease-in-out infinite;  
    }  

    @keyframes bgPulse {  
        0%, 100% { opacity: 1; transform: scale(1); }  
        50% { opacity: 0.8; transform: scale(1.1); }  
    }  

    /* Login Screen */  
    .login-screen {  
        position: fixed;  
        top: 0;  
        left: 0;  
        width: 100%;  
        height: 100%;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        background: var(--bg-dark);  
        z-index: 1000;  
        transition: opacity 0.5s ease, visibility 0.5s ease;  
    }  

    .login-screen.hidden {  
        opacity: 0;  
        visibility: hidden;  
    }  

    .login-container {  
        background: var(--bg-card);  
        padding: 3rem;  
        border-radius: 24px;  
        border: 1px solid var(--border);  
        width: 90%;  
        max-width: 420px;  
        box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);  
        transform: translateY(0);  
        animation: slideUp 0.6s ease;  
    }  

    @keyframes slideUp {  
        from { opacity: 0; transform: translateY(30px); }  
        to { opacity: 1; transform: translateY(0); }  
    }  

    .logo {  
        text-align: center;  
        margin-bottom: 2rem;  
    }  

    .logo-icon {  
        width: 80px;  
        height: 80px;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        border-radius: 24px;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        margin: 0 auto 1rem;  
        font-size: 2.5rem;  
        box-shadow: 0 10px 30px rgba(139, 92, 246, 0.3);  
        animation: float 3s ease-in-out infinite;  
    }  

    @keyframes float {  
        0%, 100% { transform: translateY(0); }  
        50% { transform: translateY(-10px); }  
    }  

    .logo h1 {  
        font-size: 2.5rem;  
        background: linear-gradient(to right, var(--chatbhig), var(--secondary));  
        -webkit-background-clip: text;  
        -webkit-text-fill-color: transparent;  
        margin-bottom: 0.5rem;  
        font-weight: 800;  
        letter-spacing: -1px;  
    }  

    .logo .domain {  
        font-size: 0.9rem;  
        color: var(--chatbhig);  
        font-weight: 600;  
        letter-spacing: 2px;  
        text-transform: uppercase;  
        margin-top: 0.25rem;  
    }  

    .logo p {  
        color: var(--text-secondary);  
        font-size: 0.95rem;  
        margin-top: 0.5rem;  
    }  

    .input-group {  
        margin-bottom: 1.5rem;  
    }  

    .input-group label {  
        display: block;  
        margin-bottom: 0.5rem;  
        color: var(--text-secondary);  
        font-size: 0.875rem;  
        font-weight: 500;  
    }  

    .input-group input {  
        width: 100%;  
        padding: 1rem;  
        background: var(--bg-dark);  
        border: 2px solid var(--border);  
        border-radius: 12px;  
        color: var(--text-primary);  
        font-size: 1rem;  
        transition: all 0.3s ease;  
    }  

    .input-group input:focus {  
        outline: none;  
        border-color: var(--chatbhig);  
        box-shadow: 0 0 0 3px rgba(139, 92, 246, 0.1);  
    }  

    .btn {  
        width: 100%;  
        padding: 1rem;  
        background: linear-gradient(135deg, var(--chatbhig), var(--primary-dark));  
        border: none;  
        border-radius: 12px;  
        color: white;  
        font-size: 1rem;  
        font-weight: 600;  
        cursor: pointer;  
        transition: all 0.3s ease;  
        position: relative;  
        overflow: hidden;  
    }  

    .btn:hover {  
        transform: translateY(-2px);  
        box-shadow: 0 10px 30px rgba(139, 92, 246, 0.4);  
    }  

    .btn:active {  
        transform: translateY(0);  
    }  

    .btn::after {  
        content: '';  
        position: absolute;  
        top: 50%;  
        left: 50%;  
        width: 0;  
        height: 0;  
        border-radius: 50%;  
        background: rgba(255, 255, 255, 0.3);  
        transform: translate(-50%, -50%);  
        transition: width 0.6s, height 0.6s;  
    }  

    .btn:active::after {  
        width: 300px;  
        height: 300px;  
    }  

    .footer-links {  
        text-align: center;  
        margin-top: 1.5rem;  
        color: var(--text-secondary);  
        font-size: 0.875rem;  
    }  

    .footer-links a {  
        color: var(--chatbhig);  
        text-decoration: none;  
        margin: 0 0.5rem;  
    }  

    /* Main App Layout */  
    .app-container {  
        display: none;  
        height: 100vh;  
        grid-template-columns: 300px 1fr 350px;  
        animation: fadeIn 0.5s ease;  
    }  

    .app-container.active {  
        display: grid;  
    }  

    @keyframes fadeIn {  
        from { opacity: 0; }  
        to { opacity: 1; }  
    }  

    /* Sidebar */  
    .sidebar {  
        background: var(--bg-card);  
        border-right: 1px solid var(--border);  
        display: flex;  
        flex-direction: column;  
        padding: 1.5rem;  
    }  

    .brand-header {  
        display: flex;  
        align-items: center;  
        gap: 0.75rem;  
        margin-bottom: 2rem;  
        padding-bottom: 1.5rem;  
        border-bottom: 1px solid var(--border);  
    }  

    .brand-icon {  
        width: 40px;  
        height: 40px;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        border-radius: 12px;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        font-size: 1.5rem;  
    }  

    .brand-text h2 {  
        font-size: 1.25rem;  
        background: linear-gradient(to right, var(--chatbhig), var(--secondary));  
        -webkit-background-clip: text;  
        -webkit-text-fill-color: transparent;  
    }  

    .brand-text span {  
        font-size: 0.75rem;  
        color: var(--text-secondary);  
    }  

    .user-profile {  
        display: flex;  
        align-items: center;  
        gap: 1rem;  
        padding: 1rem;  
        background: var(--bg-dark);  
        border-radius: 16px;  
        margin-bottom: 2rem;  
        border: 1px solid var(--border);  
        transition: all 0.3s ease;  
        cursor: pointer;  
    }  

    .user-profile:hover {  
        border-color: var(--chatbhig);  
        transform: translateX(5px);  
    }  

    .avatar {  
        width: 50px;  
        height: 50px;  
        border-radius: 50%;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        font-size: 1.5rem;  
        font-weight: bold;  
        position: relative;  
    }  

    .avatar::after {  
        content: '';  
        position: absolute;  
        bottom: 2px;  
        right: 2px;  
        width: 12px;  
        height: 12px;  
        background: var(--success);  
        border-radius: 50%;  
        border: 2px solid var(--bg-dark);  
    }  

    .user-info h3 {  
        font-size: 1rem;  
        margin-bottom: 0.25rem;  
    }  

    .user-info p {  
        font-size: 0.875rem;  
        color: var(--text-secondary);  
    }  

    .nav-menu {  
        display: flex;  
        flex-direction: column;  
        gap: 0.5rem;  
        flex: 1;  
    }  

    .nav-item {  
        display: flex;  
        align-items: center;  
        gap: 1rem;  
        padding: 1rem;  
        border-radius: 12px;  
        cursor: pointer;  
        transition: all 0.3s ease;  
        color: var(--text-secondary);  
        position: relative;  
        overflow: hidden;  
    }  

    .nav-item::before {  
        content: '';  
        position: absolute;  
        left: 0;  
        top: 0;  
        height: 100%;  
        width: 3px;  
        background: var(--chatbhig);  
        transform: scaleY(0);  
        transition: transform 0.3s ease;  
    }  

    .nav-item:hover, .nav-item.active {  
        background: var(--bg-dark);  
        color: var(--text-primary);  
    }  

    .nav-item.active::before {  
        transform: scaleY(1);  
    }  

    .nav-item i {  
        font-size: 1.25rem;  
        width: 24px;  
        text-align: center;  
    }  

    .badge {  
        margin-left: auto;  
        background: var(--secondary);  
        color: white;  
        padding: 0.25rem 0.5rem;  
        border-radius: 20px;  
        font-size: 0.75rem;  
        font-weight: 600;  
        animation: pulse 2s infinite;  
    }  

    @keyframes pulse {  
        0%, 100% { opacity: 1; }  
        50% { opacity: 0.7; }  
    }  

    /* Main Content */  
    .main-content {  
        display: flex;  
        flex-direction: column;  
        background: var(--bg-dark);  
        position: relative;  
    }  

    .header {  
        padding: 1.5rem 2rem;  
        border-bottom: 1px solid var(--border);  
        display: flex;  
        justify-content: space-between;  
        align-items: center;  
        background: rgba(15, 23, 42, 0.8);  
        backdrop-filter: blur(10px);  
    }  

    .search-bar {  
        display: flex;  
        align-items: center;  
        background: var(--bg-card);  
        border-radius: 12px;  
        padding: 0.75rem 1rem;  
        width: 300px;  
        border: 1px solid var(--border);  
        transition: all 0.3s ease;  
    }  

    .search-bar:focus-within {  
        border-color: var(--chatbhig);  
        box-shadow: 0 0 0 3px rgba(139, 92, 246, 0.1);  
    }  

    .search-bar input {  
        background: none;  
        border: none;  
        color: var(--text-primary);  
        margin-left: 0.5rem;  
        width: 100%;  
        outline: none;  
    }  

    .header-actions {  
        display: flex;  
        gap: 1rem;  
    }  

    .icon-btn {  
        width: 40px;  
        height: 40px;  
        border-radius: 10px;  
        background: var(--bg-card);  
        border: 1px solid var(--border);  
        color: var(--text-secondary);  
        cursor: pointer;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        transition: all 0.3s ease;  
        position: relative;  
    }  

    .icon-btn:hover {  
        background: var(--chatbhig);  
        color: white;  
        border-color: var(--chatbhig);  
        transform: scale(1.1);  
    }  

    .notification-dot {  
        position: absolute;  
        top: 8px;  
        right: 8px;  
        width: 8px;  
        height: 8px;  
        background: var(--secondary);  
        border-radius: 50%;  
        animation: blink 2s infinite;  
    }  

    @keyframes blink {  
        0%, 100% { opacity: 1; }  
        50% { opacity: 0.3; }  
    }  

    /* Feed */  
    .feed {  
        flex: 1;  
        overflow-y: auto;  
        padding: 2rem;  
        scroll-behavior: smooth;  
    }  

    .feed::-webkit-scrollbar {  
        width: 8px;  
    }  

    .feed::-webkit-scrollbar-track {  
        background: var(--bg-dark);  
    }  

    .feed::-webkit-scrollbar-thumb {  
        background: var(--border);  
        border-radius: 4px;  
    }  

    .create-post {  
        background: var(--bg-card);  
        border-radius: 20px;  
        padding: 1.5rem;  
        margin-bottom: 2rem;  
        border: 1px solid var(--border);  
        animation: slideUp 0.5s ease;  
    }  

    .post-input {  
        display: flex;  
        gap: 1rem;  
        margin-bottom: 1rem;  
    }  

    .post-input input {  
        flex: 1;  
        background: var(--bg-dark);  
        border: 1px solid var(--border);  
        border-radius: 12px;  
        padding: 1rem;  
        color: var(--text-primary);  
        font-size: 1rem;  
        outline: none;  
        transition: all 0.3s ease;  
    }  

    .post-input input:focus {  
        border-color: var(--chatbhig);  
    }  

    .post-actions {  
        display: flex;  
        justify-content: space-between;  
        align-items: center;  
    }  

    .post-options {  
        display: flex;  
        gap: 1rem;  
    }  

    .post-option {  
        display: flex;  
        align-items: center;  
        gap: 0.5rem;  
        color: var(--text-secondary);  
        cursor: pointer;  
        padding: 0.5rem;  
        border-radius: 8px;  
        transition: all 0.3s ease;  
    }  

    .post-option:hover {  
        background: var(--bg-dark);  
        color: var(--chatbhig);  
    }  

    .post-card {  
        background: var(--bg-card);  
        border-radius: 20px;  
        padding: 1.5rem;  
        margin-bottom: 1.5rem;  
        border: 1px solid var(--border);  
        animation: slideUp 0.5s ease;  
        transition: all 0.3s ease;  
    }  

    .post-card:hover {  
        border-color: var(--chatbhig);  
        transform: translateY(-2px);  
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);  
    }  

    .post-header {  
        display: flex;  
        justify-content: space-between;  
        align-items: center;  
        margin-bottom: 1rem;  
    }  

    .post-author {  
        display: flex;  
        align-items: center;  
        gap: 1rem;  
    }  

    .author-avatar {  
        width: 48px;  
        height: 48px;  
        border-radius: 50%;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        font-weight: bold;  
        font-size: 1.25rem;  
    }  

    .author-info h4 {  
        font-size: 1rem;  
        margin-bottom: 0.25rem;  
    }  

    .author-info span {  
        font-size: 0.875rem;  
        color: var(--text-secondary);  
    }  

    .post-content {  
        margin-bottom: 1rem;  
        line-height: 1.6;  
        color: var(--text-primary);  
    }  

    .post-image {  
        width: 100%;  
        height: 300px;  
        background: linear-gradient(135deg, #1e293b, #334155);  
        border-radius: 12px;  
        margin-bottom: 1rem;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        color: var(--text-secondary);  
        overflow: hidden;  
        position: relative;  
    }  

    .post-image::before {  
        content: '';  
        position: absolute;  
        top: 0;  
        left: 0;  
        right: 0;  
        bottom: 0;  
        background:   
            linear-gradient(45deg, transparent 48%, rgba(255,255,255,0.05) 50%, transparent 52%),  
            linear-gradient(-45deg, transparent 48%, rgba(255,255,255,0.05) 50%, transparent 52%);  
        background-size: 20px 20px;  
        animation: moveStripes 20s linear infinite;  
    }  

    @keyframes moveStripes {  
        0% { background-position: 0 0; }  
        100% { background-position: 20px 20px; }  
    }  

    .post-stats {  
        display: flex;  
        gap: 2rem;  
        padding-top: 1rem;  
        border-top: 1px solid var(--border);  
    }  

    .stat {  
        display: flex;  
        align-items: center;  
        gap: 0.5rem;  
        color: var(--text-secondary);  
        cursor: pointer;  
        transition: all 0.3s ease;  
        user-select: none;  
    }  

    .stat:hover {  
        color: var(--chatbhig);  
        transform: scale(1.1);  
    }  

    .stat.liked {  
        color: var(--secondary);  
    }  

    /* Right Sidebar - Chat */  
    .chat-sidebar {  
        background: var(--bg-card);  
        border-left: 1px solid var(--border);  
        display: flex;  
        flex-direction: column;  
    }  

    .chat-header {  
        padding: 1.5rem;  
        border-bottom: 1px solid var(--border);  
    }  

    .chat-header h3 {  
        display: flex;  
        align-items: center;  
        gap: 0.5rem;  
    }  

    .online-count {  
        color: var(--success);  
        font-size: 0.875rem;  
    }  

    .chat-list {  
        flex: 1;  
        overflow-y: auto;  
        padding: 1rem;  
    }  

    .chat-item {  
        display: flex;  
        align-items: center;  
        gap: 1rem;  
        padding: 1rem;  
        border-radius: 12px;  
        cursor: pointer;  
        transition: all 0.3s ease;  
        margin-bottom: 0.5rem;  
        position: relative;  
    }  

    .chat-item:hover, .chat-item.active {  
        background: var(--bg-dark);  
    }  

    .chat-avatar {  
        width: 48px;  
        height: 48px;  
        border-radius: 50%;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        font-weight: bold;  
        position: relative;  
    }  

    .chat-avatar.online::after {  
        content: '';  
        position: absolute;  
        bottom: 2px;  
        right: 2px;  
        width: 10px;  
        height: 10px;  
        background: var(--success);  
        border-radius: 50%;  
        border: 2px solid var(--bg-card);  
    }  

    .chat-preview {  
        flex: 1;  
        min-width: 0;  
    }  

    .chat-preview h4 {  
        font-size: 0.95rem;  
        margin-bottom: 0.25rem;  
        white-space: nowrap;  
        overflow: hidden;  
        text-overflow: ellipsis;  
    }  

    .chat-preview p {  
        font-size: 0.875rem;  
        color: var(--text-secondary);  
        white-space: nowrap;  
        overflow: hidden;  
        text-overflow: ellipsis;  
    }  

    .chat-meta {  
        text-align: right;  
    }  

    .chat-meta span {  
        font-size: 0.75rem;  
        color: var(--text-secondary);  
    }  

    .unread {  
        background: var(--secondary);  
        color: white;  
        padding: 0.125rem 0.375rem;  
        border-radius: 10px;  
        font-size: 0.75rem;  
        margin-top: 0.25rem;  
        display: inline-block;  
    }  

    /* Chat Window */  
    .chat-window {  
        position: fixed;  
        bottom: 0;  
        right: 350px;  
        width: 350px;  
        height: 450px;  
        background: var(--bg-card);  
        border-radius: 20px 20px 0 0;  
        border: 1px solid var(--border);  
        border-bottom: none;  
        display: none;  
        flex-direction: column;  
        box-shadow: 0 -10px 40px rgba(0, 0, 0, 0.4);  
        z-index: 100;  
        animation: slideUpChat 0.3s ease;  
    }  

    @keyframes slideUpChat {  
        from { transform: translateY(100%); }  
        to { transform: translateY(0); }  
    }  

    .chat-window.active {  
        display: flex;  
    }  

    .chat-window-header {  
        padding: 1rem;  
        border-bottom: 1px solid var(--border);  
        display: flex;  
        justify-content: space-between;  
        align-items: center;  
        background: rgba(30, 41, 59, 0.95);  
        border-radius: 20px 20px 0 0;  
    }  

    .chat-user {  
        display: flex;  
        align-items: center;  
        gap: 0.75rem;  
    }  

    .chat-user-info h4 {  
        font-size: 0.95rem;  
    }  

    .chat-user-info span {  
        font-size: 0.75rem;  
        color: var(--success);  
    }  

    .close-chat {  
        background: none;  
        border: none;  
        color: var(--text-secondary);  
        cursor: pointer;  
        font-size: 1.25rem;  
        padding: 0.25rem;  
        transition: color 0.3s ease;  
    }  

    .close-chat:hover {  
        color: var(--text-primary);  
    }  

    .chat-messages {  
        flex: 1;  
        overflow-y: auto;  
        padding: 1rem;  
        display: flex;  
        flex-direction: column;  
        gap: 1rem;  
    }  

    .message {  
        max-width: 80%;  
        padding: 0.75rem 1rem;  
        border-radius: 16px;  
        font-size: 0.95rem;  
        line-height: 1.4;  
        animation: messagePop 0.3s ease;  
    }  

    @keyframes messagePop {  
        from { opacity: 0; transform: scale(0.8); }  
        to { opacity: 1; transform: scale(1); }  
    }  

    .message.sent {  
        align-self: flex-end;  
        background: linear-gradient(135deg, var(--chatbhig), var(--primary-dark));  
        color: white;  
        border-bottom-right-radius: 4px;  
    }  

    .message.received {  
        align-self: flex-start;  
        background: var(--bg-dark);  
        border: 1px solid var(--border);  
        border-bottom-left-radius: 4px;  
    }  

    .chat-input-area {  
        padding: 1rem;  
        border-top: 1px solid var(--border);  
        display: flex;  
        gap: 0.75rem;  
    }  

    .chat-input {  
        flex: 1;  
        background: var(--bg-dark);  
        border: 1px solid var(--border);  
        border-radius: 24px;  
        padding: 0.75rem 1rem;  
        color: var(--text-primary);  
        outline: none;  
        transition: all 0.3s ease;  
    }  

    .chat-input:focus {  
        border-color: var(--chatbhig);  
    }  

    .send-btn {  
        width: 40px;  
        height: 40px;  
        border-radius: 50%;  
        background: var(--chatbhig);  
        border: none;  
        color: white;  
        cursor: pointer;  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        transition: all 0.3s ease;  
    }  

    .send-btn:hover {  
        background: var(--primary-dark);  
        transform: scale(1.1);  
    }  

    /* Stories */  
    .stories {  
        display: flex;  
        gap: 1rem;  
        margin-bottom: 2rem;  
        overflow-x: auto;  
        padding-bottom: 0.5rem;  
    }  

    .stories::-webkit-scrollbar {  
        height: 6px;  
    }  

    .stories::-webkit-scrollbar-thumb {  
        background: var(--border);  
        border-radius: 3px;  
    }  

    .story {  
        display: flex;  
        flex-direction: column;  
        align-items: center;  
        gap: 0.5rem;  
        cursor: pointer;  
        transition: transform 0.3s ease;  
        min-width: 70px;  
    }  

    .story:hover {  
        transform: translateY(-5px);  
    }  

    .story-ring {  
        width: 70px;  
        height: 70px;  
        border-radius: 50%;  
        padding: 3px;  
        background: linear-gradient(135deg, var(--chatbhig), var(--secondary));  
        position: relative;  
    }  

    .story-ring.viewed {  
        background: var(--border);  
    }  

    .story-img {  
        width: 100%;  
        height: 100%;  
        border-radius: 50%;  
        background: var(--bg-card);  
        border: 3px solid var(--bg-dark);  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        font-size: 1.5rem;  
        overflow: hidden;  
    }  

    .story.add .story-ring {  
        background: var(--border);  
    }  

    .story.add .story-img {  
        font-size: 2rem;  
        color: var(--chatbhig);  
    }  

    .story-name {  
        font-size: 0.75rem;  
        color: var(--text-secondary);  
        text-align: center;  
    }  

    /* Responsive */  
    @media (max-width: 1200px) {  
        .app-container {  
            grid-template-columns: 250px 1fr;  
        }  
        .chat-sidebar {  
            display: none;  
        }  
        .chat-window {  
            right: 20px;  
        }  
    }  

    @media (max-width: 768px) {  
        .app-container {  
            grid-template-columns: 1fr;  
        }  
        .sidebar {  
            position: fixed;  
            bottom: 0;  
            left: 0;  
            right: 0;  
            height: auto;  
            flex-direction: row;  
            padding: 0.5rem;  
            z-index: 100;  
            border-right: none;  
            border-top: 1px solid var(--border);  
        }  
        .brand-header, .user-profile, .nav-menu {  
            display: none;  
        }  
        .mobile-nav {  
            display: flex;  
            justify-content: space-around;  
            width: 100%;  
        }  
        .feed {  
            padding-bottom: 80px;  
        }  
        .chat-window {  
            width: 100%;  
            right: 0;  
            border-radius: 0;  
        }  
    }  

    /* Utility */  
    .hidden {  
        display: none !important;  
    }  

    /* Toast Notification */  
    .toast {  
        position: fixed;  
        top: 2rem;  
        right: 2rem;  
        background: var(--bg-card);  
        border: 1px solid var(--chatbhig);  
        padding: 1rem 1.5rem;  
        border-radius: 12px;  
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);  
        display: flex;  
        align-items: center;  
        gap: 0.75rem;  
        z-index: 2000;  
        animation: slideInRight 0.3s ease;  
        transform: translateX(0);  
    }  

    @keyframes slideInRight {  
        from { transform: translateX(100%); opacity: 0; }  
        to { transform: translateX(0); opacity: 1; }  
    }  

    .toast.hiding {  
        animation: slideOutRight 0.3s ease forwards;  
    }  

    @keyframes slideOutRight {  
        to { transform: translateX(100%); opacity: 0; }  
    }  

    .toast-icon {  
        width: 40px;  
        height: 40px;  
        border-radius: 50%;  
        background: var(--chatbhig);  
        display: flex;  
        align-items: center;  
        justify-content: center;  
        color: white;  
    }  

    /* Typing Indicator */  
    .typing {  
        display: flex;  
        gap: 0.25rem;  
        padding: 0.5rem 1rem;  
    }  

    .typing span {  
        width: 8px;  
        height: 8px;  
        background: var(--text-secondary);  
        border-radius: 50%;  
        animation: typing 1.4s infinite;  
    }  

    .typing span:nth-child(2) { animation-delay: 0.2s; }  
    .typing span:nth-child(3) { animation-delay: 0.4s; }  

    @keyframes typing {  
        0%, 60%, 100% { transform: translateY(0); }  
        30% { transform: translateY(-10px); }  
    }  

    /* Domain watermark */  
    .domain-watermark {  
        position: fixed;  
        bottom: 1rem;  
        left: 1rem;  
        color: var(--text-secondary);  
        font-size: 0.75rem;  
        opacity: 0.5;  
        pointer-events: none;  
        z-index: 50;  
    }  
</style>

</head>  
<body>  
    <div class="bg-animation"></div>  
    <div class="domain-watermark">ChatBhig.com</div>  <!-- Login Screen -->  
<div class="login-screen" id="loginScreen">  
    <div class="login-container">  
        <div class="logo">  
            <div class="logo-icon">💬</div>  
            <h1>ChatBhig</h1>  
            <div class="domain">ChatBhig.com</div>  
            <p>Connect. Chat. Share.<br>Your world, closer than ever.</p>  
        </div>  
        <form id="loginForm">  
            <div class="input-group">  
                <label>Display Name</label>  
                <input type="text" id="username" placeholder="Enter your name" required maxlength="20">  
            </div>  
            <div class="input-group">  
                <label>Status</label>  
                <input type="text" id="userStatus" placeholder="What's on your mind?" maxlength="30" value="Hey there! I'm on ChatBhig.com">  
            </div>  
            <button type="submit" class="btn">Join ChatBhig</button>  
        </form>  
        <div class="footer-links">  
            <a href="#">Terms</a> • <a href="#">Privacy</a> • <a href="#">Help</a>  
            <br><br>  
            <span>© 2026 ChatBhig.com</span>  
        </div>  
    </div>  
</div>  

<!-- Main App -->  
<div class="app-container" id="appContainer">  
    <!-- Left Sidebar -->  
    <aside class="sidebar">  
        <div class="brand-header">  
            <div class="brand-icon">💬</div>  
            <div class="brand-text">  
                <h2>ChatBhig</h2>  
                <span>ChatBhig.com</span>  
            </div>  
        </div>  

        <div class="user-profile" onclick="showProfile()">  
            <div class="avatar" id="userAvatar">?</div>  
            <div class="user-info">  
                <h3 id="displayName">User</h3>  
                <p id="displayStatus">Online</p>  
            </div>  
        </div>  

        <nav class="nav-menu">  
            <div class="nav-item active" onclick="showFeed()">  
                <i>🏠</i>  
                <span>Feed</span>  
            </div>  
            <div class="nav-item" onclick="showMessages()">  
                <i>💬</i>  
                <span>Messages</span>  
                <span class="badge" id="msgBadge">3</span>  
            </div>  
            <div class="nav-item" onclick="showNotifications()">  
                <i>🔔</i>  
                <span>Notifications</span>  
                <span class="badge">5</span>  
            </div>  
            <div class="nav-item" onclick="showExplore()">  
                <i>🔍</i>  
                <span>Explore</span>  
            </div>  
            <div class="nav-item" onclick="showSaved()">  
                <i>🔖</i>  
                <span>Saved</span>  
            </div>  
        </nav>  

        <div class="nav-item" onclick="logout()" style="margin-top: auto;">  
            <i>🚪</i>  
            <span>Logout</span>  
        </div>  
    </aside>  

    <!-- Main Content -->  
    <main class="main-content">  
        <header class="header">  
            <div class="search-bar">  
                <i>🔍</i>  
                <input type="text" placeholder="Search ChatBhig..." id="searchInput">  
            </div>  
            <div class="header-actions">  
                <button class="icon-btn" onclick="toggleTheme()">  
                    <span id="themeIcon">🌙</span>  
                </button>  
                <button class="icon-btn" onclick="showNotifications()">  
                    🔔  
                    <span class="notification-dot"></span>  
                </button>  
                <button class="icon-btn" onclick="showSettings()">  
                    ⚙️  
                </button>  
            </div>  
        </header>  

        <div class="feed" id="feed">  
            <!-- Stories -->  
            <div class="stories">  
                <div class="story add">  
                    <div class="story-ring">  
                        <div class="story-img">+</div>  
                    </div>  
                    <span class="story-name">Add Story</span>  
                </div>  
                <div class="story">  
                    <div class="story-ring">  
                        <div class="story-img">👩</div>  
                    </div>  
                    <span class="story-name">Sarah</span>  
                </div>  
                <div class="story">  
                    <div class="story-ring">  
                        <div class="story-img">👨</div>  
                    </div>  
                    <span class="story-name">Mike</span>  
                </div>  
                <div class="story">  
                    <div class="story-ring viewed">  
                        <div class="story-img">👩‍💼</div>  
                    </div>  
                    <span class="story-name">Emma</span>  
                </div>  
                <div class="story">  
                    <div class="story-ring">  
                        <div class="story-img">👨‍💻</div>  
                    </div>  
                    <span class="story-name">Alex</span>  
                </div>  
            </div>  

            <!-- Create Post -->  
            <div class="create-post">  
                <div class="post-input">  
                    <div class="avatar" id="postAvatar" style="width: 40px; height: 40px; font-size: 1rem;">?</div>  
                    <input type="text" id="postContent" placeholder="What's happening on ChatBhig?" maxlength="280">  
                </div>  
                <div class="post-actions">  
                    <div class="post-options">  
                        <div class="post-option" onclick="addImage()">  
                            <span>📷</span>  
                            <span>Photo</span>  
                        </div>  
                        <div class="post-option" onclick="addVideo()">  
                            <span>🎥</span>  
                            <span>Video</span>  
                        </div>  
                        <div class="post-option" onclick="addPoll()">  
                            <span>📊</span>  
                            <span>Poll</span>  
                        </div>  
                        <div class="post-option" onclick="addEmoji()">  
                            <span>😊</span>  
                            <span>Emoji</span>  
                        </div>  
                    </div>  
                    <button class="btn" style="width: auto; padding: 0.75rem 1.5rem;" onclick="createPost()">Post</button>  
                </div>  
            </div>  

            <!-- Posts Container -->  
            <div id="postsContainer"></div>  
        </div>  
    </main>  

    <!-- Right Sidebar - Chat -->  
    <aside class="chat-sidebar">  
        <div class="chat-header">  
            <h3>Messages <span class="online-count">● 12 online</span></h3>  
        </div>  
        <div class="chat-list" id="chatList"></div>  
    </aside>  
</div>  

<!-- Chat Window -->  
<div class="chat-window" id="chatWindow">  
    <div class="chat-window-header">  
        <div class="chat-user">  
            <div class="chat-avatar online" id="chatWindowAvatar">?</div>  
            <div class="chat-user-info">  
                <h4 id="chatWindowName">User</h4>  
                <span>typing...</span>  
            </div>  
        </div>  
        <button class="close-chat" onclick="closeChat()">✕</button>  
    </div>  
    <div class="chat-messages" id="chatMessages"></div>  
    <div class="chat-input-area">  
        <input type="text" class="chat-input" id="chatInput" placeholder="Type a message..." onkeypress="handleChatKeypress(event)">  
        <button class="send-btn" onclick="sendMessage()">➤</button>  
    </div>  
</div>  

<script>  
    // State Management  
    let currentUser = null;  
    let activeChat = null;  
    let posts = [];  
    let chats = {};  
    let chatHistory = {};  

    // Sample Data  
    const sampleUsers = [  
        { name: 'Sarah Chen', avatar: '👩', status: 'online', lastMsg: 'Thanks! Check out ChatBhig.com 🎉', time: '2m', unread: 2 },  
        { name: 'Mike Ross', avatar: '👨', status: 'online', lastMsg: 'Did you see the new update?', time: '15m', unread: 0 },  
        { name: 'Emma Wilson', avatar: '👩‍💼', status: 'offline', lastMsg: 'Let\'s catch up tomorrow!', time: '1h', unread: 1 },  
        { name: 'Alex Kumar', avatar: '👨‍💻', status: 'online', lastMsg: 'ChatBhig is amazing!', time: '3h', unread: 0 },  
        { name: 'Lisa Park', avatar: '👩‍🎨', status: 'online', lastMsg: 'Check out my new design!', time: '5h', unread: 3 }  
    ];  

    const samplePosts = [  
        {  
            author: 'Sarah Chen',  
            avatar: '👩',  
            time: '2 hours ago',  
            content: 'Just discovered ChatBhig.com and I\'m loving it! 🚀 The chat features are incredible. Who else is on here? #ChatBhig #NewPlatform',  
            likes: 234,  
            comments: 45,  
            shares: 12,  
            liked: false  
        },  
        {  
            author: 'Mike Ross',  
            avatar: '👨',  
            time: '4 hours ago',  
            content: 'Beautiful sunset from my weekend hike! Nature never fails to amaze me. 🌅 Shared exclusively on ChatBhig!',  
            hasImage: true,  
            likes: 892,  
            comments: 127,  
            shares: 56,  
            liked: true  
        },  
        {  
            author: 'Emma Wilson',  
            avatar: '👩‍💼',  
            time: '6 hours ago',  
            content: 'Key takeaways from today\'s product meeting: 1) Focus on user experience 2) Simplify the onboarding flow 3) Ship fast, iterate faster. Let\'s build something amazing together on ChatBhig! 💪',  
            likes: 156,  
            comments: 23,  
            shares: 8,  
            liked: false  
        }  
    ];  

    // Login Handler  
    document.getElementById('loginForm').addEventListener('submit', function(e) {  
        e.preventDefault();  
        const username = document.getElementById('username').value.trim();  
        const status = document.getElementById('userStatus').value.trim();  
          
        if (username) {  
            currentUser = {  
                name: username,  
                status: status,  
                avatar: username.charAt(0).toUpperCase()  
            };  
              
            initApp();  
        }  
    });  

    function initApp() {  
        // Update UI with user data  
        document.getElementById('displayName').textContent = currentUser.name;  
        document.getElementById('displayStatus').textContent = currentUser.status;  
        document.getElementById('userAvatar').textContent = currentUser.avatar;  
        document.getElementById('postAvatar').textContent = currentUser.avatar;  
          
        // Populate initial data  
        posts = [...samplePosts];  
        renderPosts();  
        renderChatList();  
          
        // Transition  
        document.getElementById('loginScreen').classList.add('hidden');  
        document.getElementById('appContainer').classList.add('active');  
          
        showToast('Welcome to ChatBhig.com!', '💬');  
          
        // Simulate incoming activity  
        setTimeout(() => simulateActivity(), 5000);  
    }  

    // Post Functions  
    function renderPosts() {  
        const container = document.getElementById('postsContainer');  
        container.innerHTML = posts.map((post, index) => `  
            <div class="post-card" style="animation-delay: ${index * 0.1}s">  
                <div class="post-header">  
                    <div class="post-author">  
                        <div class="author-avatar">${post.avatar}</div>  
                        <div class="author-info">  
                            <h4>${post.author}</h4>  
                            <span>${post.time} • ChatBhig</span>  
                        </div>  
                    </div>  
                    <span style="cursor: pointer; color: var(--text-secondary);">⋯</span>  
                </div>  
                <div class="post-content">${post.content}</div>  
                ${post.hasImage ? '<div class="post-image">📷 Photo</div>' : ''}  
                <div class="post-stats">  
                    <div class="stat ${post.liked ? 'liked' : ''}" onclick="toggleLike(${index})">  
                        <span>${post.liked ? '❤️' : '🤍'}</span>  
                        <span>${post.likes}</span>  
                    </div>  
                    <div class="stat" onclick="showComments(${index})">  
                        <span>💬</span>  
                        <span>${post.comments}</span>  
                    </div>  
                    <div class="stat" onclick="sharePost(${index})">  
                        <span>🔄</span>  
                        <span>${post.shares}</span>  
                    </div>  
                    <div class="stat">  
                        <span>📤</span>  
                    </div>  
                </div>  
            </div>  
        `).join('');  
    }  

    function createPost() {  
        const content = document.getElementById('postContent').value.trim();  
        if (!content) return;  
          
        const newPost = {  
            author: currentUser.name,  
            avatar: currentUser.avatar,  
            time: 'Just now • ChatBhig',  
            content: content,  
            likes: 0,  
            comments: 0,  
            shares: 0,  
            liked: false  
        };  
          
        posts.unshift(newPost);  
        renderPosts();  
        document.getElementById('postContent').value = '';  
        showToast('Posted to ChatBhig!', '🚀');  
    }  

    function toggleLike(index) {  
        posts[index].liked = !posts[index].liked;  
        posts[index].likes += posts[index].liked ? 1 : -1;  
        renderPosts();  
    }  

    function sharePost(index) {  
        posts[index].shares++;  
        renderPosts();  
        showToast('Shared to your ChatBhig timeline!', '✓');  
    }  

    // Chat Functions  
    function renderChatList() {  
        const container = document.getElementById('chatList');  
        container.innerHTML = sampleUsers.map((user, index) => `  
            <div class="chat-item" onclick="openChat('${user.name}', '${user.avatar}')">  
                <div class="chat-avatar ${user.status}">${user.avatar}</div>  
                <div class="chat-preview">  
                    <h4>${user.name}</h4>  
                    <p>${user.lastMsg}</p>  
                </div>  
                <div class="chat-meta">  
                    <span>${user.time}</span>  
                    ${user.unread > 0 ? `<span class="unread">${user.unread}</span>` : ''}  
                </div>  
            </div>  
        `).join('');  
    }  

    function openChat(name, avatar) {  
        activeChat = name;  
        document.getElementById('chatWindow').classList.add('active');  
        document.getElementById('chatWindowName').textContent = name;  
        document.getElementById('chatWindowAvatar').textContent = avatar;  
          
        // Load chat history or create new  
        if (!chatHistory[name]) {  
            chatHistory[name] = [  
                { type: 'received', text: 'Hey! Welcome to ChatBhig.com! How are you doing?' },  
                { type: 'sent', text: 'I\'m great, thanks! This platform is amazing.' }  
            ];  
        }  
          
        renderChatMessages();  
        document.getElementById('chatInput').focus();  
    }  

    function renderChatMessages() {  
        const container = document.getElementById('chatMessages');  
        if (!chatHistory[activeChat]) return;  
          
        container.innerHTML = chatHistory[activeChat].map(msg => `  
            <div class="message ${msg.type}">${msg.text}</div>  
        `).join('');  
          
        container.scrollTop = container.scrollHeight;  
    }  

    function closeChat() {  
        document.getElementById('chatWindow').classList.remove('active');  
        activeChat = null;  
    }  

    function sendMessage() {  
        const input = document.getElementById('chatInput');  
        const text = input.value.trim();  
        if (!text || !activeChat) return;  
          
        chatHistory[activeChat].push({ type: 'sent', text: text });  
        renderChatMessages();  
        input.value = '';  
          
        // Simulate reply  
        setTimeout(() => {  
            if (activeChat) {  
                const replies = [  
                    'That\'s awesome! Love ChatBhig.com! 🎉',  
                    'Haha, totally agree! 😄',  
                    'Wow, really? That\'s amazing!',  
                    'I was just thinking about that too!',  
                    'Thanks for sharing on ChatBhig! 🙌'  
                ];  
                const randomReply = replies[Math.floor(Math.random() * replies.length)];  
                chatHistory[activeChat].push({ type: 'received', text: randomReply });  
                renderChatMessages();  
                showToast(`New message from ${activeChat}`, '💬');  
            }  
        }, 2000 + Math.random() * 3000);  
    }  

    function handleChatKeypress(e) {  
        if (e.key === 'Enter') sendMessage();  
    }  

    // Navigation  
    function showFeed() {  
        document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));  
        event.currentTarget.classList.add('active');  
        showToast('ChatBhig feed refreshed', '🔄');  
    }  

    function showMessages() {  
        showToast('ChatBhig Messages', '💬');  
    }  

    function showNotifications() {  
        showToast('No new notifications', '🔔');  
    }  

    function showExplore() {  
        showToast('Explore ChatBhig', '🔍');  
    }  

    function showSaved() {  
        showToast('Saved posts', '🔖');  
    }  

    function showProfile() {  
        showToast(`Viewing ${currentUser.name}'s ChatBhig profile`, '👤');  
    }  

    function showSettings() {  
        showToast('ChatBhig Settings', '⚙️');  
    }  

    function toggleTheme() {  
        const icon = document.getElementById('themeIcon');  
        icon.textContent = icon.textContent === '🌙' ? '☀️' : '🌙';  
        showToast('Theme switched!', '🎨');  
    }  

    function logout() {  
        location.reload();  
    }  

    // Post Options  
    function addImage() {  
        showToast('Image upload ready', '📷');  
    }  

    function addVideo() {  
        showToast('Video upload ready', '🎥');  
    }  

    function addPoll() {  
        showToast('Poll creation ready', '📊');  
    }  

    function addEmoji() {  
        const emojis = ['😀', '😂', '🥰', '😎', '🤔', '👍', '🔥', '❤️', '🎉', '✨'];  
        const input = document.getElementById('postContent');  
        input.value += emojis[Math.floor(Math.random() * emojis.length)];  
    }  

    function showComments(index) {  
        showToast(`Viewing ${posts[index].comments} comments`, '💬');  
    }  

    // Toast Notification  
    function showToast(message, icon) {  
        const toast = document.createElement('div');  
        toast.className = 'toast';  
        toast.innerHTML = `  
            <div class="toast-icon">${icon}</div>  
            <div>  
                <div style="font-weight: 600; margin-bottom: 0.25rem;">${message}</div>  
                <div style="font-size: 0.875rem; color: var(--text-secondary);">ChatBhig.com</div>  
            </div>  
        `;  
        document.body.appendChild(toast);  
          
        setTimeout(() => {  
            toast.classList.add('hiding');  
            setTimeout(() => toast.remove(), 300);  
        }, 3000);  
    }  

    // Simulate Activity  
    function simulateActivity() {  
        if (Math.random() > 0.7) {  
            const randomUser = sampleUsers[Math.floor(Math.random() * sampleUsers.length)];  
            showToast(`${randomUser.name} liked your ChatBhig post`, '❤️');  
        }  
        setTimeout(() => simulateActivity(), 10000 + Math.random() * 20000);  
    }  

    // Search functionality  
    document.getElementById('searchInput').addEventListener('input', function(e) {  
        const term = e.target.value.toLowerCase();  
        if (term.length > 2) {  
            const filtered = posts.filter(p =>   
                p.content.toLowerCase().includes(term) ||   
                p.author.toLowerCase().includes(term)  
            );  
            if (filtered.length !== posts.length) {  
                const container = document.getElementById('postsContainer');  
                container.innerHTML = filtered.map((post, index) => `  
                    <div class="post-card">  
                        <div class="post-header">  
                            <div class="post-author">  
                                <div class="author-avatar">${post.avatar}</div>  
                                <div class="author-info">  
                                    <h4>${post.author}</h4>  
                                    <span>${post.time}</span>  
                                </div>  
                            </div>  
                        </div>  
                        <div class="post-content">${post.content}</div>  
                        <div class="post-stats">  
                            <div class="stat ${post.liked ? 'liked' : ''}">  
                                <span>${post.liked ? '❤️' : '🤍'}</span>  
                                <span>${post.likes}</span>  
                            </div>  
                            <div class="stat">  
                                <span>💬</span>  
                                <span>${post.comments}</span>  
                            </div>  
                        </div>  
                    </div>  
                `).join('');  
            }  
        } else if (term.length === 0) {  
            renderPosts();  
        }  
    });  
</script>

</body>  
</html>  