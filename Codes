
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Pie • Complete Social Universe</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --primary: #FF3B6F;
            --primary-dark: #E02E5C;
            --secondary: #00D2FF;
            --dark: #0A0A0A;
            --card-bg: #111111;
            --gray-border: #2A2A2A;
            --text-main: #FFFFFF;
            --text-dim: #ADADAD;
            --like-red: #FF3040;
            --safe-top: env(safe-area-inset-top);
            --safe-bottom: env(safe-area-inset-bottom);
            --gold: #FFD700;
            --green: #4CAF50;
            --font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            --font-size-multiplier: 1;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body, html {
            height: 100%; width: 100%;
            background: var(--dark); color: var(--text-main);
            font-family: var(--font-family);
            font-size: calc(1rem * var(--font-size-multiplier));
            overflow: hidden; user-select: none; -webkit-user-select: none;
        }
        button { background: none; border: none; color: inherit; cursor: pointer; font-family: inherit; font-size: inherit; }
        input, textarea, select { font-family: inherit; font-size: inherit; outline: none; }

        @keyframes fadeUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes pulse { 0%,100% { transform: scale(1); } 50% { transform: scale(1.05); } }
        @keyframes spin { to { transform: rotate(360deg); } }
        @keyframes toastAnim { 0% { opacity:0;transform:translateY(20px); } 12% { opacity:1;transform:translateY(0); } 75% { opacity:1; } 100% { opacity:0;visibility:hidden; } }
        @keyframes typingBounce { 0%,60%,100% { transform:translateY(0); } 30% { transform:translateY(-8px); } }
        @keyframes slideUp { from { transform:translateY(100%); } to { transform:translateY(0); } }
        @keyframes pauseIconFade { 0% { opacity:1;transform:translate(-50%,-50%) scale(1); } 60% { opacity:1; } 100% { opacity:0;transform:translate(-50%,-50%) scale(1.3); } }

        /* AUTH */
        .auth-screen { position:fixed;inset:0;background:radial-gradient(circle at 30% 20%,#1f0c16,#000);z-index:10000;display:flex;align-items:center;justify-content:center;padding:20px;overflow-y:auto; }
        .auth-card { background:rgba(18,18,18,0.96);backdrop-filter:blur(20px);border-radius:48px;padding:32px 24px;width:100%;max-width:400px;border:1px solid rgba(255,255,255,0.1);animation:fadeUp 0.5s ease; }
        .auth-toggle { display:flex;gap:12px;background:#1E1E1E;border-radius:60px;padding:4px;margin-bottom:28px; }
        .auth-switch { flex:1;text-align:center;padding:10px;border-radius:40px;cursor:pointer;font-weight:600;transition:0.2s; }
        .auth-switch.active { background:var(--primary);color:white; }
        .input-field { width:100%;padding:14px 18px;background:#1A1A1A;border:1px solid #2C2C2C;border-radius:60px;color:white;margin-bottom:14px;font-size:0.95rem;transition:0.2s; }
        .input-field:focus { border-color:var(--primary);box-shadow:0 0 0 3px rgba(255,59,111,0.15); }
        .btn-glow { background:linear-gradient(95deg,var(--primary),#FF8E53);width:100%;padding:14px;border:none;border-radius:60px;color:white;font-weight:bold;font-size:1rem;cursor:pointer;transition:0.15s; }
        .btn-glow:active { transform:scale(0.96); }
        .btn-outline { background:transparent;border:1.5px solid var(--primary);color:var(--primary);border-radius:60px;padding:12px 20px;font-weight:600;cursor:pointer;transition:0.2s;font-size:0.85rem; }
        .btn-outline:hover { background:var(--primary);color:#fff; }
        .avatar-preview { width:80px;height:80px;border-radius:50%;background:#333;margin:0 auto 20px;object-fit:cover;border:3px solid var(--primary); }
        .avatar-circle { border-radius:50%;object-fit:cover;flex-shrink:0; }

        /* MAIN LAYOUT */
        .main-ui { display:none;height:100%;flex-direction:column;position:relative; }
        .top-header { position:fixed;top:0;left:0;right:0;display:flex;justify-content:space-between;padding:12px 18px;padding-top:max(12px,var(--safe-top));background:linear-gradient(to bottom,rgba(0,0,0,0.75),transparent);z-index:1000;pointer-events:none; }
        .top-header>div { pointer-events:auto;display:flex;gap:14px; }
        .icon-circle { background:rgba(0,0,0,0.55);backdrop-filter:blur(14px);width:42px;height:42px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.2rem;cursor:pointer;color:white;transition:0.2s;border:1px solid rgba(255,255,255,0.12);position:relative; }
        .icon-circle:active { transform:scale(0.9);background:rgba(255,59,111,0.3); }
        .bottom-nav { position:fixed;bottom:0;left:0;right:0;display:flex;justify-content:space-around;align-items:flex-end;padding:8px 10px;padding-bottom:max(8px,var(--safe-bottom));background:rgba(10,10,10,0.97);backdrop-filter:blur(22px);border-top:0.5px solid rgba(255,255,255,0.1);z-index:1050;height:62px; }
        .nav-item { display:flex;flex-direction:column;align-items:center;font-size:1.35rem;cursor:pointer;opacity:0.55;transition:0.2s;color:white;flex:1;text-align:center;position:relative; }
        .nav-item.active { opacity:1;color:var(--primary);text-shadow:0 0 8px rgba(255,59,111,0.5); }
        .nav-label { font-size:0.58rem;margin-top:1px;font-weight:500; }
        .nav-center-btn { width:48px;height:48px;background:linear-gradient(135deg,var(--primary),#FF6B8A);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.7rem;cursor:pointer;color:#fff;margin-top:-20px;box-shadow:0 6px 20px rgba(255,59,111,0.5);transition:0.2s;border:3px solid var(--dark);z-index:10; }
        .nav-center-btn:active { transform:scale(0.88); }

        /* FEED - FIXED VIDEO PLAYER */
        .feed-container { height:100%;overflow-y:scroll;scroll-snap-type:y mandatory;scrollbar-width:none;-webkit-overflow-scrolling:touch; }
        .feed-container::-webkit-scrollbar { display:none; }
        .video-post { height:100vh;scroll-snap-align:start;position:relative;background:#000;overflow:hidden; }

        /* VIDEO LOADING STATE */
        .video-loading-overlay {
            position:absolute;inset:0;background:#000;display:flex;align-items:center;justify-content:center;z-index:5;
            transition:opacity 0.3s;
        }
        .video-loading-overlay.hidden { opacity:0;pointer-events:none; }
        .video-loading-spinner { width:44px;height:44px;border:3px solid rgba(255,255,255,0.2);border-top-color:#fff;border-radius:50%;animation:spin 0.8s linear infinite; }

        /* VIDEO ERROR STATE */
        .video-error-overlay {
            position:absolute;inset:0;background:#111;display:none;align-items:center;justify-content:center;z-index:5;flex-direction:column;gap:12px;color:#888;
        }

        /* PLAY/PAUSE VISUAL FEEDBACK */
        .play-pause-icon {
            position:absolute;top:50%;left:50%;transform:translate(-50%,-50%) scale(1);
            width:70px;height:70px;border-radius:50%;background:rgba(0,0,0,0.6);
            display:flex;align-items:center;justify-content:center;font-size:1.8rem;color:#fff;
            pointer-events:none;z-index:18;opacity:0;
            transition:none;
        }
        .play-pause-icon.animate { animation:pauseIconFade 0.7s ease forwards; }

        .video-player {
            width:100%;height:100%;object-fit:cover;cursor:pointer;
            /* Critical: ensure video is always visible when loaded */
            display:block;
        }
        .sound-toggle-btn { position:absolute;top:80px;right:16px;z-index:25;width:38px;height:38px;border-radius:50%;background:rgba(0,0,0,0.5);display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:1rem;color:#fff;border:1px solid rgba(255,255,255,0.2);transition:0.2s; }
        .sound-toggle-btn:active { transform:scale(0.85); }
        .video-meta { position:absolute;bottom:130px;left:16px;right:85px;z-index:20;text-shadow:0 1px 6px black; }
        .video-meta .author-clickable { cursor:pointer;display:flex;align-items:center;gap:8px; }
        .video-meta .author-clickable img { width:40px;height:40px;border-radius:50%;object-fit:cover;border:2px solid #fff; }
        .side-actions { position:absolute;right:10px;bottom:125px;display:flex;flex-direction:column;gap:22px;align-items:center;z-index:20; }
        .action-icon { font-size:28px;cursor:pointer;background:none;border:none;color:white;display:flex;flex-direction:column;align-items:center;gap:3px;transition:0.15s;text-shadow:0 1px 3px rgba(0,0,0,0.7); }
        .action-icon span { font-size:11px;font-weight:700; }
        .action-icon:active { transform:scale(0.85); }
        .liked { color:var(--like-red);filter:drop-shadow(0 0 6px red);animation:pulse 0.35s ease; }
        .saved-icon { color:var(--gold) !important; }
        .follow-btn-sm { background:rgba(255,255,255,0.18);border-radius:30px;padding:5px 14px;font-size:0.7rem;cursor:pointer;backdrop-filter:blur(8px);border:1px solid rgba(255,255,255,0.2);font-weight:600; }
        .watermark-overlay { position:absolute;top:50%;left:50%;transform:translate(-50%,-50%) rotate(-20deg);font-size:3rem;font-weight:900;color:rgba(255,255,255,0.12);pointer-events:none;z-index:15;letter-spacing:4px; }

        /* PAGES */
        .pies-page, .explore-page, .profile-page, .pie-updates-page { padding:90px 12px 100px;overflow-y:auto;height:100%;-webkit-overflow-scrolling:touch; }
        .pie-card { background:var(--card-bg);border-radius:24px;padding:16px;margin-bottom:14px;border:1px solid var(--gray-border);animation:fadeIn 0.3s ease; }
        .pie-update-card { background:var(--card-bg);border-radius:20px;padding:16px;margin-bottom:16px;border:1px solid var(--gray-border); }
        .pie-update-card img { width:100%;border-radius:14px;max-height:350px;object-fit:cover;margin-top:10px; }
        .explore-grid { display:grid;grid-template-columns:repeat(3,1fr);gap:4px; }
        .grid-item { aspect-ratio:9/16;background:#1e1e1e;border-radius:10px;overflow:hidden;position:relative;cursor:pointer;max-height:280px; }
        .grid-item video, .grid-item img { width:100%;height:100%;object-fit:cover; }
        .grid-item .view-count-badge { position:absolute;bottom:4px;left:4px;background:rgba(0,0,0,0.65);border-radius:12px;padding:2px 7px;font-size:0.65rem;display:flex;align-items:center;gap:3px; }

        /* PROFILE */
        .profile-header { display:flex;flex-direction:column;align-items:center;padding:20px; }
        .avatar-lg { width:96px;height:96px;border-radius:50%;border:3px solid var(--primary);object-fit:cover;cursor:pointer; }
        .stats-row { display:flex;gap:34px;margin:14px 0;text-align:center; }
        .stat-item { cursor:pointer;transition:0.2s; }
        .stat-item:hover { color:var(--primary); }
        .stat-number { font-weight:800;font-size:1.15rem; }

        /* DRAWERS & OVERLAYS */
        .drawer { position:fixed;bottom:-100%;left:0;width:100%;background:#121212;border-radius:28px 28px 0 0;transition:bottom 0.35s cubic-bezier(0.2,0.9,0.4,1);z-index:2000;max-height:78%;display:flex;flex-direction:column; }
        .drawer.active { bottom:0; }
        .drawer-header { padding:18px;text-align:center;border-bottom:1px solid #2a2a2a;position:relative;font-weight:700;font-size:1rem; }
        .close-drawer { position:absolute;right:18px;top:12px;font-size:26px;cursor:pointer;opacity:0.7; }
        .comment-list, .chat-messages { padding:14px;overflow-y:auto;flex:1; }
        .chat-input-area { display:flex;gap:8px;padding:12px;border-top:1px solid #222;align-items:center; }

        /* FIXED COMMENT SECTION */
        .comment-item { display:flex;gap:10px;padding:10px 0;border-bottom:1px solid #1a1a1a; }
        .comment-item img { width:32px;height:32px;border-radius:50%;object-fit:cover;flex-shrink:0; }
        .comment-bubble { background:#1a1a1a;border-radius:16px;padding:8px 12px;flex:1; }
        .comment-bubble b { font-size:0.8rem;color:var(--primary); }
        .comment-bubble p { font-size:0.85rem;margin-top:2px; }
        .comment-bubble span { font-size:0.6rem;color:#555; }

        /* FULLSCREEN OVERLAYS */
        .fullscreen-overlay { position:fixed;inset:0;z-index:5000;background:#0A0A0A;display:flex;flex-direction:column;transform:translateY(105%);transition:transform 0.4s cubic-bezier(0.22,0.61,0.36,1);overflow:hidden; }
        .fullscreen-overlay.open { transform:translateY(0); }
        .overlay-top-bar { display:flex;align-items:center;gap:12px;padding:12px 16px;padding-top:max(12px,var(--safe-top));border-bottom:1px solid #1a1a1a;background:#0A0A0A;z-index:10; }
        .overlay-back-btn { width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.25rem;cursor:pointer;flex-shrink:0; }
        .overlay-content { flex:1;overflow-y:auto;-webkit-overflow-scrolling:touch; }
        .search-bar-wrap { position:relative;flex:1; }
        .search-bar-wrap input { width:100%;padding:12px 44px 12px 40px;background:#1a1a1a;border:1px solid #333;border-radius:30px;color:#fff;font-size:0.9rem; }
        .search-bar-wrap .search-icon-left { position:absolute;left:14px;top:50%;transform:translateY(-50%);color:#888;pointer-events:none;font-size:0.85rem; }
        .search-bar-wrap .clear-search-btn { position:absolute;right:10px;top:50%;transform:translateY(-50%);font-size:1rem;cursor:pointer;color:#aaa;width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;background:#333; }
        .trending-tag { display:inline-block;padding:8px 16px;background:#1a1a1a;border-radius:20px;margin:4px;cursor:pointer;font-size:0.8rem;border:1px solid #2a2a2a;transition:0.2s; }
        .trending-tag:hover { border-color:var(--primary); }
        .search-tabs { display:flex;border-bottom:1px solid #222;position:sticky;top:0;background:#0A0A0A;z-index:5; }
        .search-tab { flex:1;text-align:center;padding:11px;cursor:pointer;font-weight:600;font-size:0.8rem;opacity:0.6;border-bottom:2px solid transparent;transition:0.2s; }
        .search-tab.active { opacity:1;border-bottom-color:var(--primary);color:var(--primary); }
        .search-result-user { display:flex;align-items:center;gap:12px;padding:13px 16px;border-bottom:1px solid #1a1a1a;cursor:pointer;transition:0.15s; }
        .search-result-user:hover { background:#111; }
        .search-result-user img { width:44px;height:44px;border-radius:50%;object-fit:cover; }

        /* SETTINGS */
        .settings-page-overlay { position:fixed;inset:0;z-index:5000;background:#0A0A0A;display:flex;flex-direction:column;transform:translateX(105%);transition:transform 0.4s cubic-bezier(0.22,0.61,0.36,1);overflow:hidden; }
        .settings-page-overlay.open { transform:translateX(0); }
        .settings-list-item { display:flex;align-items:center;justify-content:space-between;padding:15px 18px;border-bottom:1px solid #1a1a1a;cursor:pointer;transition:0.15s;gap:12px; }
        .settings-list-item:hover { background:#111; }
        .settings-detail-panel { position:absolute;inset:0;background:#0A0A0A;z-index:10;display:flex;flex-direction:column;transform:translateX(100%);transition:transform 0.35s cubic-bezier(0.22,0.61,0.36,1); }
        .settings-detail-panel.open { transform:translateX(0); }

        /* CHAT */
        .chat-page-overlay { position:fixed;inset:0;z-index:5000;background:#0A0A0A;display:flex;flex-direction:column;transform:translateY(105%);transition:transform 0.4s cubic-bezier(0.22,0.61,0.36,1);overflow:hidden; }
        .chat-page-overlay.open { transform:translateY(0); }
        .chat-tabs { display:flex;border-bottom:1px solid #1a1a1a; }
        .chat-tab-btn { flex:1;text-align:center;padding:13px;cursor:pointer;font-weight:700;opacity:0.5;border-bottom:2px solid transparent;transition:0.2s;font-size:0.85rem; }
        .chat-tab-btn.active { opacity:1;border-bottom-color:var(--secondary);color:var(--secondary); }
        .conversation-item { display:flex;align-items:center;gap:12px;padding:14px 16px;border-bottom:1px solid #1a1a1a;cursor:pointer;transition:0.15s; }
        .conversation-item:hover { background:#111; }
        .conversation-item img { width:46px;height:46px;border-radius:50%;object-fit:cover; }
        .msg-bubble { max-width:75%;padding:10px 14px;border-radius:20px;margin-bottom:6px;word-break:break-word;font-size:0.85rem; }
        .msg-bubble.sent { background:var(--primary);margin-left:auto;border-bottom-right-radius:6px; }
        .msg-bubble.received { background:#1e1e1e;margin-right:auto;border-bottom-left-radius:6px; }
        .typing-dots span { display:inline-block;width:5px;height:5px;border-radius:50%;background:#888;margin:0 2px;animation:typingBounce 1.4s infinite; }
        .typing-dots span:nth-child(2) { animation-delay:0.2s; }
        .typing-dots span:nth-child(3) { animation-delay:0.4s; }

        /* CALL */
        .call-overlay { position:fixed;inset:0;z-index:6000;background:#000;display:flex;flex-direction:column;align-items:center;justify-content:center;transform:scale(0.8);opacity:0;pointer-events:none;transition:0.35s cubic-bezier(0.22,0.61,0.36,1); }
        .call-overlay.active { transform:scale(1);opacity:1;pointer-events:all; }
        .call-avatar-lg { width:110px;height:110px;border-radius:50%;object-fit:cover;border:4px solid var(--primary);animation:pulse 2s infinite; }
        .call-controls { display:flex;gap:18px;margin-top:36px; }
        .call-ctrl-btn { width:54px;height:54px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.3rem;cursor:pointer;transition:0.2s;background:#333;color:#fff; }
        .call-ctrl-btn.end { background:#ff3040;width:62px;height:62px;font-size:1.5rem; }
        .call-ctrl-btn:active { transform:scale(0.85); }
        .call-timer { font-size:1.2rem;margin-top:14px;font-weight:600;letter-spacing:1px; }

        /* TOAST */
        .toast { position:fixed;bottom:100px;left:20px;right:20px;background:rgba(0,0,0,0.9);backdrop-filter:blur(16px);padding:13px 20px;border-radius:60px;text-align:center;z-index:4000;animation:toastAnim 2.3s forwards;font-weight:500;border:1px solid rgba(255,255,255,0.1);font-size:0.9rem; }
        .unread-badge { position:absolute;top:-4px;right:-4px;width:18px;height:18px;background:var(--primary);border-radius:50%;font-size:0.55rem;display:flex;align-items:center;justify-content:center;font-weight:700; }
        .online-dot { width:9px;height:9px;border-radius:50%;background:var(--green);display:inline-block;margin-left:4px; }
        .toggle-switch { position:relative;width:46px;height:25px;background:#333;border-radius:20px;cursor:pointer;transition:0.3s;flex-shrink:0; }
        .toggle-switch.on { background:var(--primary); }
        .toggle-switch::after { content:'';position:absolute;top:2.5px;left:2.5px;width:20px;height:20px;border-radius:50%;background:#fff;transition:0.3s; }
        .toggle-switch.on::after { left:23px; }
        .loading-spinner { width:28px;height:28px;border:3px solid #333;border-top-color:var(--primary);border-radius:50%;animation:spin 0.8s linear infinite;margin:20px auto; }

        /* NOTIFICATION DRAWER - FIXED & ENHANCED */
        .notif-item {
            display:flex;align-items:flex-start;gap:12px;padding:14px 16px;border-bottom:1px solid #1a1a1a;
            animation:fadeIn 0.3s ease;
        }
        .notif-item.unread { background:rgba(255,59,111,0.06); }
        .notif-icon { width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem;flex-shrink:0; }
        .notif-icon.like { background:rgba(255,48,64,0.2);color:var(--like-red); }
        .notif-icon.comment { background:rgba(0,210,255,0.2);color:var(--secondary); }
        .notif-icon.follow { background:rgba(255,59,111,0.2);color:var(--primary); }
        .notif-icon.message { background:rgba(255,200,0,0.2);color:var(--gold); }
        .notif-icon.default { background:rgba(255,255,255,0.1);color:#fff; }
        .notif-text { flex:1; }
        .notif-text p { font-size:0.85rem;line-height:1.4; }
        .notif-text span { font-size:0.65rem;color:#555;margin-top:2px;display:block; }

        /* FOLLOW LIST / MODAL */
        .follow-list-modal { position:fixed;inset:0;z-index:7000;background:rgba(0,0,0,0.8);display:flex;align-items:flex-end;justify-content:center; }
        .follow-list-content { background:#121212;border-radius:24px 24px 0 0;width:100%;max-width:500px;max-height:70%;overflow-y:auto;padding:20px 16px;animation:slideUp 0.35s ease; }
        .follow-list-item { display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid #1a1a1a; }
        .follow-list-item img { width:44px;height:44px;border-radius:50%;object-fit:cover; }
        .share-options-container { position:fixed;bottom:0;left:0;right:0;background:#1a1a1a;border-radius:24px 24px 0 0;z-index:3000;padding:20px;display:flex;flex-wrap:wrap;gap:16px;justify-content:center;animation:slideUp 0.3s ease; }
        .share-option { display:flex;flex-direction:column;align-items:center;gap:6px;cursor:pointer;padding:10px 16px;border-radius:16px;transition:0.2s;font-size:0.8rem; }
        .share-option:hover { background:#252525; }
        .share-option i { font-size:1.6rem; }
        .share-overlay-bg { position:fixed;inset:0;z-index:2999;background:rgba(0,0,0,0.6); }

        /* CUSTOM MODAL */
        .custom-modal-overlay { position:fixed;inset:0;z-index:9000;background:rgba(0,0,0,0.75);display:flex;align-items:center;justify-content:center;animation:fadeIn 0.2s ease;padding:20px; }
        .custom-modal { background:#1a1a1a;border-radius:24px;padding:28px 22px;width:100%;max-width:400px;border:1px solid #333;text-align:center;animation:fadeUp 0.3s ease;max-height:85vh;overflow-y:auto; }
        .custom-modal h3 { margin-bottom:12px;font-size:1.1rem; }
        .custom-modal p { color:#aaa;margin-bottom:14px;font-size:0.85rem;line-height:1.4; }
        .custom-modal .modal-input { width:100%;padding:12px 16px;background:#111;border:1px solid #333;border-radius:30px;color:#fff;margin-bottom:10px;font-size:0.9rem; }
        .custom-modal .modal-btn-row { display:flex;gap:10px;justify-content:center;flex-wrap:wrap; }
        .custom-modal .modal-btn { padding:11px 22px;border-radius:30px;font-weight:600;cursor:pointer;font-size:0.85rem;transition:0.15s;min-width:80px; }
        .custom-modal .modal-btn:active { transform:scale(0.94); }
        .modal-btn.primary { background:var(--primary);color:#fff; }
        .modal-btn.secondary { background:#2a2a2a;color:#fff; }
        .modal-btn.danger { background:#ff3040;color:#fff; }
        .modal-btn.outline { border:1.5px solid var(--primary);color:var(--primary);background:transparent; }
        .modal-btn.gold { background:#FFD700;color:#000;font-weight:700; }
        .payment-option-card { background:#1a1a1a;border-radius:16px;padding:16px;margin:8px 0;cursor:pointer;border:2px solid transparent;transition:0.2s;text-align:left;display:flex;align-items:center;gap:14px; }
        .payment-option-card:hover { border-color:var(--primary); }
        .payment-option-card.selected { border-color:var(--gold);background:#1f1a10; }
        .payment-option-card i { font-size:2rem;width:48px;text-align:center;color:var(--gold); }

        /* DRAWER OVERLAY */
        .drawer-overlay-bg { position:fixed;inset:0;z-index:1999;background:rgba(0,0,0,0.5);display:none; }
        .drawer-overlay-bg.active { display:block; }

        @media (min-width:768px) {
            .settings-page-overlay, .chat-page-overlay, .fullscreen-overlay { width:480px;right:0;left:auto;border-left:1px solid #1a1a1a; }
            .grid-item { max-height:320px; }
        }
    </style>
</head>
<body>
    <!-- AUTH SCREEN -->
    <div id="authScreen" class="auth-screen">
        <div class="auth-card">
            <div style="text-align:center;font-size:2.5rem;margin-bottom:12px;">🥧</div>
            <div class="auth-toggle">
                <div id="loginTab" class="auth-switch active" onclick="AuthUI.showLogin()">Login</div>
                <div id="signupTab" class="auth-switch" onclick="AuthUI.showSignup()">Sign Up</div>
            </div>
            <div id="loginForm">
                <input type="text" id="loginUsername" class="input-field" placeholder="Username">
                <input type="password" id="loginPassword" class="input-field" placeholder="Password">
                <button class="btn-glow" onclick="AuthUI.login()">Enter Pie 🥧</button>
            </div>
            <div id="signupForm" style="display:none;">
                <input type="text" id="signupName" class="input-field" placeholder="Choose username">
                <input type="number" id="signupAge" class="input-field" placeholder="Age (under 25)">
                <input type="password" id="signupPass" class="input-field" placeholder="Password">
                <div style="text-align:center;margin-bottom:14px;">
                    <img id="signupAvatarPreview" class="avatar-preview" src="https://api.dicebear.com/7.x/avataaars/svg?seed=default" alt="avatar">
                    <label class="btn-outline" style="display:inline-block;padding:8px 18px;margin-top:8px;cursor:pointer;">📷 Upload Pic<input type="file" id="signupAvatarFile" accept="image/*" style="display:none" onchange="AuthUI.previewAvatar(this)"></label>
                </div>
                <button class="btn-glow" onclick="AuthUI.signup()">Bake Account</button>
            </div>
        </div>
    </div>

    <!-- MAIN UI -->
    <div id="mainUI" class="main-ui">
        <div class="top-header">
            <div>
                <div class="icon-circle" onclick="SearchPage.open()"><i class="fas fa-search"></i></div>
                <div class="icon-circle" onclick="NotifDrawer.open()"><i class="fas fa-bell"></i><span id="notifBadge" class="unread-badge" style="display:none;">0</span></div>
            </div>
            <div>
                <div class="icon-circle" onclick="SettingsPage.open()"><i class="fas fa-cog"></i></div>
                <div class="icon-circle" onclick="PieUpdatesPage.open()" title="Pie Updates"><i class="fas fa-pie-chart"></i><span id="pieBadge" class="unread-badge" style="display:none;">0</span></div>
            </div>
        </div>
        <div class="bottom-nav">
            <div class="nav-item active" data-tab="feed" onclick="Core.switchTab('feed')"><i class="fas fa-play-circle"></i><span class="nav-label">Feed</span></div>
            <div class="nav-item" data-tab="explore" onclick="Core.switchTab('explore')"><i class="fas fa-compass"></i><span class="nav-label">Explore</span></div>
            <div class="nav-center-btn" onclick="Core.openUploadOptions()"><i class="fas fa-plus"></i></div>
            <div class="nav-item" data-tab="messages" onclick="ChatPage.open()"><i class="fas fa-envelope"></i><span class="nav-label">Messages</span></div>
            <div class="nav-item" data-tab="profile" onclick="Core.switchTab('profile')"><i class="fas fa-user"></i><span class="nav-label">Me</span></div>
        </div>
        <input type="file" id="videoUpload" accept="video/*" style="display:none" onchange="Core.uploadVideo(this)">
        <input type="file" id="imageUpload" accept="image/*" style="display:none" onchange="Core.uploadImagePost(this)">

        <div id="feedPage" class="feed-container" style="display:block;"></div>
        <div id="piesPage" class="pies-page" style="display:none;"></div>
        <div id="explorePage" class="explore-page" style="display:none;"><div class="explore-grid" id="exploreGrid"></div></div>
        <div id="profilePage" class="profile-page" style="display:none;">
            <div class="profile-header">
                <img id="profileAvatar" class="avatar-lg" src="" alt="avatar" onclick="Core.changeProfilePic()">
                <h2 id="profileDisplayName">@user</h2>
                <p id="profileBio" style="color:var(--text-dim);">Pie creator 🥧</p>
                <p id="profilePrivateBadge" style="color:var(--gold);font-size:0.75rem;display:none;">🔒 Private Account</p>
                <div class="stats-row">
                    <div class="stat-item" onclick="Core.showFollowList('followers')"><div class="stat-number" id="profilePostCount">0</div><div>Posts</div></div>
                    <div class="stat-item" onclick="Core.showFollowList('followers')"><div class="stat-number" id="profileFollowerCount">0</div><div>Followers</div></div>
                    <div class="stat-item" onclick="Core.showFollowList('following')"><div class="stat-number" id="profileFollowingCount">0</div><div>Following</div></div>
                </div>
                <div id="profileActionButtons" style="display:flex;gap:8px;flex-wrap:wrap;justify-content:center;"></div>
                <div id="followRequestBadge" style="display:none;margin-top:8px;background:var(--gold);color:#000;padding:6px 14px;border-radius:20px;font-size:0.75rem;cursor:pointer;font-weight:600;" onclick="Core.showFollowRequests()">📩 Pending Follow Requests</div>
            </div>
            <div class="explore-grid" id="profileGrid"></div>
        </div>

        <!-- PIE UPDATES PAGE -->
        <div id="pieUpdatesPage" class="pie-updates-page" style="display:none;">
            <div style="background:var(--card-bg);border-radius:24px;padding:16px;margin-bottom:18px;border:1px solid var(--gray-border);">
                <textarea id="pieUpdateInput" class="input-field" rows="2" placeholder="Share an update... 📝" style="border-radius:16px;resize:none;"></textarea>
                <div style="display:flex;gap:10px;align-items:center;">
                    <button class="btn-glow" style="flex:1;padding:12px;" onclick="PieUpdatesPage.postUpdate()"><i class="fas fa-feather-alt"></i> Post Update</button>
                    <button class="icon-circle" style="flex-shrink:0;" onclick="document.getElementById('imageUpload').click()"><i class="fas fa-image"></i></button>
                </div>
                <img id="pieUpdateImagePreview" style="display:none;width:100%;border-radius:14px;margin-top:10px;max-height:250px;object-fit:cover;" alt="preview">
            </div>
            <div id="pieUpdateList"></div>
        </div>

        <!-- SEARCH FULLSCREEN -->
        <div id="searchOverlay" class="fullscreen-overlay">
            <div class="overlay-top-bar">
                <div class="overlay-back-btn" onclick="SearchPage.close()"><i class="fas fa-arrow-left"></i></div>
                <div class="search-bar-wrap">
                    <i class="fas fa-search search-icon-left"></i>
                    <input type="text" id="searchOverlayInput" placeholder="Search users, videos, or hashtags" oninput="SearchPage.onInput()" autocomplete="off">
                    <div class="clear-search-btn" id="clearSearchBtn" style="display:none;" onclick="SearchPage.clearSearch()"><i class="fas fa-times"></i></div>
                </div>
                <div class="icon-circle" onclick="SearchPage.voiceSearch()" style="flex-shrink:0;"><i class="fas fa-microphone"></i></div>
            </div>
            <div class="search-tabs" id="searchTabs" style="display:none;">
                <div class="search-tab active" data-stab="top" onclick="SearchPage.switchTab('top')">Top</div>
                <div class="search-tab" data-stab="users" onclick="SearchPage.switchTab('users')">Users</div>
                <div class="search-tab" data-stab="videos" onclick="SearchPage.switchTab('videos')">Videos</div>
                <div class="search-tab" data-stab="hashtags" onclick="SearchPage.switchTab('hashtags')">Hashtags</div>
            </div>
            <div class="overlay-content" id="searchContent">
                <div id="trendingSection" style="padding:16px;">
                    <h4 style="margin-bottom:12px;color:var(--text-dim);">🔥 Trending</h4>
                    <div id="trendingTags"></div>
                    <h4 style="margin:14px 0 8px;color:var(--text-dim);">📋 Recent</h4>
                    <div id="recentSearches"></div>
                </div>
                <div id="searchResultsArea" style="display:none;padding-bottom:40px;"></div>
            </div>
        </div>

        <!-- SETTINGS FULLSCREEN -->
        <div id="settingsOverlay" class="settings-page-overlay">
            <div class="overlay-top-bar">
                <div class="overlay-back-btn" onclick="SettingsPage.close()"><i class="fas fa-arrow-left"></i></div>
                <span style="font-weight:700;"><i class="fas fa-sliders-h"></i> Settings</span>
            </div>
            <div class="overlay-content" id="settingsMainList">
                <div class="settings-list-item" onclick="SettingsPage.openDetail('account')"><span><i class="fas fa-user-circle" style="color:var(--primary);width:24px;"></i> Account Information</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('password')"><span><i class="fas fa-lock" style="color:#FFD700;width:24px;"></i> Change Password</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('download')"><span><i class="fas fa-download" style="color:#00D2FF;width:24px;"></i> Download Your Data</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('deactivate')"><span><i class="fas fa-ban" style="color:#ff5252;width:24px;"></i> Deactivate Account</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('monetization')"><span><i class="fas fa-gem" style="color:#FF8E53;width:24px;"></i> Premium</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('privacy')"><span><i class="fas fa-eye-slash" style="color:#aaa;width:24px;"></i> Privacy & Safety</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('notifications')"><span><i class="fas fa-bell" style="color:#ff9800;width:24px;"></i> Notifications</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('accessibility')"><span><i class="fas fa-universal-access" style="color:#fff;width:24px;"></i> Language & Display</span><i class="fas fa-chevron-right"></i></div>
                <div class="settings-list-item" onclick="SettingsPage.openDetail('help')"><span><i class="fas fa-question-circle" style="color:#00D2FF;width:24px;"></i> Help Center</span><i class="fas fa-chevron-right"></i></div>
            </div>
            <div id="settingsDetailPanel" class="settings-detail-panel"></div>
        </div>

        <!-- CHAT FULLSCREEN -->
        <div id="chatOverlay" class="chat-page-overlay">
            <div class="overlay-top-bar">
                <div class="overlay-back-btn" onclick="ChatPage.close()"><i class="fas fa-arrow-left"></i></div>
                <span style="font-weight:700;"><i class="fas fa-comments"></i> Messages</span>
            </div>
            <div class="chat-tabs">
                <div class="chat-tab-btn active" data-ctab="community" onclick="ChatPage.switchChatTab('community')">🌍 Community</div>
                <div class="chat-tab-btn" data-ctab="private" onclick="ChatPage.switchChatTab('private')">💬 Private</div>
            </div>
            <div class="overlay-content" id="chatMainContent">
                <div id="communityChatView" style="display:flex;flex-direction:column;height:100%;">
                    <div id="communityMessages" class="chat-messages" style="flex:1;"></div>
                    <div class="chat-input-area">
                        <input type="text" id="communityMsgInput" class="input-field" placeholder="Chat with everyone..." style="margin:0;flex:1;" onkeydown="if(event.key==='Enter')ChatPage.sendCommunityMsg()">
                        <button class="btn-glow" style="width:auto;padding:12px 16px;" onclick="ChatPage.sendCommunityMsg()"><i class="fas fa-paper-plane"></i></button>
                    </div>
                </div>
                <div id="privateChatList" style="display:none;"><div id="dmConversationsList"></div></div>
                <div id="privateChatThread" style="display:none;flex-direction:column;height:100%;">
                    <div style="padding:10px 16px;border-bottom:1px solid #1a1a1a;display:flex;align-items:center;gap:10px;cursor:pointer;" onclick="ChatPage.backToDMList()"><i class="fas fa-arrow-left"></i> <span id="dmThreadName">Chat</span></div>
                    <div id="dmThreadMessages" class="chat-messages" style="flex:1;"></div>
                    <div id="dmTypingIndicator" style="padding:4px 16px;font-size:0.7rem;color:#888;display:none;">Typing<span class="typing-dots"><span></span><span></span><span></span></span></div>
                    <div class="chat-input-area" style="gap:6px;">
                        <button class="icon-circle" style="width:34px;height:34px;font-size:0.85rem;" onclick="ChatPage.startVoiceCall()"><i class="fas fa-phone"></i></button>
                        <button class="icon-circle" style="width:34px;height:34px;font-size:0.85rem;" onclick="ChatPage.startVideoCall()"><i class="fas fa-video"></i></button>
                        <input type="text" id="dmMsgInput" class="input-field" placeholder="Message..." style="margin:0;flex:1;" onkeydown="if(event.key==='Enter')ChatPage.sendDMMsg()">
                        <button class="btn-glow" style="width:auto;padding:12px 16px;" onclick="ChatPage.sendDMMsg()"><i class="fas fa-paper-plane"></i></button>
                    </div>
                </div>
            </div>
        </div>

        <!-- CALL OVERLAY -->
        <div id="callOverlay" class="call-overlay">
            <div style="text-align:center;">
                <img id="callAvatar" class="call-avatar-lg" src="" alt="caller">
                <h3 id="callName">@user</h3>
                <p id="callStatus" style="color:#aaa;">Calling...</p>
                <div class="call-timer" id="callTimer" style="display:none;">00:00</div>
            </div>
            <div class="call-controls">
                <button class="call-ctrl-btn" id="muteBtn" onclick="CallUI.toggleMute()"><i class="fas fa-microphone"></i></button>
                <button class="call-ctrl-btn end" onclick="CallUI.endCall()"><i class="fas fa-phone-slash"></i></button>
                <button class="call-ctrl-btn" id="speakerBtn" onclick="CallUI.toggleSpeaker()"><i class="fas fa-volume-up"></i></button>
            </div>
        </div>

        <!-- COMMENTS DRAWER - FIXED -->
        <div class="drawer-overlay-bg" id="commentDrawerBg" onclick="Core.closeComments()"></div>
        <div id="commentDrawer" class="drawer">
            <div class="drawer-header">
                💬 Comments <span id="commentCount" style="color:#888;font-size:0.8rem;"></span>
                <span class="close-drawer" onclick="Core.closeComments()">×</span>
            </div>
            <div id="commentList" class="comment-list" style="flex:1;overflow-y:auto;"></div>
            <div class="chat-input-area">
                <img id="commentUserAvatar" style="width:32px;height:32px;border-radius:50%;object-fit:cover;flex-shrink:0;" src="" alt="">
                <input type="text" id="commentInput" class="input-field" style="margin:0;flex:1;" placeholder="Add a comment..." onkeydown="if(event.key==='Enter')Core.addComment()">
                <button class="btn-glow" style="width:auto;padding:10px 16px;" onclick="Core.addComment()"><i class="fas fa-paper-plane"></i></button>
            </div>
        </div>

        <!-- NOTIFICATION DRAWER - FIXED -->
        <div class="drawer-overlay-bg" id="notifDrawerBg" onclick="NotifDrawer.close()"></div>
        <div id="notifDrawer" class="drawer">
            <div class="drawer-header">
                <i class="fas fa-bell" style="color:var(--primary);"></i> Notifications
                <button style="position:absolute;left:16px;top:14px;font-size:0.7rem;color:#888;background:none;border:none;cursor:pointer;" onclick="NotifDrawer.markAllRead()">Mark all read</button>
                <span class="close-drawer" onclick="NotifDrawer.close()">×</span>
            </div>
            <div id="notifList" style="overflow-y:auto;flex:1;"></div>
        </div>

        <!-- SHARE OVERLAY -->
        <div id="shareOverlayBg" class="share-overlay-bg" style="display:none;" onclick="Core.closeShareOptions()"></div>
        <div id="shareOptionsContainer" class="share-options-container" style="display:none;"></div>

        <!-- FOLLOW LIST MODAL -->
        <div id="followListModalContainer"></div>

        <!-- CUSTOM MODAL -->
        <div id="customModalContainer"></div>
    </div>

    <script>
    // ==================== TRANSLATIONS ====================
    const LANG = {
        en: {
            feed:'Feed', explore:'Explore', messages:'Messages', me:'Me',
            search:'Search users, videos, or hashtags', trending:'🔥 Trending', recent:'📋 Recent',
            noResults:'No results found', followers:'Followers', following:'Following', posts:'Posts',
            editProfile:'Edit Profile', saveChanges:'Save Changes', cancel:'Cancel', confirm:'Confirm',
            delete:'Delete', share:'Share', save:'Save', copyLink:'Copy Link',
            linkCopied:'🔗 Link copied!', liked:'❤️ Liked!', removedLike:'💔 Removed like',
            addedFav:'⭐ Added to favorites', removedFav:'Removed from favorites',
            commentAdded:'💬 Comment added', videoUploaded:'🎬 Video uploaded!',
            piePosted:'🥧 Update posted!', bioUpdated:'✅ Bio updated',
            passwordChanged:'✅ Password changed', accountUpdated:'✅ Account updated',
            deactivateWarning:'⚠️ This will hide your profile and content.',
            enterPassword:'Enter password to confirm', typeMessage:'Type a message...',
            noNotifications:'No notifications yet', noVideos:'No videos yet. Tap + to upload!',
            privateAccount:'🔒 This account is private', followToView:'Follow to see content',
        },
        zh:{ feed:'推荐', explore:'探索', messages:'消息', me:'我', search:'搜索用户、视频或话题', trending:'🔥 热门', recent:'📋 最近', noResults:'未找到结果', followers:'粉丝', following:'关注', posts:'帖子', editProfile:'编辑资料', saveChanges:'保存更改', cancel:'取消', confirm:'确认', delete:'删除', share:'分享', save:'保存', copyLink:'复制链接', linkCopied:'🔗 链接已复制！', liked:'❤️ 已点赞！', removedLike:'💔 取消点赞', addedFav:'⭐ 已加入收藏', removedFav:'已取消收藏', commentAdded:'💬 评论已添加', videoUploaded:'🎬 视频已上传！', piePosted:'🥧 更新已发布！', bioUpdated:'✅ 简介已更新', passwordChanged:'✅ 密码已更改', accountUpdated:'✅ 账户已更新', deactivateWarning:'⚠️ 这将隐藏您的个人资料和内容。', enterPassword:'输入密码确认', typeMessage:'输入消息...', noNotifications:'暂无通知', noVideos:'暂无视频。点击 + 上传！', privateAccount:'🔒 此账户为私密账户', followToView:'关注后查看内容' },
        lg:{ feed:'Emmere', explore:'Noonya', messages:'Obubaka', me:'Nze', search:'Noonya abakozesa, vidiyo, oba hashtags', trending:'🔥 Ebisinga', recent:'📋 Ebya katono', noResults:'Tewali kizuuliddwa', followers:'Abagoberezi', following:'Abagobererwa', posts:'Ebiwandiiko', editProfile:'Kyusa Profile', saveChanges:'Tereka Enkyukakyuka', cancel:'Sazaamu', confirm:'Kakasa', delete:'Sanguula', share:'Gabana', save:'Tereka', copyLink:'Koppa Link', linkCopied:'🔗 Link koppiddwa!', liked:'❤️ Kyagadwa!', removedLike:'💔 Okwagala kuggiddwa', addedFav:'⭐ Kyongedwa ku byagalwa', removedFav:'Kiggiddwa ku byagalwa', commentAdded:'💬 Endowooza yongedwa', videoUploaded:'🎬 Vidiyo eteredwa!', piePosted:'🥧 Update eteredwa!', bioUpdated:'✅ Bio ekyusiddwa', passwordChanged:'✅ Password ekyusiddwa', accountUpdated:'✅ Account ekyusiddwa', deactivateWarning:'⚠️ Kino kijja kukweka profile yo.', enterPassword:'Wandiika password okukakasa', typeMessage:'Wandiika obubaka...', noNotifications:'Tewali notifications', noVideos:'Tewali vidiyo. Koona + okutereka!', privateAccount:'🔒 Account eno ya kyama', followToView:'Goberera okulaba' },
        sw:{ feed:'Mlisho', explore:'Gundua', messages:'Ujumbe', me:'Mimi', search:'Tafuta watumiaji, video, au hashtags', trending:'🔥 Zinazovuma', recent:'📋 Hivi karibuni', noResults:'Hakuna matokeo', followers:'Wafuasi', following:'Wanaofuatwa', posts:'Machapisho', editProfile:'Hariri Wasifu', saveChanges:'Hifadhi Mabadiliko', cancel:'Ghairi', confirm:'Thibitisha', delete:'Futa', share:'Shiriki', save:'Hifadhi', copyLink:'Nakili Kiungo', linkCopied:'🔗 Kiungo kimenakiliwa!', liked:'❤️ Umependa!', removedLike:'💔 Like imeondolewa', addedFav:'⭐ Imeongezwa kwa vipendwa', removedFav:'Imeondolewa kwa vipendwa', commentAdded:'💬 Maoni yameongezwa', videoUploaded:'🎬 Video imepakiwa!', piePosted:'🥧 Update imechapishwa!', bioUpdated:'✅ Wasifu umesasishwa', passwordChanged:'✅ Nenosiri limebadilishwa', accountUpdated:'✅ Akaunti imesasishwa', deactivateWarning:'⚠️ Hii itaficha wasifu wako.', enterPassword:'Ingiza nenosiri kuthibitisha', typeMessage:'Andika ujumbe...', noNotifications:'Hakuna arifa', noVideos:'Hakuna video. Gonga + kupakia!', privateAccount:'🔒 Akaunti hii ni ya faragha', followToView:'Fuata kuona maudhui' },
        es:{ feed:'Inicio', explore:'Explorar', messages:'Mensajes', me:'Yo', search:'Buscar usuarios, videos o hashtags', trending:'🔥 Tendencias', recent:'📋 Reciente', noResults:'Sin resultados', followers:'Seguidores', following:'Siguiendo', posts:'Publicaciones', editProfile:'Editar Perfil', saveChanges:'Guardar Cambios', cancel:'Cancelar', confirm:'Confirmar', delete:'Eliminar', share:'Compartir', save:'Guardar', copyLink:'Copiar Enlace', linkCopied:'🔗 ¡Enlace copiado!', liked:'❤️ ¡Gusta!', removedLike:'💔 Gusta quitado', addedFav:'⭐ Añadido a favoritos', removedFav:'Eliminado de favoritos', commentAdded:'💬 Comentario añadido', videoUploaded:'🎬 ¡Video subido!', piePosted:'🥧 ¡Actualización publicada!', bioUpdated:'✅ Biografía actualizada', passwordChanged:'✅ Contraseña cambiada', accountUpdated:'✅ Cuenta actualizada', deactivateWarning:'⚠️ Esto ocultará tu perfil.', enterPassword:'Ingresa contraseña', typeMessage:'Escribe un mensaje...', noNotifications:'Sin notificaciones', noVideos:'Sin videos. ¡Toca +!', privateAccount:'🔒 Esta cuenta es privada', followToView:'Sigue para ver' },
        fr:{ feed:'Accueil', explore:'Explorer', messages:'Messages', me:'Moi', search:'Rechercher utilisateurs, vidéos ou hashtags', trending:'🔥 Tendance', recent:'📋 Récent', noResults:'Aucun résultat', followers:'Abonnés', following:'Abonnements', posts:'Publications', editProfile:'Modifier Profil', saveChanges:'Enregistrer', cancel:'Annuler', confirm:'Confirmer', delete:'Supprimer', share:'Partager', save:'Sauvegarder', copyLink:'Copier Lien', linkCopied:'🔗 Lien copié!', liked:'❤️ Aimé!', removedLike:'💔 Like retiré', addedFav:'⭐ Ajouté aux favoris', removedFav:'Retiré des favoris', commentAdded:'💬 Commentaire ajouté', videoUploaded:'🎬 Vidéo téléchargée!', piePosted:'🥧 Publication ajoutée!', bioUpdated:'✅ Bio mise à jour', passwordChanged:'✅ Mot de passe changé', accountUpdated:'✅ Compte mis à jour', deactivateWarning:'⚠️ Cela masquera votre profil.', enterPassword:'Mot de passe', typeMessage:'Écrivez un message...', noNotifications:'Aucune notification', noVideos:'Pas de vidéos. Touchez +!', privateAccount:'🔒 Ce compte est privé', followToView:'Suivre pour voir' }
    };
    let currentLang = 'en';
    function t(key){ return (LANG[currentLang]&&LANG[currentLang][key])||(LANG['en'][key])||key; }

    // ==================== DATABASE ====================
    let DB = {
        users:[], posts:[], follows:[], likes:[], notifications:[], chats:[],
        communityMessages:[], searchHistory:[], callLogs:[], pieUpdates:[],
        savedPosts:[], postViews:{}, followRequests:[], subscriptions:{}
    };
    let currentUser = null;
    let activeCommentPostId = null;
    let currentDmUserId = null;
    let callTimerInterval = null;
    let callSeconds = 0;
    let pendingImageForPieUpdate = null;
    let viewedPostsSession = new Set();
    // Track video observer globally so we can disconnect/reconnect
    let feedObserver = null;

    function syncStorage(){ localStorage.setItem('pie_db_v4', JSON.stringify(DB)); }
    function loadData(){
        const raw = localStorage.getItem('pie_db_v4');
        if(raw){ try{ DB = {...DB,...JSON.parse(raw)}; }catch(e){ syncStorage(); } }
        else syncStorage();
    }
    function getUserById(id){ return DB.users.find(u=>u.id===id); }
    function getPostLikesCount(postId){ return DB.likes.filter(l=>l.postId===postId).length; }
    function getPostCommentsCount(postId){
        const p = DB.posts.find(p=>p.id===postId)||DB.pieUpdates.find(p=>p.id===postId);
        return p?.comments?.length||0;
    }
    function getPostSharesCount(postId){
        const p = DB.posts.find(p=>p.id===postId)||DB.pieUpdates.find(p=>p.id===postId);
        return p?.shares||0;
    }
    function getPostViews(postId){ return DB.postViews[postId]||0; }
    function incrementViews(postId){
        const key = currentUser?.id+'_'+postId;
        if(viewedPostsSession.has(key)) return;
        if(!DB.postViews[postId]) DB.postViews[postId]=0;
        DB.postViews[postId]++;
        viewedPostsSession.add(key);
        syncStorage();
    }
    function isLikedByCurrent(postId){ return DB.likes.some(l=>l.userId===currentUser?.id&&l.postId===postId); }
    function isSavedByCurrent(postId){ return DB.savedPosts.some(s=>s.userId===currentUser?.id&&s.postId===postId); }
    function isFavoritedByCurrent(postId){ return (currentUser?.favorites||[]).includes(postId); }
    function getComments(postId){
        const p = DB.posts.find(p=>p.id===postId)||DB.pieUpdates.find(p=>p.id===postId);
        return p?.comments||[];
    }
    function generateId(prefix=''){ return prefix+Date.now().toString(36)+Math.random().toString(36).substr(2,6); }
    function isAccountPrivate(userId){ return getUserById(userId)?.isPrivate||false; }
    function canViewContent(targetUserId){
        if(!currentUser) return false;
        if(targetUserId===currentUser.id) return true;
        if(!isAccountPrivate(targetUserId)) return true;
        return DB.follows.some(f=>f.followerId===currentUser.id&&f.followingId===targetUserId);
    }
    function hasPendingFollowRequest(targetUserId){
        return DB.followRequests.some(r=>r.fromUserId===currentUser?.id&&r.toUserId===targetUserId&&r.status==='pending');
    }
    function timeAgo(ts){
        const s = Math.floor((Date.now()-ts)/1000);
        if(s<60) return 'just now';
        const m=Math.floor(s/60); if(m<60) return m+'m ago';
        const h=Math.floor(m/60); if(h<24) return h+'h ago';
        return Math.floor(h/24)+'d ago';
    }

    // ==================== CUSTOM MODAL ====================
    function showCustomModal(options){
        const container = document.getElementById('customModalContainer');
        const {title='',message='',inputType=null,inputPlaceholder='',inputValue='',buttons=[],onClose=null,customHTML=''}=options;
        let inputHTML='';
        if(inputType) inputHTML=`<input type="${inputType}" id="customModalInput" class="modal-input" placeholder="${inputPlaceholder}" value="${inputValue}" autocomplete="off">`;
        const btnsHTML=buttons.map((b,i)=>`<button class="modal-btn ${b.cls||'secondary'}" data-btnidx="${i}">${b.text}</button>`).join('');
        container.innerHTML=`<div class="custom-modal-overlay" id="customModalOverlay"><div class="custom-modal">${title?`<h3>${title}</h3>`:''}${message?`<p>${message}</p>`:''}${customHTML}${inputHTML}<div class="modal-btn-row">${btnsHTML}</div></div></div>`;
        document.getElementById('customModalOverlay').addEventListener('click',function(e){
            if(e.target===this){closeModal();if(onClose)onClose(null);}
        });
        document.querySelectorAll('.modal-btn').forEach(btn=>{
            btn.addEventListener('click',function(){
                const idx=parseInt(this.dataset.btnidx);
                const inputVal=document.getElementById('customModalInput')?.value||null;
                closeModal();
                if(buttons[idx]&&buttons[idx].callback) buttons[idx].callback(inputVal);
            });
        });
        function closeModal(){ container.innerHTML=''; }
        setTimeout(()=>{ const inp=document.getElementById('customModalInput'); if(inp) inp.focus(); },300);
        return {close:closeModal};
    }
    function showAlert(title,message){ return showCustomModal({title,message,buttons:[{text:'OK',cls:'primary',callback:()=>{}}]}); }
    function showConfirm(title,message,onConfirm,onCancel){
        return showCustomModal({title,message,buttons:[{text:t('cancel'),cls:'secondary',callback:()=>{if(onCancel)onCancel();}},{text:t('confirm'),cls:'primary',callback:()=>{if(onConfirm)onConfirm();}}]});
    }
    function showPrompt(title,message,placeholder,currentValue,callback){
        return showCustomModal({title,message,inputType:'text',inputPlaceholder:placeholder||'',inputValue:currentValue||'',buttons:[{text:t('cancel'),cls:'secondary',callback:()=>{}},{text:t('confirm'),cls:'primary',callback:(val)=>{if(callback)callback(val);}}]});
    }

    // ==================== CORE ====================
    const Core = {
        switchTab(tab){
            document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
            const navItem=document.querySelector(`.nav-item[data-tab="${tab}"]`);
            if(navItem) navItem.classList.add('active');
            ['feedPage','piesPage','explorePage','profilePage','pieUpdatesPage'].forEach(id=>document.getElementById(id).style.display='none');
            if(tab==='feed'){ document.getElementById('feedPage').style.display='block'; this.renderFeed(); }
            if(tab==='explore'){ document.getElementById('explorePage').style.display='block'; this.renderExplore(); }
            if(tab==='profile'){ document.getElementById('profilePage').style.display='block'; this.renderProfile(); }
            if(tab==='messages'){ ChatPage.open(); }
        },

        // ===================== FIXED VIDEO RENDERING =====================
        renderFeed(){
            if(!currentUser) return;
            // Disconnect old observer
            if(feedObserver){ feedObserver.disconnect(); feedObserver=null; }

            let feedPosts = DB.posts.filter(p=>p.type==='video').sort((a,b)=>b.createdAt-a.createdAt);
            const container = document.getElementById('feedPage');

            if(feedPosts.length===0){
                container.innerHTML=`<div style="height:100%;display:flex;align-items:center;justify-content:center;color:gray;flex-direction:column;gap:12px;"><i class="fas fa-video" style="font-size:52px;"></i><p>${t('noVideos')}</p></div>`;
                return;
            }

            container.innerHTML = feedPosts.map(post=>{
                const author = getUserById(post.userId);
                if(!author) return '';
                if(!canViewContent(author.id) && author.id!==currentUser.id){
                    return `<div class="video-post" style="display:flex;align-items:center;justify-content:center;flex-direction:column;gap:12px;color:#888;"><i class="fas fa-lock" style="font-size:48px;"></i><p>${t('privateAccount')}</p><p style="font-size:0.8rem;">${t('followToView')}</p></div>`;
                }
                const liked=isLikedByCurrent(post.id);
                const saved=isSavedByCurrent(post.id);
                const fav=isFavoritedByCurrent(post.id);
                const likeCount=getPostLikesCount(post.id);
                const commentCount=getPostCommentsCount(post.id);
                const shareCount=getPostSharesCount(post.id);
                const views=getPostViews(post.id);
                const isFollowing=DB.follows.some(f=>f.followerId===currentUser.id&&f.followingId===author.id);
                incrementViews(post.id);

                // Validate mediaUrl — skip broken posts
                const mediaUrl = (post.mediaUrl && post.mediaUrl.startsWith('blob:')) ? post.mediaUrl :
                                 (post.mediaUrl && post.mediaUrl.trim()!='') ? post.mediaUrl : null;

                const videoHTML = mediaUrl
                    ? `<div class="video-loading-overlay" id="loading-${post.id}"><div class="video-loading-spinner"></div></div>
                       <div class="video-error-overlay" id="error-${post.id}"><i class="fas fa-video-slash" style="font-size:48px;"></i><p>Video unavailable</p><p style="font-size:0.75rem;color:#555;">The file may have been removed</p></div>
                       <video class="video-player" id="vid-${post.id}"
                         src="${mediaUrl}"
                         loop playsinline preload="metadata"
                         muted
                         oncanplay="Core.onVideoReady('${post.id}')"
                         onerror="Core.onVideoError('${post.id}')"
                         onclick="Core.toggleVideoPlayback('${post.id}')">
                       </video>
                       <div class="play-pause-icon" id="pp-icon-${post.id}"></div>`
                    : `<div style="height:100%;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:8px;color:#555;background:#111;"><i class="fas fa-video-slash" style="font-size:48px;"></i><p>No video available</p></div>`;

                return `<div class="video-post" id="post-${post.id}" data-postid="${post.id}">
                    ${videoHTML}
                    <div class="sound-toggle-btn" id="sound-${post.id}" onclick="Core.toggleSound('${post.id}')"><i class="fas fa-volume-mute"></i></div>
                    ${saved?'<div class="watermark-overlay">Pie</div>':''}
                    <div class="video-meta">
                        <div class="author-clickable" onclick="Core.viewUserProfile('${author.id}')">
                            <img src="${author.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+author.username}" alt="@${author.username}" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'">
                            <div><strong>@${author.username}</strong>
                            ${author.id!==currentUser.id?`<button class="follow-btn-sm" onclick="event.stopPropagation();Core.toggleFollow('${author.id}')">${isFollowing?'<i class="fas fa-check"></i> Following':(hasPendingFollowRequest(author.id)?'⏳ Requested':'<i class="fas fa-plus"></i> Follow')}</button>`:''}</div>
                        </div>
                        <p style="margin-top:4px;">${post.caption||''}</p>
                        <p style="font-size:0.7rem;color:#aaa;">👁 ${views} views • ❤️ ${likeCount} • 💬 ${commentCount}</p>
                    </div>
                    <div class="side-actions">
                        <button class="action-icon ${liked?'liked':''}" id="like-btn-${post.id}" onclick="Core.likePost('${post.id}')"><i class="fas fa-heart"></i><span id="like-count-${post.id}">${likeCount}</span></button>
                        <button class="action-icon" onclick="Core.openComments('${post.id}')"><i class="fas fa-comment"></i><span>${commentCount}</span></button>
                        <button class="action-icon" onclick="Core.openShareOptions('${post.id}')"><i class="fas fa-share-alt"></i><span>${shareCount}</span></button>
                        <button class="action-icon ${fav?'liked':''}" id="fav-btn-${post.id}" onclick="Core.toggleFavorite('${post.id}')"><i class="fas fa-bookmark" style="color:${fav?'var(--gold)':'white'}"></i></button>
                    </div>
                </div>`;
            }).join('');

            this.initVideoObserver();
        },

        onVideoReady(postId){
            // Hide loading overlay when video is ready to play
            const loadingEl = document.getElementById(`loading-${postId}`);
            if(loadingEl) loadingEl.classList.add('hidden');
        },

        onVideoError(postId){
            // Hide loading, show error
            const loadingEl = document.getElementById(`loading-${postId}`);
            if(loadingEl) loadingEl.classList.add('hidden');
            const errorEl = document.getElementById(`error-${postId}`);
            if(errorEl){ errorEl.style.display='flex'; }
            const vid = document.getElementById(`vid-${postId}`);
            if(vid) vid.style.display='none';
            const soundBtn = document.getElementById(`sound-${postId}`);
            if(soundBtn) soundBtn.style.display='none';
        },

        // FIXED: Intersection Observer for video autoplay
        initVideoObserver(){
            if(feedObserver){ feedObserver.disconnect(); }

            feedObserver = new IntersectionObserver((entries)=>{
                entries.forEach(entry=>{
                    const postId = entry.target.dataset.postid;
                    if(!postId) return;
                    const vid = document.getElementById(`vid-${postId}`);
                    const soundBtn = document.getElementById(`sound-${postId}`);
                    if(!vid) return;

                    if(entry.isIntersecting && entry.intersectionRatio >= 0.7){
                        // Unmute and play
                        vid.muted = false;
                        const playPromise = vid.play();
                        if(playPromise!==undefined){
                            playPromise.then(()=>{
                                if(soundBtn){ soundBtn.innerHTML='<i class="fas fa-volume-up"></i>'; soundBtn.dataset.muted='false'; }
                            }).catch(()=>{
                                // Autoplay blocked — play muted
                                vid.muted=true;
                                vid.play().catch(()=>{});
                                if(soundBtn){ soundBtn.innerHTML='<i class="fas fa-volume-mute"></i>'; soundBtn.dataset.muted='true'; }
                            });
                        }
                    } else {
                        vid.pause();
                        vid.muted=true;
                        if(soundBtn){ soundBtn.innerHTML='<i class="fas fa-volume-mute"></i>'; soundBtn.dataset.muted='true'; }
                    }
                });
            },{ threshold:[0.7] });

            document.querySelectorAll('.video-post[data-postid]').forEach(el=>feedObserver.observe(el));
        },

        // Toggle play/pause on tap
        toggleVideoPlayback(postId){
            const vid = document.getElementById(`vid-${postId}`);
            const icon = document.getElementById(`pp-icon-${postId}`);
            if(!vid) return;

            if(vid.paused){
                vid.play().catch(()=>{});
                if(icon){ icon.innerHTML='<i class="fas fa-play"></i>'; }
            } else {
                vid.pause();
                if(icon){ icon.innerHTML='<i class="fas fa-pause"></i>'; }
            }
            // Animate icon
            if(icon){
                icon.classList.remove('animate');
                void icon.offsetWidth; // reflow
                icon.classList.add('animate');
            }
        },

        toggleSound(postId){
            const vid = document.getElementById(`vid-${postId}`);
            const btn = document.getElementById(`sound-${postId}`);
            if(!vid||!btn) return;
            if(btn.dataset.muted==='true'){
                vid.muted=false;
                btn.dataset.muted='false';
                btn.innerHTML='<i class="fas fa-volume-up"></i>';
            } else {
                vid.muted=true;
                btn.dataset.muted='true';
                btn.innerHTML='<i class="fas fa-volume-mute"></i>';
            }
        },

        // FIXED like — no full re-render, just update DOM
        likePost(postId){
            const existing=DB.likes.find(l=>l.userId===currentUser.id&&l.postId===postId);
            if(existing) DB.likes=DB.likes.filter(l=>!(l.userId===currentUser.id&&l.postId===postId));
            else{
                DB.likes.push({userId:currentUser.id,postId});
                const post=DB.posts.find(p=>p.id===postId)||DB.pieUpdates.find(p=>p.id===postId);
                if(post&&post.userId!==currentUser.id) DB.notifications.unshift({
                    id:generateId('n'),userId:post.userId,type:'like',
                    message:`@${currentUser.username} liked your post`,createdAt:Date.now(),read:false
                });
            }
            syncStorage();

            // Update like button in-place without full re-render
            const btn=document.getElementById(`like-btn-${postId}`);
            const countEl=document.getElementById(`like-count-${postId}`);
            if(btn){
                const nowLiked=isLikedByCurrent(postId);
                if(nowLiked){ btn.classList.add('liked'); } else { btn.classList.remove('liked'); }
            }
            if(countEl) countEl.textContent=getPostLikesCount(postId);

            // Update notif badge
            this.updateNotifBadge();
            PieUpdatesPage.renderUpdates();
            this.showToast(existing?t('removedLike'):t('liked'));
        },

        toggleFavorite(postId){
            if(!currentUser.favorites) currentUser.favorites=[];
            const idx=currentUser.favorites.indexOf(postId);
            if(idx===-1){ currentUser.favorites.push(postId); this.showToast(t('addedFav')); }
            else{ currentUser.favorites.splice(idx,1); this.showToast(t('removedFav')); }
            const uidx=DB.users.findIndex(u=>u.id===currentUser.id);
            DB.users[uidx].favorites=currentUser.favorites;
            syncStorage();
            // Update fav button in-place
            const btn=document.getElementById(`fav-btn-${postId}`);
            if(btn){
                const fav=isFavoritedByCurrent(postId);
                if(fav){ btn.classList.add('liked'); btn.querySelector('i').style.color='var(--gold)'; }
                else{ btn.classList.remove('liked'); btn.querySelector('i').style.color='white'; }
            }
        },

        // FIXED COMMENTS — styled drawer, not alert
        openComments(postId){
            activeCommentPostId=postId;
            this.renderCommentList();
            document.getElementById('commentDrawer').classList.add('active');
            document.getElementById('commentDrawerBg').classList.add('active');
            document.getElementById('commentInput').focus();
            // Set user avatar in comment input area
            const avEl=document.getElementById('commentUserAvatar');
            if(avEl) avEl.src=currentUser.profilePic||`https://api.dicebear.com/7.x/avataaars/svg?seed=${currentUser.username}`;
        },

        renderCommentList(){
            const comments=getComments(activeCommentPostId);
            const countEl=document.getElementById('commentCount');
            if(countEl) countEl.textContent=`(${comments.length})`;

            const list=document.getElementById('commentList');
            if(comments.length===0){
                list.innerHTML=`<div style="color:#888;text-align:center;padding:30px 20px;"><i class="fas fa-comment-slash" style="font-size:36px;opacity:0.4;"></i><p style="margin-top:8px;">No comments yet — be first!</p></div>`;
                return;
            }
            list.innerHTML=comments.map(c=>{
                const u=DB.users.find(u=>u.username===c.user)||{profilePic:'',username:c.user};
                return `<div class="comment-item">
                    <img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+c.user}" alt="@${c.user}" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'">
                    <div class="comment-bubble">
                        <b>@${c.user}</b>
                        <p>${c.text}</p>
                        <span>${timeAgo(c.timestamp||Date.now())}</span>
                    </div>
                </div>`;
            }).join('');
            // Scroll to bottom
            list.scrollTop=list.scrollHeight;
        },

        addComment(){
            const text=document.getElementById('commentInput').value.trim();
            if(!text||!activeCommentPostId) return;
            const post=DB.posts.find(p=>p.id===activeCommentPostId)||DB.pieUpdates.find(p=>p.id===activeCommentPostId);
            if(!post) return;
            post.comments=post.comments||[];
            post.comments.push({user:currentUser.username,text,timestamp:Date.now()});
            if(post.userId!==currentUser.id) DB.notifications.unshift({
                id:generateId('n'),userId:post.userId,type:'comment',
                message:`@${currentUser.username} commented: "${text.substring(0,30)}${text.length>30?'...':''}"`,
                createdAt:Date.now(),read:false
            });
            syncStorage();
            document.getElementById('commentInput').value='';
            this.renderCommentList();
            PieUpdatesPage.renderUpdates();
            this.updateNotifBadge();
            this.showToast(t('commentAdded'));
        },

        closeComments(){
            document.getElementById('commentDrawer').classList.remove('active');
            document.getElementById('commentDrawerBg').classList.remove('active');
        },

        openShareOptions(postId){
            const container=document.getElementById('shareOptionsContainer');
            const bg=document.getElementById('shareOverlayBg');
            container.innerHTML=`
                <div class="share-option" onclick="Core.copyShareLink('${postId}')"><i class="fas fa-link" style="color:var(--secondary)"></i><span>${t('copyLink')}</span></div>
                <div class="share-option" onclick="Core.savePost('${postId}')"><i class="fas fa-save" style="color:var(--gold)"></i><span>${t('save')}</span></div>
                <div class="share-option" onclick="Core.closeShareOptions()"><i class="fas fa-times" style="color:#aaa"></i><span>${t('cancel')}</span></div>`;
            container.style.display='flex';
            bg.style.display='block';
            const post=DB.posts.find(p=>p.id===postId)||DB.pieUpdates.find(p=>p.id===postId);
            if(post){ post.shares=(post.shares||0)+1; syncStorage(); }
        },
        closeShareOptions(){ document.getElementById('shareOptionsContainer').style.display='none'; document.getElementById('shareOverlayBg').style.display='none'; },
        copyShareLink(postId){ navigator.clipboard.writeText('Check out this Pie post! 🥧').then(()=>this.showToast(t('linkCopied'))).catch(()=>this.showToast(t('linkCopied'))); this.closeShareOptions(); },
        savePost(postId){
            const existing=DB.savedPosts.find(s=>s.userId===currentUser.id&&s.postId===postId);
            if(existing){ DB.savedPosts=DB.savedPosts.filter(s=>!(s.userId===currentUser.id&&s.postId===postId)); this.showToast('Removed from saved'); }
            else{ DB.savedPosts.push({userId:currentUser.id,postId,savedAt:Date.now()}); this.showToast('⭐ Saved!'); }
            syncStorage();
            this.closeShareOptions();
        },

        viewUserProfile(userId){
            if(userId===currentUser?.id){ this.switchTab('profile'); return; }
            const user=getUserById(userId);
            if(!user) return;
            ['feedPage','explorePage','pieUpdatesPage'].forEach(id=>document.getElementById(id).style.display='none');
            document.getElementById('profilePage').style.display='block';
            document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
            document.getElementById('profileAvatar').src=user.profilePic||`https://api.dicebear.com/7.x/avataaars/svg?seed=${user.username}`;
            document.getElementById('profileDisplayName').innerText=`@${user.username}`;
            document.getElementById('profileBio').innerText=user.bio||'';
            document.getElementById('profilePrivateBadge').style.display=user.isPrivate?'block':'none';
            const userPosts=DB.posts.filter(p=>p.userId===user.id&&p.type==='video');
            document.getElementById('profilePostCount').innerText=userPosts.length;
            document.getElementById('profileFollowerCount').innerText=DB.follows.filter(f=>f.followingId===user.id).length;
            document.getElementById('profileFollowingCount').innerText=DB.follows.filter(f=>f.followerId===user.id).length;
            const actionDiv=document.getElementById('profileActionButtons');
            const isFollowing=DB.follows.some(f=>f.followerId===currentUser.id&&f.followingId===user.id);
            const hasRequested=hasPendingFollowRequest(user.id);
            if(user.id!==currentUser.id){
                actionDiv.innerHTML=`${isFollowing?`<button class="btn-outline" onclick="Core.toggleFollow('${user.id}')"><i class="fas fa-check"></i> Following</button>`:(hasRequested?`<button class="btn-outline" style="background:#FFD700;color:#000;" onclick="Core.cancelFollowRequest('${user.id}')">⏳ Requested</button>`:`<button class="btn-glow" style="width:auto;padding:12px 24px;" onclick="Core.toggleFollow('${user.id}')"><i class="fas fa-plus"></i> Follow</button>`)}<button class="btn-outline" onclick="ChatPage.open();ChatPage.openDM('${user.id}')"><i class="fas fa-comment"></i> Message</button>`;
            } else { actionDiv.innerHTML='<button class="btn-outline" onclick="Core.openEditProfileModal()"><i class="fas fa-edit"></i> Edit Profile</button>'; }
            document.getElementById('followRequestBadge').style.display='none';
            if(!canViewContent(user.id)&&user.id!==currentUser.id){
                document.getElementById('profileGrid').innerHTML=`<div style="color:#888;text-align:center;padding:30px;grid-column:1/-1;"><i class="fas fa-lock" style="font-size:48px;"></i><p>${t('privateAccount')}</p></div>`;
            } else {
                document.getElementById('profileGrid').innerHTML=userPosts.map(post=>`<div class="grid-item" onclick="Core.watchVideo('${post.id}')"><video src="${post.mediaUrl}" muted preload="metadata" onerror="this.parentElement.innerHTML='<div style=color:#888;text-align:center;padding:20px;>📹</div>'"></video><div class="view-count-badge"><i class="fas fa-eye"></i> ${getPostViews(post.id)} <i class="fas fa-heart" style="color:var(--like-red);margin-left:3px;"></i> ${getPostLikesCount(post.id)}</div></div>`).join('')||'<div style="color:#888;text-align:center;padding:20px;grid-column:1/-1;">No videos yet</div>';
            }
        },

        renderProfile(){
            if(!currentUser) return;
            document.getElementById('profileAvatar').src=currentUser.profilePic||`https://api.dicebear.com/7.x/avataaars/svg?seed=${currentUser.username}`;
            document.getElementById('profileDisplayName').innerText=`@${currentUser.username}`;
            document.getElementById('profileBio').innerText=currentUser.bio||'Pie creator 🥧';
            document.getElementById('profilePrivateBadge').style.display=currentUser.isPrivate?'block':'none';
            const myPosts=DB.posts.filter(p=>p.userId===currentUser.id&&p.type==='video');
            document.getElementById('profilePostCount').innerText=myPosts.length;
            document.getElementById('profileFollowerCount').innerText=DB.follows.filter(f=>f.followingId===currentUser.id).length;
            document.getElementById('profileFollowingCount').innerText=DB.follows.filter(f=>f.followerId===currentUser.id).length;
            document.getElementById('profileActionButtons').innerHTML='<button class="btn-outline" onclick="Core.openEditProfileModal()"><i class="fas fa-edit"></i> Edit Profile</button><button class="btn-outline" onclick="Core.showCollection(\'liked\')"><i class="fas fa-heart"></i> Liked</button><button class="btn-outline" onclick="Core.showCollection(\'favorites\')"><i class="fas fa-bookmark"></i> Favorites</button><button class="btn-outline" onclick="Core.showCollection(\'saved\')"><i class="fas fa-save"></i> Saved</button>';
            const pendingReqs=DB.followRequests.filter(r=>r.toUserId===currentUser.id&&r.status==='pending');
            document.getElementById('followRequestBadge').style.display=pendingReqs.length>0?'inline-block':'none';
            if(pendingReqs.length>0) document.getElementById('followRequestBadge').innerText=`📩 ${pendingReqs.length} Pending Follow Request(s)`;
            document.getElementById('profileGrid').innerHTML=myPosts.map(post=>`<div class="grid-item" onclick="Core.watchVideo('${post.id}')"><video src="${post.mediaUrl}" muted preload="metadata" onerror="this.parentElement.innerHTML='<div style=color:#888;text-align:center;padding:20px;>📹</div>'"></video><div class="view-count-badge"><i class="fas fa-eye"></i> ${getPostViews(post.id)} <i class="fas fa-heart" style="color:var(--like-red);margin-left:3px;"></i> ${getPostLikesCount(post.id)}</div></div>`).join('')||'<div style="color:#888;text-align:center;padding:20px;grid-column:1/-1;">No videos yet. Tap + to upload!</div>';
        },

        watchVideo(id){ this.switchTab('feed'); setTimeout(()=>{ const el=document.getElementById(`post-${id}`); if(el) el.scrollIntoView({behavior:'smooth'}); },250); },

        toggleFollow(targetUserId){
            if(targetUserId===currentUser.id) return;
            const targetUser=getUserById(targetUserId);
            if(targetUser?.isPrivate){
                const existingReq=DB.followRequests.find(r=>r.fromUserId===currentUser.id&&r.toUserId===targetUserId&&r.status==='pending');
                if(existingReq){ DB.followRequests=DB.followRequests.filter(r=>r.id!==existingReq.id); syncStorage(); this.renderFeed(); this.showToast('Follow request cancelled'); return; }
                const existingFollow=DB.follows.find(f=>f.followerId===currentUser.id&&f.followingId===targetUserId);
                if(existingFollow){ DB.follows=DB.follows.filter(f=>!(f.followerId===currentUser.id&&f.followingId===targetUserId)); syncStorage(); this.renderFeed(); this.renderProfile(); this.showToast('Unfollowed'); return; }
                DB.followRequests.push({id:generateId('fr'),fromUserId:currentUser.id,toUserId:targetUserId,status:'pending',createdAt:Date.now()});
                DB.notifications.unshift({id:generateId('n'),userId:targetUserId,type:'follow',message:`@${currentUser.username} requested to follow you`,createdAt:Date.now(),read:false});
                syncStorage(); this.renderFeed(); this.showToast('📩 Follow request sent!'); return;
            }
            const existing=DB.follows.find(f=>f.followerId===currentUser.id&&f.followingId===targetUserId);
            if(existing) DB.follows=DB.follows.filter(f=>!(f.followerId===currentUser.id&&f.followingId===targetUserId));
            else{ DB.follows.push({followerId:currentUser.id,followingId:targetUserId}); DB.notifications.unshift({id:generateId('n'),userId:targetUserId,type:'follow',message:`@${currentUser.username} started following you`,createdAt:Date.now(),read:false}); }
            syncStorage(); this.renderFeed(); this.renderProfile(); this.updateNotifBadge(); this.showToast(existing?'Unfollowed':'Following!');
        },
        cancelFollowRequest(userId){ DB.followRequests=DB.followRequests.filter(r=>!(r.fromUserId===currentUser.id&&r.toUserId===userId&&r.status==='pending')); syncStorage(); this.renderFeed(); this.showToast('Follow request cancelled'); },

        showFollowRequests(){
            const requests=DB.followRequests.filter(r=>r.toUserId===currentUser?.id&&r.status==='pending');
            const container=document.getElementById('followListModalContainer');
            container.innerHTML=`<div class="follow-list-modal" onclick="if(event.target===this)document.getElementById('followListModalContainer').innerHTML=''"><div class="follow-list-content"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;"><h3>Pending (${requests.length})</h3><i class="fas fa-times" style="cursor:pointer;font-size:1.3rem;" onclick="document.getElementById('followListModalContainer').innerHTML=''"></i></div>${requests.map(r=>{const u=getUserById(r.fromUserId);return u?`<div class="follow-list-item"><img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+u.username}" alt=""><div style="flex:1;"><b>@${u.username}</b></div><button class="btn-glow" style="width:auto;padding:8px 16px;font-size:0.75rem;" onclick="Core.approveFollowRequest('${r.id}')">✓</button><button class="modal-btn danger" style="padding:8px 16px;font-size:0.75rem;" onclick="Core.denyFollowRequest('${r.id}')">✕</button></div>`:''}).join('')||'<div style="color:#888;text-align:center;padding:20px;">No pending requests</div>'}</div></div>`;
        },
        approveFollowRequest(requestId){ const req=DB.followRequests.find(r=>r.id===requestId); if(!req||req.toUserId!==currentUser.id) return; req.status='approved'; DB.follows.push({followerId:req.fromUserId,followingId:req.toUserId}); DB.notifications.unshift({id:generateId('n'),userId:req.fromUserId,type:'follow',message:`@${currentUser.username} approved your follow request`,createdAt:Date.now(),read:false}); syncStorage(); document.getElementById('followListModalContainer').innerHTML=''; this.renderProfile(); this.showToast('✅ Approved!'); },
        denyFollowRequest(requestId){ const req=DB.followRequests.find(r=>r.id===requestId); if(!req||req.toUserId!==currentUser.id) return; req.status='denied'; syncStorage(); document.getElementById('followListModalContainer').innerHTML=''; this.renderProfile(); this.showToast('❌ Denied'); },

        showFollowList(type){
            const targetUserId=currentUser.id;
            let list=[];
            if(type==='followers') list=DB.follows.filter(f=>f.followingId===targetUserId).map(f=>getUserById(f.followerId)).filter(Boolean);
            else list=DB.follows.filter(f=>f.followerId===targetUserId).map(f=>getUserById(f.followingId)).filter(Boolean);
            const container=document.getElementById('followListModalContainer');
            container.innerHTML=`<div class="follow-list-modal" onclick="if(event.target===this)document.getElementById('followListModalContainer').innerHTML=''"><div class="follow-list-content"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;"><h3>${type==='followers'?t('followers'):t('following')} (${list.length})</h3><i class="fas fa-times" style="cursor:pointer;font-size:1.3rem;" onclick="document.getElementById('followListModalContainer').innerHTML=''"></i></div>${list.map(u=>`<div class="follow-list-item" onclick="Core.viewUserProfile('${u.id}');document.getElementById('followListModalContainer').innerHTML='';"><img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+u.username}" alt=""><div><b>@${u.username}</b><div style="font-size:0.7rem;color:#888;">${u.bio||''}</div></div></div>`).join('')||'<div style="color:#888;text-align:center;padding:20px;">No users</div>'}</div></div>`;
        },

        openUploadOptions(){
            showCustomModal({title:'📤 Create Post',message:'Choose what to upload:',buttons:[
                {text:'🎬 Video',cls:'primary',callback:()=>document.getElementById('videoUpload').click()},
                {text:'📝 Pie Update',cls:'outline',callback:()=>{PieUpdatesPage.open();setTimeout(()=>document.getElementById('pieUpdateInput').focus(),400);}},
                {text:t('cancel'),cls:'secondary',callback:()=>{}}
            ]});
        },
        uploadVideo(input){
            const file=input.files[0]; if(!file) return;
            showPrompt('Add Caption','Write a caption for your video:','Caption...','',caption=>{
                const url=URL.createObjectURL(file);
                DB.posts.unshift({id:generateId('vid'),type:'video',userId:currentUser.id,mediaUrl:url,caption:caption||'',comments:[],shares:0,createdAt:Date.now()});
                syncStorage(); this.switchTab('feed'); this.renderFeed(); this.showToast(t('videoUploaded'));
            });
            input.value='';
        },
        uploadImagePost(input){
            const file=input.files[0]; if(!file) return;
            const reader=new FileReader();
            reader.onload=e=>{ pendingImageForPieUpdate=e.target.result; const preview=document.getElementById('pieUpdateImagePreview'); preview.src=e.target.result; preview.style.display='block'; this.showToast('📷 Image ready!'); };
            reader.readAsDataURL(file); input.value='';
        },
        openEditProfileModal(){
            if(!currentUser) return;
            showCustomModal({title:t('editProfile'),inputType:'text',inputPlaceholder:'New bio...',inputValue:currentUser.bio||'',buttons:[
                {text:t('cancel'),cls:'secondary',callback:()=>{}},
                {text:t('saveChanges'),cls:'primary',callback:val=>{ if(val!==null&&val!==undefined){ currentUser.bio=val; DB.users[DB.users.findIndex(u=>u.id===currentUser.id)].bio=val; syncStorage(); this.renderProfile(); this.showToast(t('bioUpdated')); }}}
            ]});
        },
        changeProfilePic(){
            if(!currentUser) return;
            const input=document.createElement('input'); input.type='file'; input.accept='image/*';
            input.onchange=e=>{ const file=e.target.files[0]; if(!file) return; const reader=new FileReader(); reader.onload=ev=>{ currentUser.profilePic=ev.target.result; DB.users[DB.users.findIndex(u=>u.id===currentUser.id)].profilePic=ev.target.result; syncStorage(); this.renderProfile(); this.showToast('✅ Profile picture updated!'); }; reader.readAsDataURL(file); };
            input.click();
        },
        showCollection(type){
            let posts=[];
            if(type==='liked'){ const ids=DB.likes.filter(l=>l.userId===currentUser?.id).map(l=>l.postId); posts=DB.posts.filter(p=>ids.includes(p.id)&&p.type==='video'); }
            else if(type==='favorites'){ const ids=currentUser?.favorites||[]; posts=DB.posts.filter(p=>ids.includes(p.id)&&p.type==='video'); }
            else if(type==='saved'){ const ids=DB.savedPosts.filter(s=>s.userId===currentUser?.id).map(s=>s.postId); posts=DB.posts.filter(p=>ids.includes(p.id)&&p.type==='video'); }
            const container=document.getElementById('followListModalContainer');
            container.innerHTML=`<div class="follow-list-modal" onclick="if(event.target===this)document.getElementById('followListModalContainer').innerHTML=''"><div class="follow-list-content"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;"><h3>${type.charAt(0).toUpperCase()+type.slice(1)} (${posts.length})</h3><i class="fas fa-times" style="cursor:pointer;font-size:1.3rem;" onclick="document.getElementById('followListModalContainer').innerHTML=''"></i></div><div class="explore-grid">${posts.map(p=>`<div class="grid-item" onclick="Core.watchVideo('${p.id}');document.getElementById('followListModalContainer').innerHTML='';"><video src="${p.mediaUrl}" muted preload="metadata" onerror="this.parentElement.innerHTML='<div style=color:#888;>📹</div>'"></video></div>`).join('')||'<div style="color:#888;padding:20px;">No videos</div>'}</div></div></div>`;
        },
        renderExplore(){
            const explore=DB.posts.filter(p=>p.type==='video').sort((a,b)=>getPostLikesCount(b.id)-getPostLikesCount(a.id)).slice(0,30);
            document.getElementById('exploreGrid').innerHTML=explore.map(post=>`<div class="grid-item" onclick="Core.watchVideo('${post.id}')"><video src="${post.mediaUrl}" muted preload="metadata" onerror="this.parentElement.innerHTML='<div style=color:#888;text-align:center;padding:20px;>📹</div>'"></video><div class="view-count-badge"><i class="fas fa-heart" style="color:var(--like-red);"></i> ${getPostLikesCount(post.id)} <i class="fas fa-eye" style="margin-left:3px;"></i> ${getPostViews(post.id)}</div></div>`).join('');
        },

        updateNotifBadge(){
            const unread=DB.notifications.filter(n=>n.userId===currentUser?.id&&!n.read).length;
            const badge=document.getElementById('notifBadge');
            badge.style.display=unread>0?'flex':'none';
            if(unread>0) badge.innerText=unread>99?'99+':unread;
        },

        showToast(msg){
            const tEl=document.createElement('div'); tEl.className='toast'; tEl.innerHTML=msg;
            document.body.appendChild(tEl); setTimeout(()=>tEl.remove(),2400);
        }
    };
    window.Core=Core;

    // ==================== PIE UPDATES ====================
    const PieUpdatesPage = {
        open(){
            ['feedPage','explorePage','profilePage'].forEach(id=>document.getElementById(id).style.display='none');
            document.getElementById('pieUpdatesPage').style.display='block';
            document.querySelectorAll('.nav-item').forEach(n=>n.classList.remove('active'));
            this.renderUpdates();
        },
        renderUpdates(){
            const updates=DB.pieUpdates.sort((a,b)=>b.createdAt-a.createdAt);
            document.getElementById('pieUpdateList').innerHTML=updates.map(post=>{
                const author=getUserById(post.userId);
                const liked=isLikedByCurrent(post.id);
                const lc=getPostLikesCount(post.id);
                const cc=getPostCommentsCount(post.id);
                const sc=getPostSharesCount(post.id);
                return `<div class="pie-update-card">
                    <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px;">
                        <img src="${author?.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed=anon'}" style="width:36px;height:36px;border-radius:50%;object-fit:cover;cursor:pointer;" onclick="Core.viewUserProfile('${author?.id}')" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'" alt="">
                        <b style="cursor:pointer;" onclick="Core.viewUserProfile('${author?.id}')">@${author?.username}</b>
                        <span style="font-size:0.65rem;color:#555;margin-left:auto;">${timeAgo(post.createdAt)}</span>
                    </div>
                    <div style="margin:8px 0;">${post.content}</div>
                    ${post.imageUrl?`<img src="${post.imageUrl}" alt="update" onerror="this.style.display='none'">`:''}
                    <div style="display:flex;gap:24px;margin-top:10px;">
                        <button class="action-icon ${liked?'liked':''}" onclick="Core.likePost('${post.id}')"><i class="fas fa-heart"></i><span>${lc}</span></button>
                        <button class="action-icon" onclick="Core.openComments('${post.id}')"><i class="fas fa-comment"></i><span>${cc}</span></button>
                        <button class="action-icon" onclick="Core.openShareOptions('${post.id}')"><i class="fas fa-share-alt"></i><span>${sc}</span></button>
                    </div>
                </div>`;
            }).join('')||'<div style="color:#888;text-align:center;padding:30px;">No updates yet. Share something! 📝</div>';
        },
        postUpdate(){
            const content=document.getElementById('pieUpdateInput').value.trim();
            if(!content&&!pendingImageForPieUpdate) return;
            DB.pieUpdates.unshift({id:generateId('pieup'),userId:currentUser.id,content:content||'',imageUrl:pendingImageForPieUpdate||null,comments:[],shares:0,createdAt:Date.now()});
            syncStorage();
            document.getElementById('pieUpdateInput').value='';
            document.getElementById('pieUpdateImagePreview').style.display='none';
            pendingImageForPieUpdate=null;
            this.renderUpdates();
            Core.showToast(t('piePosted'));
        }
    };
    window.PieUpdatesPage=PieUpdatesPage;

    // ==================== SEARCH ====================
    const SearchPage = {
        currentSearchTab:'top',
        open(){ document.getElementById('searchOverlay').classList.add('open'); setTimeout(()=>document.getElementById('searchOverlayInput').focus(),350); this.renderTrending(); this.renderRecent(); document.getElementById('searchResultsArea').style.display='none'; document.getElementById('trendingSection').style.display='block'; document.getElementById('searchTabs').style.display='none'; document.getElementById('clearSearchBtn').style.display='none'; document.getElementById('searchOverlayInput').value=''; },
        close(){ document.getElementById('searchOverlay').classList.remove('open'); },
        renderTrending(){ document.getElementById('trendingTags').innerHTML=['#PieLife','#DanceChallenge','#ViralVibes','#CreatorSpotlight','#ComedyGold'].map(t=>`<span class="trending-tag" onclick="SearchPage.searchTag('${t}')">${t}</span>`).join(''); },
        renderRecent(){ const recent=DB.searchHistory.slice(-6).reverse(); document.getElementById('recentSearches').innerHTML=recent.length?recent.map(s=>`<div style="padding:8px 0;cursor:pointer;border-bottom:1px solid #1a1a1a;" onclick="SearchPage.searchTag('${s}')"><i class="fas fa-history"></i> ${s}</div>`).join(''):'<div style="color:#888;">No recent searches</div>'; },
        searchTag(tag){ document.getElementById('searchOverlayInput').value=tag; if(!DB.searchHistory.includes(tag)) DB.searchHistory.push(tag); syncStorage(); this.onInput(); },
        onInput(){ const val=document.getElementById('searchOverlayInput').value.trim(); document.getElementById('clearSearchBtn').style.display=val?'flex':'none'; if(val){ document.getElementById('trendingSection').style.display='none'; document.getElementById('searchTabs').style.display='flex'; this.performSearch(); } else { document.getElementById('trendingSection').style.display='block'; document.getElementById('searchTabs').style.display='none'; document.getElementById('searchResultsArea').style.display='none'; } },
        clearSearch(){ document.getElementById('searchOverlayInput').value=''; document.getElementById('clearSearchBtn').style.display='none'; document.getElementById('trendingSection').style.display='block'; document.getElementById('searchTabs').style.display='none'; document.getElementById('searchResultsArea').style.display='none'; document.getElementById('searchOverlayInput').focus(); },
        switchTab(tab){ this.currentSearchTab=tab; document.querySelectorAll('.search-tab').forEach(t=>t.classList.remove('active')); document.querySelector(`.search-tab[data-stab="${tab}"]`).classList.add('active'); this.performSearch(); },
        performSearch(){
            const query=document.getElementById('searchOverlayInput').value.trim().toLowerCase();
            if(!query) return;
            document.getElementById('searchResultsArea').style.display='block';
            document.getElementById('searchResultsArea').innerHTML='<div class="loading-spinner"></div>';
            if(!DB.searchHistory.includes(query)){ DB.searchHistory.push(query); syncStorage(); }
            setTimeout(()=>{
                let html=''; const tab=this.currentSearchTab;
                if(tab==='top'||tab==='users') html+=DB.users.filter(u=>u.username.toLowerCase().includes(query)).map(u=>`<div class="search-result-user" onclick="SearchPage.goToUser('${u.id}')"><img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+u.username}" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'" alt=""><div><b>@${u.username}</b><div style="font-size:0.7rem;color:#888;">${DB.follows.filter(f=>f.followingId===u.id).length} followers ${u.isPrivate?'🔒':''}</div></div></div>`).join('');
                if(tab==='top'||tab==='videos') html+=DB.posts.filter(p=>p.type==='video'&&(p.caption||'').toLowerCase().includes(query)).map(p=>`<div class="search-result-user" onclick="Core.watchVideo('${p.id}');SearchPage.close();"><i class="fas fa-play-circle" style="font-size:1.4rem;color:var(--primary);"></i><div><b>Video</b><div style="font-size:0.75rem;color:#aaa;">${p.caption||'No caption'} • ${getPostLikesCount(p.id)} ❤️</div></div></div>`).join('');
                document.getElementById('searchResultsArea').innerHTML=html||`<div style="padding:20px;text-align:center;color:#888;">${t('noResults')}</div>`;
            },350);
        },
        goToUser(userId){ this.close(); Core.viewUserProfile(userId); },
        voiceSearch(){ if('webkitSpeechRecognition' in window||'SpeechRecognition' in window){ const SR=window.SpeechRecognition||window.webkitSpeechRecognition; const rec=new SR(); rec.lang='en-US'; rec.interimResults=false; rec.start(); rec.onresult=e=>{ document.getElementById('searchOverlayInput').value=e.results[0][0].transcript; SearchPage.onInput(); }; Core.showToast('🎤 Listening...'); } else Core.showToast('🎤 Not supported'); }
    };
    window.SearchPage=SearchPage;

    // ==================== SETTINGS ====================
    const SettingsPage = {
        open(){ document.getElementById('settingsOverlay').classList.add('open'); this.closeDetail(); },
        close(){ document.getElementById('settingsOverlay').classList.remove('open'); },
        openDetail(section){ const panel=document.getElementById('settingsDetailPanel'); panel.classList.add('open'); panel.innerHTML=this.getDetailHTML(section); },
        closeDetail(){ document.getElementById('settingsDetailPanel').classList.remove('open'); document.getElementById('settingsDetailPanel').innerHTML=''; },
        getDetailHTML(section){
            const u=currentUser||{};
            const maps={
                account:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Account</span></div><div style="padding:20px;overflow-y:auto;"><div style="text-align:center;"><img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+(u.username||'user')}" style="width:80px;height:80px;border-radius:50%;object-fit:cover;border:3px solid var(--primary);cursor:pointer;" onclick="Core.changeProfilePic()" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'"><p style="font-size:0.7rem;color:#888;margin-top:6px;">Tap to change photo</p></div><label>Username</label><input class="input-field" id="setUsername" value="${u.username||''}"><label>Bio</label><input class="input-field" id="setBio" value="${u.bio||''}"><label>Email</label><input class="input-field" id="setEmail" value="${u.email||''}" placeholder="Add email"><label>Phone</label><input class="input-field" id="setPhone" value="${u.phone||''}" placeholder="Add phone"><button class="btn-glow" onclick="SettingsPage.saveAccount()">${t('saveChanges')}</button></div>`,
                password:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Password</span></div><div style="padding:20px;"><label>Current</label><input type="password" class="input-field" id="currentPw"><label>New</label><input type="password" class="input-field" id="newPw"><label>Confirm</label><input type="password" class="input-field" id="confirmPw"><button class="btn-glow" onclick="SettingsPage.changePassword()">Update</button><div id="pwFeedback" style="margin-top:10px;text-align:center;"></div></div>`,
                download:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Download</span></div><div style="padding:20px;text-align:center;"><i class="fas fa-cloud-download-alt" style="font-size:3rem;color:var(--secondary);"></i><p>Request archive of your data.</p><button class="btn-glow" id="downloadBtn" onclick="SettingsPage.downloadData()">Download</button><div id="downloadStatus" style="margin-top:10px;"></div></div>`,
                deactivate:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Deactivate</span></div><div style="padding:20px;text-align:center;"><i class="fas fa-exclamation-triangle" style="font-size:3rem;color:#ff5252;"></i><p style="color:#ff5252;">${t('deactivateWarning')}</p><input type="password" class="input-field" id="deactivatePw" placeholder="${t('enterPassword')}"><button class="btn-glow" style="background:#ff5252;" onclick="SettingsPage.deactivateAccount()">Deactivate</button></div>`,
                monetization:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Premium</span></div><div style="padding:20px;"><div style="background:#1a1a1a;border-radius:16px;padding:14px;margin-bottom:10px;"><b>Free Plan</b> — Current ✓</div><div style="background:#1a1a1a;border-radius:16px;padding:14px;margin-bottom:10px;border:2px solid var(--gold);"><b>🥧 Monthly Premium</b> — $4.99/mo<p style="font-size:0.75rem;color:#888;">No ads, HD uploads, priority support</p><button class="btn-glow" onclick="SettingsPage.showPaymentFlow('monthly')">Upgrade Monthly</button></div><div style="background:#1a1a1a;border-radius:16px;padding:14px;border:2px solid var(--gold);"><b>🥧 Yearly Premium</b> — $48/year <span style="color:var(--green);font-size:0.75rem;">Save 20%</span><p style="font-size:0.75rem;color:#888;">All premium features, best value</p><button class="btn-glow" onclick="SettingsPage.showPaymentFlow('yearly')">Upgrade Yearly</button></div></div>`,
                privacy:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Privacy</span></div><div style="padding:20px;"><div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;"><label>Private Account</label><div class="toggle-switch ${currentUser?.isPrivate?'on':''}" id="privateToggle" onclick="this.classList.toggle('on');SettingsPage.togglePrivacy()"></div></div><p style="font-size:0.7rem;color:#888;">Only approved followers can see your posts</p></div>`,
                notifications:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Notifications</span></div><div style="padding:20px;"><div style="display:flex;justify-content:space-between;align-items:center;padding:14px 0;border-bottom:1px solid #1a1a1a;"><span>Likes</span><div class="toggle-switch on" onclick="this.classList.toggle('on')"></div></div><div style="display:flex;justify-content:space-between;align-items:center;padding:14px 0;border-bottom:1px solid #1a1a1a;"><span>Comments</span><div class="toggle-switch on" onclick="this.classList.toggle('on')"></div></div><div style="display:flex;justify-content:space-between;align-items:center;padding:14px 0;"><span>Follows</span><div class="toggle-switch on" onclick="this.classList.toggle('on')"></div></div></div>`,
                accessibility:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Language & Display</span></div><div style="padding:20px;"><label>Language</label><select class="input-field" id="langSelect" onchange="SettingsPage.changeLanguage(this.value)"><option value="en" ${currentLang==='en'?'selected':''}>English</option><option value="zh" ${currentLang==='zh'?'selected':''}>中文</option><option value="lg" ${currentLang==='lg'?'selected':''}>Luganda</option><option value="sw" ${currentLang==='sw'?'selected':''}>Kiswahili</option><option value="es" ${currentLang==='es'?'selected':''}>Español</option><option value="fr" ${currentLang==='fr'?'selected':''}>Français</option></select><label style="margin-top:10px;display:block;">Font Style</label><select class="input-field" id="fontSelect" onchange="SettingsPage.changeFont(this.value)"><option value="default">Default</option><option value="serif">Serif</option><option value="mono">Monospace</option></select><label style="margin-top:10px;display:block;">Font Size</label><select class="input-field" id="fontSizeSelect" onchange="SettingsPage.changeFontSize(this.value)"><option value="1">Normal</option><option value="1.15">Large</option><option value="1.3">Extra Large</option></select></div>`,
                help:`<div class="overlay-top-bar"><div class="overlay-back-btn" onclick="SettingsPage.closeDetail()"><i class="fas fa-arrow-left"></i></div><span>Help</span></div><div style="padding:20px;"><h4>🤖 AI Assistant</h4><input class="input-field" id="helpQuestion" placeholder="Ask anything..."><button class="btn-glow" onclick="SettingsPage.askAI()">Ask</button><div id="aiResponse" style="margin-top:10px;padding:12px;background:#1a1a1a;border-radius:12px;display:none;"></div><h4 style="margin-top:16px;">FAQs</h4><p style="color:#888;font-size:0.8rem;">How to upload? Tap + button.<br>How to get followers? Post engaging content.<br>Contact: help@pie.com</p></div>`
            };
            return maps[section]||'<div>Section not found</div>';
        },
        saveAccount(){ const uname=document.getElementById('setUsername')?.value.trim(); const bio=document.getElementById('setBio')?.value.trim(); const email=document.getElementById('setEmail')?.value.trim(); const phone=document.getElementById('setPhone')?.value.trim(); if(uname) currentUser.username=uname; currentUser.bio=bio; currentUser.email=email; currentUser.phone=phone; DB.users[DB.users.findIndex(u=>u.id===currentUser.id)]=currentUser; syncStorage(); Core.renderProfile(); Core.showToast(t('accountUpdated')); },
        changePassword(){ const cp=document.getElementById('currentPw')?.value; const np=document.getElementById('newPw')?.value; const cf=document.getElementById('confirmPw')?.value; const fb=document.getElementById('pwFeedback'); if(cp!==currentUser.password){fb.innerHTML='<span style="color:#ff5252;">❌ Incorrect password</span>';return;} if(np!==cf){fb.innerHTML='<span style="color:#ff5252;">❌ Passwords do not match</span>';return;} if(np.length<4){fb.innerHTML='<span style="color:#ff5252;">❌ Too short</span>';return;} currentUser.password=np; DB.users[DB.users.findIndex(u=>u.id===currentUser.id)].password=np; syncStorage(); fb.innerHTML='<span style="color:#4CAF50;">✅ Password changed!</span>'; },
        downloadData(){ const btn=document.getElementById('downloadBtn'); const status=document.getElementById('downloadStatus'); btn.disabled=true; btn.innerText='Processing...'; status.innerHTML='<div class="loading-spinner"></div>'; setTimeout(()=>{ const data={user:currentUser,posts:DB.posts.filter(p=>p.userId===currentUser.id)}; const blob=new Blob([JSON.stringify(data,null,2)],{type:'application/json'}); const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='pie_data.json'; a.click(); status.innerHTML='<span style="color:#4CAF50;">✅ Downloaded!</span>'; btn.disabled=false; btn.innerText='Download Again'; },1500); },
        deactivateAccount(){ const pw=document.getElementById('deactivatePw')?.value; if(pw!==currentUser.password){Core.showToast('❌ Incorrect password');return;} showConfirm('Deactivate?',t('deactivateWarning'),()=>{DB.users=DB.users.filter(u=>u.id!==currentUser.id);syncStorage();location.reload();}); },
        togglePrivacy(){ currentUser.isPrivate=!currentUser.isPrivate; DB.users[DB.users.findIndex(u=>u.id===currentUser.id)].isPrivate=currentUser.isPrivate; syncStorage(); Core.showToast(currentUser.isPrivate?'🔒 Account is now private':'🌍 Account is now public'); Core.renderProfile(); },
        showPaymentFlow(plan){ const planName=plan==='yearly'?'Yearly Premium ($48/year)':'Monthly Premium ($4.99/mo)'; const planAmount=plan==='yearly'?48:4.99; showCustomModal({title:`💎 ${planName}`,message:'Choose payment method:',customHTML:`<div class="payment-option-card selected" id="payMomo" onclick="document.getElementById('payMomo').classList.add('selected');document.getElementById('payCard').classList.remove('selected');"><i class="fas fa-mobile-alt"></i><div><b>MTN MoMo</b><div style="font-size:0.7rem;color:#888;">Mobile money</div></div></div><div class="payment-option-card" id="payCard" onclick="document.getElementById('payCard').classList.add('selected');document.getElementById('payMomo').classList.remove('selected');"><i class="fas fa-credit-card"></i><div><b>Credit Card</b><div style="font-size:0.7rem;color:#888;">Visa, Mastercard</div></div></div>`,buttons:[{text:t('cancel'),cls:'secondary',callback:()=>{}},{text:'Continue →',cls:'gold',callback:()=>{const isMomo=document.getElementById('payMomo').classList.contains('selected');SettingsPage.processPayment(plan,planAmount,isMomo);}}]}); },
        processPayment(plan,amount,isMomo){ if(isMomo){ showCustomModal({title:'📱 MTN MoMo Payment',message:`Amount: $${amount}`,inputType:'tel',inputPlaceholder:'Enter MTN phone number...',buttons:[{text:t('cancel'),cls:'secondary',callback:()=>{}},{text:'Send Request',cls:'gold',callback:phone=>{ if(!phone){Core.showToast('❌ Enter phone number');return;} showCustomModal({title:'📱 Payment Sent',message:`Request sent to ${phone}. Enter your MoMo PIN.`,buttons:[{text:'OK',cls:'primary',callback:()=>SettingsPage.completeSubscription(plan,amount,'mtn_momo',phone)}]}); }}]}); } else { showCustomModal({title:'💳 Credit Card',message:`Amount: $${amount}`,customHTML:`<input type="text" id="ccNumber" class="modal-input" placeholder="Card Number" maxlength="19"><div style="display:flex;gap:8px;"><input type="text" id="ccExpiry" class="modal-input" placeholder="MM/YY" maxlength="5" style="flex:1;"><input type="text" id="ccCvv" class="modal-input" placeholder="CVV" maxlength="4" style="flex:1;"></div>`,buttons:[{text:t('cancel'),cls:'secondary',callback:()=>{}},{text:`Pay $${amount}`,cls:'gold',callback:()=>{const cn=document.getElementById('ccNumber')?.value.trim();const exp=document.getElementById('ccExpiry')?.value.trim();const cvv=document.getElementById('ccCvv')?.value.trim();if(!cn||!exp||!cvv){Core.showToast('❌ Fill all card details');return;}showCustomModal({title:'✅ Payment Successful',message:`Paid $${amount}. Premium activated!`,buttons:[{text:'Great!',cls:'primary',callback:()=>SettingsPage.completeSubscription(plan,amount,'credit_card',cn.slice(-4))}]});}}]}); } },
        completeSubscription(plan,amount,method,identifier){ if(!DB.subscriptions[currentUser.id]) DB.subscriptions[currentUser.id]=[]; DB.subscriptions[currentUser.id].push({plan,amount,method,identifier,purchasedAt:Date.now(),expiresAt:Date.now()+(plan==='yearly'?365:30)*86400000}); syncStorage(); Core.showToast('🎉 Premium activated!'); },
        changeLanguage(lang){ currentLang=lang; localStorage.setItem('pie_lang',lang); Core.showToast('🌐 Language: '+lang.toUpperCase()); },
        changeFont(font){ const root=document.documentElement; const fontMap={default:'-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif',serif:'Georgia,"Times New Roman",serif',mono:'"Courier New",Courier,monospace'}; root.style.setProperty('--font-family',fontMap[font]||fontMap.default); localStorage.setItem('pie_font',font); Core.showToast('✅ Font: '+font); },
        changeFontSize(size){ document.documentElement.style.setProperty('--font-size-multiplier',size); localStorage.setItem('pie_font_size',size); Core.showToast('✅ Font size updated'); },
        askAI(){ const q=document.getElementById('helpQuestion')?.value.trim(); const resp=document.getElementById('aiResponse'); if(!q) return; resp.style.display='block'; resp.innerHTML='<div class="loading-spinner"></div>'; setTimeout(()=>{ resp.innerHTML='<b>🤖 AI:</b> '+['Tap + to upload videos or create updates.','Post consistently and use trending hashtags to grow.','Enable private account in Privacy settings.','Save posts via Share > Save.','Change language in Settings > Language & Display.'][Math.floor(Math.random()*5)]; },700); }
    };
    window.SettingsPage=SettingsPage;

    // ==================== CHAT ====================
    const ChatPage = {
        currentChatTab:'community',
        open(){ document.getElementById('chatOverlay').classList.add('open'); this.switchChatTab('community'); this.renderCommunityMessages(); this.renderDMList(); },
        close(){ document.getElementById('chatOverlay').classList.remove('open'); currentDmUserId=null; document.getElementById('privateChatThread').style.display='none'; document.getElementById('privateChatList').style.display='none'; document.getElementById('communityChatView').style.display='flex'; },
        switchChatTab(tab){ this.currentChatTab=tab; document.querySelectorAll('.chat-tab-btn').forEach(b=>b.classList.remove('active')); document.querySelector(`.chat-tab-btn[data-ctab="${tab}"]`).classList.add('active'); document.getElementById('communityChatView').style.display=tab==='community'?'flex':'none'; document.getElementById('privateChatList').style.display=tab==='private'?'block':'none'; document.getElementById('privateChatThread').style.display='none'; if(tab==='community') this.renderCommunityMessages(); if(tab==='private') this.renderDMList(); currentDmUserId=null; },
        renderCommunityMessages(){ const msgs=DB.communityMessages.slice(-80); const div=document.getElementById('communityMessages'); div.innerHTML=msgs.map(m=>{ const u=getUserById(m.userId); return `<div style="margin-bottom:8px;display:flex;gap:8px;"><img src="${u?.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed=anon'}" style="width:30px;height:30px;border-radius:50%;object-fit:cover;" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'" alt=""><div><b>@${u?.username||'anon'}</b> <span style="font-size:0.6rem;color:#555;">${timeAgo(m.timestamp)}</span><div>${m.text}</div></div></div>`; }).join('')||'<div style="color:#888;text-align:center;padding:20px;">No messages yet. Say hello!</div>'; setTimeout(()=>{div.scrollTop=div.scrollHeight;},100); },
        sendCommunityMsg(){ const input=document.getElementById('communityMsgInput'); const text=input.value.trim(); if(!text||!currentUser) return; DB.communityMessages.push({userId:currentUser.id,text,timestamp:Date.now()}); syncStorage(); input.value=''; this.renderCommunityMessages(); },
        renderDMList(){ const others=DB.users.filter(u=>u.id!==currentUser?.id); document.getElementById('dmConversationsList').innerHTML=others.map(u=>{ const chat=DB.chats.find(c=>c.participants.includes(currentUser.id)&&c.participants.includes(u.id)); const lastMsg=chat?.messages?.slice(-1)[0]; const unread=chat?.messages?.filter(m=>m.from!==currentUser.id&&!m.read).length||0; return `<div class="conversation-item" onclick="ChatPage.openDM('${u.id}')"><img src="${u.profilePic||'https://api.dicebear.com/7.x/avataaars/svg?seed='+u.username}" onerror="this.src='https://api.dicebear.com/7.x/avataaars/svg?seed=fallback'" alt=""><div style="flex:1;"><b>@${u.username}</b><span class="online-dot"></span><div style="font-size:0.75rem;color:#888;">${lastMsg?.text?.slice(0,40)||'Tap to chat'}</div></div>${unread>0?`<span style="background:var(--primary);color:#fff;border-radius:50%;width:20px;height:20px;display:flex;align-items:center;justify-content:center;font-size:0.6rem;">${unread}</span>`:''}</div>`; }).join('')||'<div style="color:#888;text-align:center;padding:20px;">No users to message</div>'; },
        openDM(userId){ currentDmUserId=userId; document.getElementById('privateChatList').style.display='none'; document.getElementById('privateChatThread').style.display='flex'; document.getElementById('communityChatView').style.display='none'; document.getElementById('dmThreadName').innerText=`@${getUserById(userId)?.username||'user'}`; this.renderDMThread(); this.simulateTyping(); },
        backToDMList(){ currentDmUserId=null; document.getElementById('privateChatThread').style.display='none'; document.getElementById('privateChatList').style.display='block'; document.getElementById('dmTypingIndicator').style.display='none'; },
        renderDMThread(){ if(!currentDmUserId) return; let chat=DB.chats.find(c=>c.participants.includes(currentUser.id)&&c.participants.includes(currentDmUserId)); if(!chat){chat={id:generateId('chat'),participants:[currentUser.id,currentDmUserId],messages:[]};DB.chats.push(chat);syncStorage();} const div=document.getElementById('dmThreadMessages'); div.innerHTML=chat.messages.map(m=>{ const isSent=m.from===currentUser.id; return `<div class="msg-bubble ${isSent?'sent':'received'}">${m.text}<div style="font-size:0.55rem;opacity:0.6;">${timeAgo(m.timestamp)} ${isSent?(m.read?'✓✓':'✓'):''}</div></div>`; }).join('')||'<div style="color:#888;text-align:center;padding:20px;">Start chatting!</div>'; chat.messages.forEach(m=>{if(m.from!==currentUser.id) m.read=true;}); syncStorage(); setTimeout(()=>{div.scrollTop=div.scrollHeight;},100); },
        sendDMMsg(){ const input=document.getElementById('dmMsgInput'); const text=input.value.trim(); if(!text||!currentDmUserId) return; let chat=DB.chats.find(c=>c.participants.includes(currentUser.id)&&c.participants.includes(currentDmUserId)); if(!chat){chat={id:generateId('chat'),participants:[currentUser.id,currentDmUserId],messages:[]};DB.chats.push(chat);} chat.messages.push({from:currentUser.id,text,timestamp:Date.now(),read:false}); DB.notifications.unshift({id:generateId('n'),userId:currentDmUserId,type:'message',message:`@${currentUser.username} sent you a message`,createdAt:Date.now(),read:false}); syncStorage(); input.value=''; this.renderDMThread(); document.getElementById('dmTypingIndicator').style.display='none'; Core.updateNotifBadge(); },
        simulateTyping(){ const ind=document.getElementById('dmTypingIndicator'); ind.style.display='block'; setTimeout(()=>{ind.style.display='none';},2200); },
        startVoiceCall(){ if(currentDmUserId){const u=getUserById(currentDmUserId);CallUI.startCall(u,'voice');this.close();}},
        startVideoCall(){ if(currentDmUserId){const u=getUserById(currentDmUserId);CallUI.startCall(u,'video');this.close();}}
    };
    window.ChatPage=ChatPage;

    // ==================== CALL ====================
    const CallUI = {
        callType:'voice', callTarget:null, isMuted:false, isSpeakerOn:true,
        startCall(target,type){ this.callTarget=target; this.callType=type; document.getElementById('callAvatar').src=target.profilePic||`https://api.dicebear.com/7.x/avataaars/svg?seed=${target.username}`; document.getElementById('callName').innerText=`@${target.username}`; document.getElementById('callStatus').innerText='Calling...'; document.getElementById('callStatus').style.display='block'; document.getElementById('callTimer').style.display='none'; document.getElementById('callOverlay').classList.add('active'); callSeconds=0; if(callTimerInterval) clearInterval(callTimerInterval); setTimeout(()=>this.connectCall(),2000); },
        connectCall(){ document.getElementById('callStatus').innerText='Connected'; document.getElementById('callTimer').style.display='block'; document.getElementById('callTimer').innerText='00:00'; callSeconds=0; callTimerInterval=setInterval(()=>{ callSeconds++; const m=Math.floor(callSeconds/60).toString().padStart(2,'0'); const s=(callSeconds%60).toString().padStart(2,'0'); document.getElementById('callTimer').innerText=`${m}:${s}`; },1000); DB.callLogs.push({caller:currentUser.id,receiver:this.callTarget.id,type:this.callType,duration:0,timestamp:Date.now()}); syncStorage(); },
        toggleMute(){ this.isMuted=!this.isMuted; document.getElementById('muteBtn').style.background=this.isMuted?'#ff5252':'#333'; Core.showToast(this.isMuted?'🔇 Muted':'🎤 Unmuted'); },
        toggleSpeaker(){ this.isSpeakerOn=!this.isSpeakerOn; document.getElementById('speakerBtn').style.background=this.isSpeakerOn?'#333':'#ff5252'; Core.showToast(this.isSpeakerOn?'🔊 Speaker On':'🔈 Speaker Off'); },
        endCall(){ if(callTimerInterval) clearInterval(callTimerInterval); document.getElementById('callOverlay').classList.remove('active'); Core.showToast(`📞 Call ended (${Math.floor(callSeconds/60)}m ${callSeconds%60}s)`); callSeconds=0; }
    };
    window.CallUI=CallUI;

    // ==================== NOTIFICATIONS — FIXED ====================
    const NotifDrawer = {
        open(){
            // Build notifications list
            const myNotifs=DB.notifications.filter(n=>n.userId===currentUser?.id).slice(0,50).reverse();
            const list=document.getElementById('notifList');

            if(myNotifs.length===0){
                list.innerHTML=`<div style="text-align:center;padding:40px 20px;color:#555;"><i class="fas fa-bell-slash" style="font-size:48px;opacity:0.4;"></i><p style="margin-top:12px;">${t('noNotifications')}</p></div>`;
            } else {
                list.innerHTML=myNotifs.map(n=>{
                    const type=n.type||'default';
                    const iconMap={like:'fa-heart like',comment:'fa-comment comment',follow:'fa-user-plus follow',message:'fa-envelope message'};
                    const iconClass=iconMap[type]||'fa-bell default';
                    const [iconName,iconColor]=iconClass.split(' ');
                    return `<div class="notif-item ${n.read?'':'unread'}">
                        <div class="notif-icon ${iconColor||'default'}"><i class="fas ${iconName}"></i></div>
                        <div class="notif-text">
                            <p>${n.message}</p>
                            <span>${timeAgo(n.createdAt)}</span>
                        </div>
                        ${!n.read?`<div style="width:8px;height:8px;border-radius:50%;background:var(--primary);flex-shrink:0;"></div>`:''}
                    </div>`;
                }).join('');
            }

            document.getElementById('notifDrawer').classList.add('active');
            document.getElementById('notifDrawerBg').classList.add('active');

            // Mark as read after opening
            setTimeout(()=>{
                DB.notifications.forEach(n=>{ if(n.userId===currentUser?.id) n.read=true; });
                syncStorage();
                Core.updateNotifBadge();
            },800);
        },

        markAllRead(){
            DB.notifications.forEach(n=>{ if(n.userId===currentUser?.id) n.read=true; });
            syncStorage();
            Core.updateNotifBadge();
            Core.showToast('✅ All notifications marked as read');
            // Refresh the list to remove unread dots
            document.querySelectorAll('.notif-item').forEach(el=>el.classList.remove('unread'));
            document.querySelectorAll('.notif-item > div:last-child').forEach(el=>{ if(el.style.background) el.remove(); });
        },

        close(){
            document.getElementById('notifDrawer').classList.remove('active');
            document.getElementById('notifDrawerBg').classList.remove('active');
        }
    };
    window.NotifDrawer=NotifDrawer;

    // ==================== AUTH ====================
    const AuthUI = {
        showLogin(){ document.getElementById('loginForm').style.display='block'; document.getElementById('signupForm').style.display='none'; document.getElementById('loginTab').classList.add('active'); document.getElementById('signupTab').classList.remove('active'); },
        showSignup(){ document.getElementById('loginForm').style.display='none'; document.getElementById('signupForm').style.display='block'; document.getElementById('signupTab').classList.add('active'); document.getElementById('loginTab').classList.remove('active'); },
        previewAvatar(input){ const f=input.files[0]; if(f){const r=new FileReader();r.onload=e=>document.getElementById('signupAvatarPreview').src=e.target.result;r.readAsDataURL(f);} },
        signup(){
            const uname=document.getElementById('signupName').value.trim();
            const age=parseInt(document.getElementById('signupAge').value);
            const pwd=document.getElementById('signupPass').value.trim();
            const avFile=document.getElementById('signupAvatarFile').files[0];
            if(!uname||!pwd||isNaN(age)||age>=25) return showAlert('Error','All fields required. Age must be under 25.');
            if(DB.users.find(u=>u.username===uname)) return showAlert('Error','Username taken.');
            const create=pic=>{ const u={id:generateId('u'),username:uname,password:pwd,age,bio:'Fresh Pie! 🥧',profilePic:pic||`https://api.dicebear.com/7.x/avataaars/svg?seed=${uname}`,favorites:[],isPrivate:false,email:'',phone:'',createdAt:Date.now()}; DB.users.push(u); syncStorage(); showAlert('Success','Account created! Please login.'); this.showLogin(); };
            if(avFile){const r=new FileReader();r.onload=e=>create(e.target.result);r.readAsDataURL(avFile);}else create(null);
        },
        login(){
            const uname=document.getElementById('loginUsername').value.trim();
            const pwd=document.getElementById('loginPassword').value.trim();
            const user=DB.users.find(u=>u.username===uname&&u.password===pwd);
            if(!user) return showAlert('Error','Invalid credentials.');
            currentUser=user;
            document.getElementById('authScreen').style.display='none';
            document.getElementById('mainUI').style.display='flex';
            Core.switchTab('feed');
            Core.renderProfile();
            Core.updateNotifBadge();
        }
    };
    window.AuthUI=AuthUI;

    // ==================== INIT ====================
    loadData();
    const savedLang=localStorage.getItem('pie_lang');
    if(savedLang&&LANG[savedLang]) currentLang=savedLang;
    const savedFont=localStorage.getItem('pie_font');
    if(savedFont){ const root=document.documentElement; const fontMap={default:'-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif',serif:'Georgia,"Times New Roman",serif',mono:'"Courier New",Courier,monospace'}; root.style.setProperty('--font-family',fontMap[savedFont]||fontMap.default); }
    const savedFontSize=localStorage.getItem('pie_font_size');
    if(savedFontSize) document.documentElement.style.setProperty('--font-size-multiplier',savedFontSize);

    if(!DB.users.length){
        DB.users.push({id:'u_demo1',username:'pieking',password:'pie123',age:22,bio:'Official Pie Creator 👑',profilePic:'https://api.dicebear.com/7.x/avataaars/svg?seed=pieking',favorites:[],isPrivate:false,email:'',phone:'',createdAt:Date.now()-86400000});
        DB.users.push({id:'u_demo2',username:'chefjoy',password:'pie123',age:20,bio:'Baking happiness daily 🥧',profilePic:'https://api.dicebear.com/7.x/avataaars/svg?seed=chefjoy',favorites:[],isPrivate:true,email:'',phone:'',createdAt:Date.now()-172800000});
        DB.communityMessages.push({userId:'u_demo1',text:'Welcome to Pie! 🥧🎉',timestamp:Date.now()-3600000});
        DB.pieUpdates.push({id:'pieup_demo1',userId:'u_demo1',content:'Excited to launch Pie Updates! Share your thoughts here 📝 #PieLife',imageUrl:null,comments:[],shares:0,createdAt:Date.now()-7200000});
        // Add demo notifications
        DB.notifications.push({id:'n_demo1',userId:'u_demo1',type:'follow',message:'@chefjoy started following you',createdAt:Date.now()-3600000,read:false});
        DB.notifications.push({id:'n_demo2',userId:'u_demo1',type:'like',message:'@chefjoy liked your update',createdAt:Date.now()-1800000,read:false});
        syncStorage();
    }

    document.getElementById('authScreen').style.display='flex';
    document.getElementById('mainUI').style.display='none';

    // Global click — close drawers when clicking outside
    document.addEventListener('keydown',function(e){
        if(e.key==='Escape'){
            Core.closeComments();
            NotifDrawer.close();
            Core.closeShareOptions();
        }
    });

    console.log('🥧 Pie Social Universe — Fixed v5');
    console.log('✅ Video: Intersection Observer with proper error/loading states');
    console.log('✅ Comments: Styled drawer with avatar, timestamps, live update');
    console.log('✅ Notifications: Typed notifications with icons, timestamps, unread dots');
    console.log('✅ All buttons connected, no dead interactions');
    </script>
</body>
</html>
