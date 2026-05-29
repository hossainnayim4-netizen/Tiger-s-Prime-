<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Team Tigers • Premium Scorer</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        /* ========== ULTRA-PREMIUM ELITE THEME ========== */
        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; font-family: 'Poppins', sans-serif; }
        
        :root {
            --bg-main: #070B14; 
            --bg-card: #121A2F;
            --primary: #FF2A46; 
            --primary-glow: rgba(255, 42, 70, 0.5);
            --accent: #FFBE0B; 
            --accent-glow: rgba(255, 190, 11, 0.4);
            --text-main: #FFFFFF;
            --text-muted: #9CA3AF;
            --sheet-bg: #0F172A; /* Darkened for scoreboard visibility */
            --border-light: rgba(255, 255, 255, 0.08);
            --glass-shadow: 0 10px 40px rgba(0, 0, 0, 0.4);
            --success: #10B981;
            --info: #3B82F6;
            --gold-gradient: linear-gradient(135deg, #FFD700, #DAA520, #B8860B);
        }

        body { background-color: var(--bg-main); background-image: radial-gradient(circle at 50% -20%, #121A2F 0%, #070B14 80%); color: var(--text-main); height: 100vh; display: flex; flex-direction: column; overflow: hidden; transition: all 0.3s ease; }

        /* SCREEN SHAKE EFFECT */
        @keyframes shake {
            0% { transform: translate(1px, 1px) rotate(0deg); }
            10% { transform: translate(-1px, -2px) rotate(-1deg); }
            20% { transform: translate(-3px, 0px) rotate(1deg); }
            30% { transform: translate(3px, 2px) rotate(0deg); }
            40% { transform: translate(1px, -1px) rotate(1deg); }
            50% { transform: translate(-1px, 2px) rotate(-1deg); }
            60% { transform: translate(-3px, 1px) rotate(0deg); }
            70% { transform: translate(3px, 1px) rotate(-1deg); }
            80% { transform: translate(-1px, -1px) rotate(1deg); }
            90% { transform: translate(1px, 2px) rotate(0deg); }
            100% { transform: translate(1px, -2px) rotate(-1deg); }
        }
        .shake-screen { animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both; }

        /* BACKGROUND PARTICLES */
        #particles-container { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 1; overflow: hidden; }
        .particle { position: absolute; background: rgba(255, 190, 11, 0.2); border-radius: 50%; animation: floatUp linear infinite; }
        @keyframes floatUp { 0% { transform: translateY(100vh) scale(0); opacity: 1; } 100% { transform: translateY(-10vh) scale(1.5); opacity: 0; } }

        /* LOADER */
        #ultra-loader { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: var(--bg-main); z-index: 99999; display: flex; flex-direction: column; justify-content: center; align-items: center; transition: opacity 0.4s ease; }
        .loader-logo i { font-size: 4rem; color: var(--accent); filter: drop-shadow(0 0 25px var(--accent-glow)); animation: pulseGlow 1.5s infinite alternate; }
        .loader-text { margin-top: 20px; font-size: 1.5rem; font-weight: 900; letter-spacing: 4px; background: var(--gradient-2); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .loader-bar-container { width: 200px; height: 4px; background: rgba(255,255,255,0.1); margin-top: 20px; border-radius: 4px; overflow: hidden; }
        .loader-bar { height: 100%; width: 0%; background: var(--accent); box-shadow: 0 0 10px var(--accent-glow); transition: width 0.3s; }
        @keyframes pulseGlow { 0% { transform: scale(0.95); filter: drop-shadow(0 0 15px var(--accent-glow)); } 100% { transform: scale(1.05); filter: drop-shadow(0 0 35px var(--accent-glow)); } }

        /* HEADER & TICKER */
        header { position: relative; z-index: 30; padding: 20px 24px 10px; display: flex; justify-content: space-between; align-items: center; }
        .header-title { font-size: 1.4rem; font-weight: 900; letter-spacing: 0.5px; text-shadow: 0 0 10px rgba(255,255,255,0.2); display: flex; align-items: center; gap: 8px; }
        .header-title span { color: var(--accent); text-shadow: 0 0 15px var(--accent-glow); }
        .header-actions { display: flex; align-items: center; gap: 16px; }
        .wallet-badge { background: rgba(255,190,11,0.15); color: var(--accent); padding: 6px 14px; border-radius: 20px; font-size: 0.9rem; font-weight: 800; border: 1px solid rgba(255,190,11,0.3); display: flex; align-items: center; gap: 6px; cursor: pointer; transition: 0.3s; box-shadow: 0 0 10px rgba(255,190,11,0.2); }
        .wallet-badge:active { transform: scale(0.95); }
        .notification-bell { font-size: 1.3rem; color: var(--text-main); position: relative; cursor: pointer; transition: 0.3s; }
        .notif-badge { position: absolute; top: -5px; right: -5px; background: var(--primary); color: #fff; border-radius: 50%; width: 18px; height: 18px; font-size: 0.6rem; font-weight: 800; display: none; align-items: center; justify-content: center; box-shadow: 0 0 8px var(--primary-glow); }

        .live-ticker { background: rgba(255, 42, 70, 0.1); border-top: 1px solid rgba(255,42,70,0.2); border-bottom: 1px solid rgba(255,42,70,0.2); padding: 6px 0; overflow: hidden; white-space: nowrap; font-size: 0.75rem; font-weight: 700; color: var(--accent); text-transform: uppercase; letter-spacing: 2px; }
        .ticker-content { display: inline-block; animation: scrollTicker 20s linear infinite; }
        @keyframes scrollTicker { 0% { transform: translateX(100vw); } 100% { transform: translateX(-100%); } }

        /* MAIN CONTAINER */
        #main-container { position: relative; z-index: 10; flex: 1; overflow-y: auto; padding: 10px 20px 120px; scrollbar-width: none; }
        #main-container::-webkit-scrollbar { display: none; }
        .section { display: none; opacity: 0; transform: translateY(20px); transition: all 0.3s ease; }
        .section.active { display: block; opacity: 1; transform: translateY(0); }

        .card { background: var(--bg-card); backdrop-filter: blur(16px); border-radius: 20px; padding: 20px; margin-bottom: 16px; box-shadow: var(--glass-shadow); border: 1px solid var(--border-light); transition: transform 0.3s ease, box-shadow 0.3s; transform-style: preserve-3d; perspective: 1000px; }
        .card:hover { transform: translateY(-2px) scale(1.01); box-shadow: 0 15px 35px rgba(0,0,0,0.5); }
        .notice-card { border-left: 4px solid var(--accent); background: linear-gradient(90deg, rgba(255, 190, 11, 0.05) 0%, var(--bg-card) 100%); }
        
        .btn-primary { background: linear-gradient(135deg, var(--primary), #D90429); color: #fff; font-weight: 800; padding: 16px 24px; border: none; border-radius: 14px; font-size: 1rem; cursor: pointer; transition: 0.3s; width: 100%; text-align: center; box-shadow: 0 10px 30px var(--primary-glow); text-transform: uppercase; letter-spacing: 1px; position: relative; overflow: hidden; }
        .btn-primary:active { transform: scale(0.96); box-shadow: 0 5px 15px var(--primary-glow); }
        .btn-outline { background: transparent; border: 2px solid var(--primary); color: var(--primary); font-weight: 700; padding: 14px 24px; border-radius: 14px; font-size: 1rem; width: 100%; cursor: pointer; box-shadow: inset 0 0 10px rgba(255,42,70,0.1); transition: 0.2s; }
        .btn-outline:active { transform: scale(0.96); }
        .btn-small { background: rgba(255,255,255,0.08); border: 1px solid rgba(255,255,255,0.1); color: #fff; font-weight: 600; padding: 10px 18px; border-radius: 10px; font-size: 0.85rem; cursor: pointer; transition: 0.2s; }
        
        .ripple { position: absolute; background: rgba(255, 255, 255, 0.4); border-radius: 50%; transform: scale(0); animation: rippleEffect 0.6s linear; pointer-events: none; }
        @keyframes rippleEffect { to { transform: scale(4); opacity: 0; } }

        .login-input { width: 100%; padding: 16px 20px; border-radius: 14px; border: 1px solid rgba(255,255,255,0.1); background: rgba(0,0,0,0.4); color: #fff; font-size: 0.95rem; outline: none; margin-bottom: 14px; transition: 0.3s; backdrop-filter: blur(5px); }
        .login-input:focus { border-color: var(--accent); background: rgba(0,0,0,0.6); box-shadow: 0 0 20px rgba(255,190,11,0.15); transform: translateY(-2px); }

        .fab-score { position: fixed; bottom: 100px; right: 20px; background: linear-gradient(135deg, var(--accent), #FF9F1C); color: #000; border: none; border-radius: 30px; padding: 16px 24px; font-weight: 900; font-size: 1rem; box-shadow: 0 15px 35px rgba(255, 190, 11, 0.4); z-index: 99; cursor: pointer; display: flex; align-items: center; gap: 8px; text-transform: uppercase; transition: 0.3s; animation: floatBtn 3s ease-in-out infinite; }
        .fab-score:active { transform: scale(0.95); }
        @keyframes floatBtn { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-5px); } }

        .modal { position: fixed; top:0; left:0; width:100%; height:100%; background: rgba(5, 8, 15, 0.85); backdrop-filter: blur(12px); display:none; justify-content:center; align-items:center; z-index:50000; padding: 20px; }
        .modal.active { display: flex !important; animation: zoomIn 0.3s ease; }
        @keyframes zoomIn { from { transform:scale(0.95); opacity:0; } to { transform:scale(1); opacity:1; } }
        .modal-content { background: var(--bg-card); border-radius: 28px; padding: 28px; width: 100%; max-width: 460px; border: 1px solid var(--border-light); max-height: 85vh; overflow-y: auto; box-shadow: 0 20px 50px rgba(0,0,0,0.7); }
        .modal-content::-webkit-scrollbar { width: 4px; }
        .modal-content::-webkit-scrollbar-thumb { background: var(--primary); border-radius: 10px; }

        .nav-bar { position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); background: rgba(13, 20, 36, 0.95); backdrop-filter: blur(25px); border: 1px solid rgba(255,255,255,0.15); border-radius: 40px; display: flex; justify-content: center; gap: 15px; padding: 8px 16px; z-index: 100; box-shadow: 0 15px 35px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,255,255,0.1); }
        .nav-item { color: var(--text-muted); font-size: 1.2rem; padding: 12px; border-radius: 50%; transition: 0.3s; cursor: pointer; display: flex; align-items: center; justify-content: center; width: 45px; height: 45px; position: relative; }
        .nav-item.active { background: rgba(255,42,70,0.15); color: var(--primary); box-shadow: 0 5px 20px rgba(255,42,70,0.3); border: 1px solid rgba(255, 42, 70, 0.3); transform: translateY(-3px); }

        /* AUTH OVERLAY */
        .auth-overlay { position: fixed; top:0; left:0; width:100%; height:100%; background: var(--bg-main); background-image: radial-gradient(circle at 50% 10%, #121A2F 0%, #070B14 100%); z-index: 9999; display: none; flex-direction: column; align-items: center; justify-content: center; padding: 24px; }
        .auth-container { width: 100%; max-width: 380px; }
        .auth-logo { text-align: center; margin-bottom: 30px; }
        .auth-logo i { font-size: 3.5rem; color: var(--accent); margin-bottom: 12px; filter: drop-shadow(0 0 20px var(--accent-glow)); animation: pulseGlow 1.5s infinite alternate; }
        .auth-logo h1 { font-size: 2rem; font-weight: 900; line-height: 1.2; text-shadow: 0 0 10px rgba(255,255,255,0.1); }
        .auth-tabs { display: flex; background: rgba(0,0,0,0.4); border-radius: 14px; padding: 5px; margin-bottom: 24px; border: 1px solid rgba(255,255,255,0.05); }
        .auth-tab { flex: 1; text-align: center; padding: 12px; border-radius: 10px; font-weight: 700; font-size: 0.9rem; cursor: pointer; color: var(--text-muted); transition: 0.3s; }
        .auth-tab.active { background: var(--primary); color: #fff; box-shadow: 0 4px 15px var(--primary-glow); }
        .auth-form { display: none; animation: fadeIn 0.3s; }
        .auth-form.active { display: block; }

        /* ================= FIXED DARK PREMIUM SCOREBOARD ================= */
        .scoreboard-full-wrapper { display: flex; flex-direction: column; height: calc(100vh - 120px); margin: -10px -20px 0; }
        .score-top { padding: 20px 20px 30px; position: relative; background: transparent; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .score-badge-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
        .inning-badge { background: rgba(255,190,11,0.15); padding: 4px 12px; border-radius: 20px; font-size: 0.75rem; font-weight: 800; color: var(--accent); border: 1px solid rgba(255,190,11,0.3); }
        .live-dot { color: var(--primary); font-size: 0.75rem; font-weight: 700; text-shadow: 0 0 10px var(--primary-glow); animation: blink 1.5s infinite; }
        @keyframes blink { 50% { opacity: 0.3; } }
        
        .batting-team-title { font-size: 1.1rem; color: var(--text-muted); font-weight: 800; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 4px; text-align: center; }
        
        /* 3D Flip Score Animation */
        .main-score { font-size: 4.5rem; font-weight: 900; line-height: 1; margin-bottom: 16px; letter-spacing: -2px; text-shadow: 0 0 30px rgba(255,255,255,0.15); text-align: center; display: inline-block; width: 100%; }
        .flip-animate { animation: flipIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275); }
        @keyframes flipIn { 0% { transform: rotateX(-90deg); opacity: 0; } 100% { transform: rotateX(0deg); opacity: 1; } }
        .main-score span { font-size: 2.2rem; opacity: 0.6; font-weight: 600; }
        
        .score-advanced-data { display: flex; justify-content: space-between; font-size: 0.8rem; font-weight: 700; color: var(--text-muted); margin-bottom: 10px; padding: 0 10px; }
        .win-prob-container { width: 100%; height: 6px; background: rgba(255,255,255,0.1); border-radius: 10px; margin-bottom: 16px; overflow: hidden; display: flex; }
        .win-prob-bar-a { height: 100%; background: var(--primary); width: 50%; box-shadow: 0 0 10px var(--primary-glow); transition: width 0.5s ease; }
        .win-prob-bar-b { height: 100%; background: var(--info); width: 50%; box-shadow: 0 0 10px rgba(59,130,246,0.5); transition: width 0.5s ease; }

        .score-meta { display: flex; justify-content: center; gap: 15px; }
        .meta-box { flex: 1; text-align: center; background: rgba(0,0,0,0.5); padding: 14px 20px; border-radius: 18px; border: 1px solid rgba(255,190,11,0.2); box-shadow: inset 0 1px 0 rgba(255,255,255,0.1); backdrop-filter: blur(10px); }
        .meta-label { font-size: 0.8rem; color: var(--accent); font-weight: 800; letter-spacing: 2px; margin-bottom: 6px; text-transform: uppercase; }
        .meta-value { font-size: 1.8rem; font-weight: 900; color: #fff; line-height: 1; text-shadow: 0 0 10px rgba(255,255,255,0.2); }

        /* FIXED DARK KEYPAD AREA */
        .score-bottom { flex: 1; background: var(--sheet-bg); border-radius: 35px 35px 0 0; padding: 24px 20px; box-shadow: 0 -10px 40px rgba(0,0,0,0.8); border-top: 1px solid rgba(255,255,255,0.05); display: flex; flex-direction: column; }
        .timeline-container { display: flex; align-items: center; gap: 10px; margin-bottom: 16px; overflow-x: auto; padding-bottom: 5px; scrollbar-width: none; }
        .timeline-label { font-size: 0.8rem; font-weight: 800; color: var(--text-muted); text-transform: uppercase; white-space: nowrap; }
        .ball-dot { width: 28px; height: 28px; border-radius: 50%; background: rgba(255,255,255,0.1); display: flex; align-items: center; justify-content: center; font-size: 0.8rem; font-weight: 800; color: #fff; flex-shrink: 0; transition: 0.3s; }
        .ball-dot.four { background: rgba(59,130,246,0.2); color: var(--info); border: 1px solid var(--info); box-shadow: 0 0 8px rgba(59,130,246,0.4); }
        .ball-dot.six { background: rgba(16,185,129,0.2); color: var(--success); border: 1px solid var(--success); box-shadow: 0 0 8px rgba(16,185,129,0.4); }
        .ball-dot.out { background: rgba(255,42,70,0.2); color: var(--primary); border: 1px solid var(--primary); box-shadow: 0 0 8px var(--primary-glow); }
        .ball-dot.extra { background: rgba(255,190,11,0.2); color: var(--accent); font-size: 0.7rem; border: 1px solid var(--accent); box-shadow: 0 0 8px var(--accent-glow); }

        /* DARK STATS LIST */
        .stats-list { background: rgba(0,0,0,0.3); border-radius: 16px; padding: 12px 16px; box-shadow: inset 0 2px 10px rgba(0,0,0,0.5); border: 1px solid rgba(255,255,255,0.05); margin-bottom: 20px; }
        .stat-row { display: flex; justify-content: space-between; align-items: center; padding: 10px 0; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .stat-row:last-child { border-bottom: none; }
        .stat-name { font-weight: 700; font-size: 1rem; color: #fff; display:flex; align-items:center; gap:8px; width: 60%; }
        .stat-val { font-weight: 900; font-size: 1.1rem; color: #fff; text-align: right; width: 40%; display: flex; flex-direction: column; align-items: flex-end;}
        .stat-sub { font-size: 0.7rem; color: var(--accent); font-weight: 700; }
        
        .fire-effect::after { content: '🔥'; margin-left: 4px; animation: fireBurn 0.5s infinite alternate; }
        @keyframes fireBurn { 0% { transform: scale(1); filter: hue-rotate(0deg); } 100% { transform: scale(1.2); filter: hue-rotate(20deg); } }

        .indicator { width: 8px; height: 8px; background: transparent; border-radius: 50%; }
        .indicator.active { background: var(--primary); box-shadow: 0 0 10px var(--primary-glow); }
        
        select.manual-select { background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); border-radius: 10px; outline: none; font-family: 'Poppins'; font-weight: 600; color: #fff; font-size: 0.85rem; width: 100%; cursor: pointer; padding: 8px 10px; transition: border-color 0.2s; }
        select.manual-select:focus { border-color: var(--primary); }
        select.manual-select option { background: var(--bg-card); color: #fff; }

        /* DARK PREMIUM KEYPAD */
        .keypad { display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px; justify-items: center; margin-bottom: 20px; }
        .key-btn { width: 100%; height: 55px; border-radius: 14px; background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1); box-shadow: 0 4px 10px rgba(0,0,0,0.3); display: flex; align-items: center; justify-content: center; font-size: 1.2rem; font-weight: 900; color: #fff; cursor: pointer; transition: 0.2s; position: relative; overflow: hidden; }
        .key-btn:active { transform: scale(0.92); box-shadow: 0 2px 5px rgba(0,0,0,0.5); background: rgba(255,255,255,0.1); }
        .key-btn.extra { font-size: 0.95rem; color: var(--accent); background: rgba(255,190,11,0.08); border-color: rgba(255,190,11,0.2); }
        .key-btn.four { color: var(--info); background: rgba(59,130,246,0.1); border-color: rgba(59,130,246,0.3); }
        .key-btn.six { color: var(--success); background: rgba(16,185,129,0.1); border-color: rgba(16,185,129,0.3); }
        .key-btn.out { background: linear-gradient(135deg, var(--primary), #D90429); color: #fff; border: none; box-shadow: 0 6px 20px var(--primary-glow); width: 100%; border-radius: 14px; grid-column: span 2; }
        .key-btn.undo { font-size: 1.1rem; color: var(--text-muted); background: rgba(255,255,255,0.02); }

        /* CINEMATIC POPUP */
        .cinematic-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); backdrop-filter: blur(15px); z-index: 100000; display: none; justify-content: center; align-items: center; flex-direction: column; }
        .cinematic-text { font-size: 6rem; font-weight: 900; font-style: italic; text-transform: uppercase; letter-spacing: -2px; transform: scale(0.5) rotate(-10deg); opacity: 0; }
        .cinematic-overlay.active { display: flex; }
        .cinematic-overlay.active .cinematic-text { animation: smashIn 1.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
        .event-six { color: var(--accent); text-shadow: 0 0 30px var(--accent), 0 0 80px #fff; } 
        .event-six-particles { position: absolute; width: 100%; height: 100%; background: radial-gradient(circle, transparent 20%, #FFD700 80%); opacity: 0.5; mix-blend-mode: color-dodge; animation: explode 1s ease-out; }
        @keyframes explode { 0% { transform: scale(0); opacity: 1; } 100% { transform: scale(3); opacity: 0; } }
        .event-four { color: var(--info); text-shadow: 0 0 30px var(--info), 0 0 80px #fff; } 
        .event-out { color: var(--primary); text-shadow: 0 0 30px var(--primary), 0 0 60px var(--primary); }
        @keyframes smashIn { 0% { transform: scale(3) rotate(20deg); opacity: 0; } 40% { transform: scale(0.9) rotate(-5deg); opacity: 1; } 60% { transform: scale(1.1) rotate(2deg); opacity: 1; } 100% { transform: scale(1) rotate(0deg); opacity: 1; filter: blur(0); } }

        /* WIZARD & FORMS */
        .wizard-step { display: none; animation: fadeIn 0.3s; }
        .wizard-step.active { display: block; }
        .setup-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 16px; }
        .radio-box { border: 1px solid rgba(255,255,255,0.1); background: rgba(0,0,0,0.2); border-radius: 12px; padding: 14px; text-align: center; cursor: pointer; font-weight: 700; font-size: 0.9rem; transition: 0.2s; color:#fff;}
        .radio-box.active { border-color: var(--accent); background: rgba(255, 190, 11, 0.15); color: var(--accent); box-shadow: inset 0 0 10px var(--accent-glow); }
        .team-player-list { background: rgba(0,0,0,0.3); border-radius: 14px; padding: 12px; max-height: 140px; overflow-y: auto; display: flex; flex-wrap: wrap; gap: 6px; border: 1px solid var(--border-light); }
        .added-player-tag { background: rgba(255,255,255,0.08); color: #fff; padding: 6px 12px; border-radius: 16px; font-size: 0.8rem; font-weight: 600; display: flex; align-items: center; gap: 6px; }
        
        .image-upload-wrapper { position: relative; width: 100px; height: 100px; margin: 0 auto 20px; }
        .image-upload-input { position: absolute; top: 0; left: 0; width: 100%; height: 100%; opacity: 0; cursor: pointer; z-index: 2; }
        .image-upload-preview { width: 100%; height: 100%; border-radius: 50%; background: rgba(0,0,0,0.3); border: 2px dashed rgba(255,255,255,0.2); display: flex; align-items: center; justify-content: center; overflow: hidden; }
        .image-upload-preview img { width: 100%; height: 100%; object-fit: cover; }
        
        .toast { background: var(--sheet-bg); color: #fff; border-radius: 12px; padding: 14px 20px; position: fixed; top: 80px; left: 50%; transform: translateX(-50%); display: none; z-index: 60000; font-weight: 700; box-shadow: 0 10px 30px rgba(0,0,0,0.6); border: 1px solid rgba(255,255,255,0.1); text-align: center; width: 80%; max-width: 300px; font-size: 0.9rem; }
        select.dark-select { background: rgba(0,0,0,0.3); border: 1px solid rgba(255,255,255,0.1); color: #fff; padding: 14px; border-radius: 12px; outline: none; width: 100%; margin-bottom: 14px; font-family: 'Poppins'; font-size: 0.95rem; }
        select.dark-select option { background: var(--bg-card); color: #fff; }
        .premium-number-box { background: rgba(255,190,11,0.05); border: 1px dashed var(--accent); padding: 20px; border-radius: 16px; margin-bottom: 16px; box-shadow: inset 0 0 20px rgba(255,190,11,0.05); }
        
        .scorecard-table { width: 100%; border-collapse: collapse; margin-bottom: 16px; font-size: 0.85rem; background: rgba(0,0,0,0.2); border-radius: 12px; overflow: hidden; }
        .scorecard-table th { text-align: left; padding: 10px 12px; background: rgba(255,255,255,0.05); color: var(--accent); font-weight: 800; text-transform: uppercase; letter-spacing: 1px; }
        .scorecard-table td { padding: 10px 12px; border-bottom: 1px dashed rgba(255,255,255,0.1); color: #fff; font-weight: 600; }
        .scorecard-table tr:last-child td { border-bottom: none; }
        
        .notification-item { background: rgba(255,255,255,0.05); border-left: 3px solid var(--accent); padding: 12px; border-radius: 10px; margin-bottom: 10px; text-align: left; }

        /* MATCH HISTORY SEARCH & TABS */
        .search-container { position: relative; margin-bottom: 16px; }
        .search-container i { position: absolute; left: 16px; top: 50%; transform: translateY(-50%); color: var(--text-muted); }
        .search-input { width: 100%; background: rgba(0,0,0,0.4); border: 1px solid var(--border-light); padding: 14px 14px 14px 45px; border-radius: 14px; color: #fff; font-size: 0.95rem; outline: none; transition: 0.3s; }
        .search-input:focus { border-color: var(--primary); box-shadow: 0 0 15px rgba(255,42,70,0.2); }

        .match-tabs { display: flex; background: rgba(0,0,0,0.4); border-radius: 14px; padding: 5px; margin-bottom: 20px; border: 1px solid rgba(255,255,255,0.05); }
        .match-tab { flex: 1; text-align: center; padding: 12px; border-radius: 10px; font-weight: 800; font-size: 0.9rem; cursor: pointer; color: var(--text-muted); transition: 0.3s; text-transform: uppercase; letter-spacing: 1px; }
        .match-tab.active { background: var(--primary); color: #fff; box-shadow: 0 4px 15px var(--primary-glow); }
        
        .dream-card { background: var(--bg-card); border-radius: 16px; padding: 0; margin-bottom: 16px; border: 1px solid rgba(255,255,255,0.05); box-shadow: 0 10px 25px rgba(0,0,0,0.4); overflow: hidden; position: relative; }
        .dream-header { background: rgba(0,0,0,0.4); padding: 12px 16px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .dream-header-title { font-weight: 800; font-size: 1rem; color: #fff; display: flex; align-items: center; gap: 8px; }
        .badge-status { background: var(--accent); color: #000; padding: 4px 10px; border-radius: 12px; font-size: 0.7rem; font-weight: 900; text-transform: uppercase; box-shadow: 0 0 10px var(--accent-glow); }
        .badge-finished { background: #10B981; color: #fff; box-shadow: 0 0 10px rgba(16,185,129,0.5); }
        .dream-body { padding: 16px; display: grid; grid-template-columns: 1fr; gap: 10px; }
        .dream-info-row { display: flex; align-items: center; gap: 10px; color: var(--text-muted); font-size: 0.85rem; font-weight: 600; }
        .dream-info-row i { color: var(--primary); width: 16px; text-align: center; }
        .dream-footer { background: rgba(255,42,70,0.05); padding: 12px 16px; border-top: 1px dashed rgba(255,42,70,0.2); font-weight: 800; font-size: 0.9rem; color: #fff; text-align: center; }
        .action-btns-row { display: flex; gap: 10px; margin-top: 12px; }

        /* PROFILE ACHIEVEMENTS */
        .achievement-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 16px; }
        .ach-badge { background: rgba(0,0,0,0.3); border: 1px solid var(--border-light); border-radius: 12px; padding: 10px; text-align: center; }
        .ach-icon { font-size: 1.5rem; color: var(--accent); margin-bottom: 4px; filter: drop-shadow(0 0 5px var(--accent-glow)); }
        .ach-title { font-size: 0.7rem; font-weight: 700; color: #fff; }
        .level-bar-bg { width: 100%; height: 8px; background: rgba(255,255,255,0.1); border-radius: 10px; margin-top: 8px; overflow: hidden; }
        .level-bar-fill { height: 100%; background: var(--gradient-2); width: 0%; box-shadow: 0 0 10px var(--accent-glow); transition: 1s ease-out; }

    </style>
</head>
<body>

<script>
    window.addEventListener('DOMContentLoaded', () => {
        setTimeout(() => {
            const loader = document.getElementById('ultra-loader');
            if(loader) {
                loader.style.opacity = '0';
                setTimeout(() => loader.style.display = 'none', 600);
            }
        }, 1500);
    });
</script>

<audio id="sfx-click" src="https://assets.mixkit.co/active_storage/sfx/2568/2568-preview.mp3" preload="auto"></audio>
<audio id="sfx-cheer" src="https://assets.mixkit.co/active_storage/sfx/2003/2003-preview.mp3" preload="auto"></audio>
<audio id="sfx-horn" src="https://assets.mixkit.co/active_storage/sfx/318/318-preview.mp3" preload="auto"></audio>

<div id="particles-container"></div>

<div id="ultra-loader">
    <div class="loader-logo"><i class="fas fa-bolt"></i></div>
    <div class="loader-text">TIGERS PRIME</div>
    <div class="loader-bar-container"><div class="loader-bar" id="loaderProgress"></div></div>
</div>

<div id="cinematicPopup" class="cinematic-overlay">
    <div id="cinematicParticles" class=""></div>
    <div id="cinematicText" class="cinematic-text">SIX!</div>
</div>

<datalist id="dbPlayersList"></datalist>
<div id="toast-msg" class="toast">Message</div>

<div id="global-loader" style="position:fixed; top:0; left:0; width:100%; height:100%; background:var(--bg-main); z-index:10000; display:none; justify-content:center; align-items:center; flex-direction:column;">
    <i class="fas fa-circle-notch fa-spin fa-3x" style="color:var(--primary); filter:drop-shadow(0 0 10px var(--primary-glow)); margin-bottom:20px;"></i>
    <div style="font-size:1rem; font-weight:800; letter-spacing:2px; color:#fff;">SYNCING</div>
</div>

<div id="authOverlay" class="auth-overlay">
    <div class="auth-container">
        <div class="auth-logo"><i class="fas fa-bolt"></i><h1>TIGERS<br><span style="color:var(--accent);">PRIME</span></h1><p style="color:var(--text-muted); font-weight:600; font-size:0.9rem;">Premium Match Management</p></div>
        <div class="auth-tabs"><div class="auth-tab active" id="tabLogin" onclick="switchAuthTab('login')">Log In</div><div class="auth-tab" id="tabSignup" onclick="switchAuthTab('signup')">Sign Up</div></div>
        <div id="formLogin" class="auth-form active">
            <input type="email" id="loginEmail" class="login-input" placeholder="Email Address">
            <input type="password" id="loginPassword" class="login-input" placeholder="Password">
            <button class="btn-primary ripple-btn" onclick="playSound('click'); handleAuth('login')">Access Account</button>
        </div>
        <div id="formSignup" class="auth-form">
            <div class="image-upload-wrapper"><input type="file" accept="image/*" class="image-upload-input" id="regPhotoInput" onchange="handleImageSelect(event, 'regPreview')"><div class="image-upload-preview"><img id="regPreview" src="https://via.placeholder.com/150/111827/FFFFFF?text=+" alt="Avatar"></div></div>
            <input type="text" id="regName" class="login-input" placeholder="Full Name (e.g. NAYIM)">
            <input type="email" id="regEmail" class="login-input" placeholder="Email Address">
            <input type="password" id="regPassword" class="login-input" placeholder="Create Password (Min 6 chars)">
            <select id="regRole" class="login-input" style="color:#fff; background:rgba(0,0,0,0.3);"><option value="Batsman">Batsman</option><option value="Bowler">Bowler</option><option value="All-rounder">All-rounder</option></select>
            <button class="btn-primary ripple-btn" onclick="playSound('click'); handleAuth('signup')">Create Account</button>
        </div>
    </div>
</div>

<div id="editProfileModal" class="modal">
    <div class="modal-content">
        <h3 style="text-align:center; color:#fff; margin-bottom:20px; font-size: 1.3rem;">Edit Profile</h3>
        <div class="image-upload-wrapper"><input type="file" accept="image/*" class="image-upload-input" id="editPhotoInput" onchange="handleImageSelect(event, 'editPreview')"><div class="image-upload-preview"><img id="editPreview" src="" alt="Avatar"></div></div>
        <input type="text" id="editName" class="login-input" placeholder="Full Name">
        <select id="editRole" class="login-input" style="margin-bottom: 24px;"><option value="Batsman">Batsman</option><option value="Bowler">Bowler</option><option value="All-rounder">All-rounder</option></select>
        <div style="display:flex; gap:12px;"><button class="btn-small" style="flex:1;" onclick="document.getElementById('editProfileModal').classList.remove('active')">Cancel</button><button class="btn-primary ripple-btn" style="flex:1; padding:12px;" onclick="playSound('click'); submitProfileEdit()">Save Profile</button></div>
    </div>
</div>

<div id="supportModal" class="modal">
    <div class="modal-content" style="text-align:center;">
        <i class="fas fa-headset" style="font-size:3rem; color:var(--accent); margin-bottom:16px;"></i><h3 style="color:#fff; margin-bottom:12px; font-size:1.4rem;">Premium Support</h3><p style="color:var(--text-muted); font-size:0.9rem; margin-bottom:24px;">If you face any issues scoring or adding balance, contact our support team.</p>
        <div style="background:rgba(0,0,0,0.3); padding:16px; border-radius:12px; border:1px solid rgba(255,255,255,0.05); margin-bottom:12px;"><div style="color:var(--primary); font-weight:800; font-size:1rem; margin-bottom:4px;"><i class="fab fa-whatsapp"></i> WhatsApp Support</div><div style="color:#fff; font-size:1.2rem; font-weight:700;">+880 1311-768469</div></div>
        <button class="btn-outline ripple-btn" style="margin-top:16px;" onclick="document.getElementById('supportModal').classList.remove('active')">Close</button>
    </div>
</div>

<div id="notificationModal" class="modal">
    <div class="modal-content" style="max-height:80vh;">
        <h3 style="color:#fff; margin-bottom:20px; font-size:1.3rem; text-align:center;"><i class="fas fa-bell" style="color:var(--accent);"></i> Notifications</h3>
        <div id="fullNotificationList" style="overflow-y:auto; max-height:50vh;"><div style="color:var(--text-muted); text-align:center;">No new notifications</div></div>
        <button class="btn-primary ripple-btn" style="margin-top:20px;" onclick="document.getElementById('notificationModal').classList.remove('active')">Close</button>
    </div>
</div>

<div id="matchWizardModal" class="modal">
    <div class="modal-content">
        <h3 style="text-align:center; color:#fff; margin-bottom:20px; font-size: 1.3rem;">Match Setup</h3>
        <div id="wizStep1" class="wizard-step active">
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Host Team</label><input type="text" id="wizTeam1" class="login-input" value="Team Tigers">
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Opponent Team</label><input type="text" id="wizTeam2" class="login-input" placeholder="e.g. Team Avengers">
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Total Overs</label><input type="number" id="wizOvers" class="login-input" value="10">
            
            <label style="font-size:0.8rem; color:var(--accent); font-weight:700; display:block; margin:10px 0 6px;">Ground Name & Media</label>
            <input type="text" id="wizGroundName" class="login-input" placeholder="Ground Name (e.g. Mirpur Stadium)">
            <input type="text" id="wizLiveLink" class="login-input" placeholder="YouTube or FB Live URL">
            
            <div style="display:flex; gap:10px; margin-top:10px;"><button class="btn-small" style="flex:1;" onclick="document.getElementById('matchWizardModal').classList.remove('active')">Cancel</button><button class="btn-primary ripple-btn" style="flex:1; padding:12px;" onclick="playSound('click'); nextWizardStep(2)">Next</button></div>
        </div>
        <div id="wizStep2" class="wizard-step">
            <h4 style="font-size:1rem; margin-bottom:12px; text-align:center; color:#fff;">Add Squads (Min 4)</h4>
            <div style="margin-bottom:12px;"><strong id="labelT1" style="font-size:0.85rem; color:var(--accent); display:block; margin-bottom:6px;">Team 1</strong><div style="display:flex; gap:8px; margin-bottom: 8px;"><input type="text" list="dbPlayersList" id="addP1Input" class="login-input" style="margin:0; padding:12px;" placeholder="Search DB or Add"><button class="btn-primary ripple-btn" style="width:auto; padding:0 16px;" onclick="playSound('click'); addWizardPlayer(1)"><i class="fas fa-plus"></i></button></div><div class="team-player-list" id="listT1"></div></div>
            <div style="margin-bottom:12px;"><strong id="labelT2" style="font-size:0.85rem; color:var(--accent); display:block; margin-bottom:6px;">Team 2</strong><div style="display:flex; gap:8px; margin-bottom: 8px;"><input type="text" list="dbPlayersList" id="addP2Input" class="login-input" style="margin:0; padding:12px;" placeholder="Search DB or Add"><button class="btn-primary ripple-btn" style="width:auto; padding:0 16px;" onclick="playSound('click'); addWizardPlayer(2)"><i class="fas fa-plus"></i></button></div><div class="team-player-list" id="listT2"></div></div>
            <div style="display:flex; gap:10px;"><button class="btn-small" style="flex:1;" onclick="playSound('click'); nextWizardStep(1)">Back</button><button class="btn-primary ripple-btn" style="flex:1; padding:12px;" onclick="playSound('click'); nextWizardStep(3)">Next</button></div>
        </div>
        <div id="wizStep3" class="wizard-step">
            <h4 style="font-size:1rem; margin-bottom:16px; text-align:center; color:#fff;">Toss Details</h4>
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Who won?</label><div class="setup-grid" id="tossWinnerGrid"></div>
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin:12px 0 6px;">Decision:</label><div class="setup-grid" id="tossDecisionGrid"><div class="radio-box active" onclick="selectRadio('tossDecisionGrid', this, 'Bat')">Bat First</div><div class="radio-box" onclick="selectRadio('tossDecisionGrid', this, 'Bowl')">Bowl First</div></div>
            <div style="display:flex; gap:10px; margin-top:16px;"><button class="btn-small" style="flex:1;" onclick="playSound('click'); nextWizardStep(2)">Back</button><button class="btn-primary ripple-btn" style="flex:1; padding:12px;" onclick="playSound('click'); prepareOpenersAndGoToStep4()">Next</button></div>
        </div>
        <div id="wizStep4" class="wizard-step">
            <div style="background: rgba(255,190,11,0.1); border: 1px solid rgba(255,190,11,0.2); padding: 10px; border-radius: 10px; margin-bottom: 16px; text-align: center;"><p id="openerDesc" style="font-size:0.95rem; font-weight:800; color:var(--accent);"></p></div>
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Striker</label><select id="wizStriker" class="dark-select"></select>
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Non-Striker</label><select id="wizNonStriker" class="dark-select"></select>
            <label style="font-size:0.8rem; color:var(--text-muted); font-weight:600; display:block; margin-bottom:6px;">Opening Bowler</label><select id="wizBowler" class="dark-select"></select>
            <div style="display:flex; gap:10px; margin-top:16px;"><button class="btn-small" style="flex:1;" onclick="playSound('click'); nextWizardStep(3)">Back</button><button class="btn-primary ripple-btn" style="flex:1; padding:12px;" onclick="playSound('click'); finalizeAndStartMatch()">Start Match</button></div>
        </div>
    </div>
</div>

<header>
    <div class="header-title"><i class="fas fa-bolt" style="color:var(--accent);"></i> TIGERS <span>PRIME</span></div>
    <div class="header-actions">
        <div class="wallet-badge ripple-btn" onclick="playSound('click'); switchTab('wallet', document.getElementById('navWallet'))"><i class="fas fa-wallet"></i> <span id="headerBalance">0</span> ৳</div>
        <div class="notification-bell" onclick="openNotifications()"><i class="fas fa-bell"></i><span class="notif-badge" id="notifBadge">0</span></div>
    </div>
</header>

<div class="live-ticker">
    <div class="ticker-content" id="mainTickerContent">
        <i class="fas fa-star" style="color:var(--accent); margin:0 8px;"></i> WELCOME TO TIGERS PRIME • ELITE SCORING ENGINE 
        <i class="fas fa-trophy" style="color:var(--accent); margin:0 8px;"></i> NO LIVE MATCH CURRENTLY 
    </div>
</div>

<div id="main-container">

    <div id="home" class="section active">
        <div class="card notice-card">
            <h4 style="margin-bottom:10px; color:#fff; font-size:0.95rem; display:flex; align-items:center; gap:8px;"><i class="fas fa-bullhorn" style="color:var(--accent);"></i> Notice Board</h4>
            <div id="noticeList"><div style="font-size:0.85rem; color:var(--text-muted);">Fetching updates...</div></div>
        </div>

        <div class="card" style="box-shadow: 0 10px 30px rgba(255,42,70,0.15); border: 1px solid rgba(255,42,70,0.2);">
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:16px;">
                <h4 style="color:#fff; font-size:1rem;"><i class="fas fa-satellite-dish" style="color:var(--primary); margin-right:6px; animation: pulseGlow 2s infinite;"></i> LIVE STATUS</h4>
                <div style="display:flex; gap:10px; align-items:center;">
                    <a id="liveWatchBtn" href="#" target="_blank" style="display:none; background:var(--primary); color:#fff; padding:4px 12px; border-radius:20px; font-size:0.75rem; font-weight:800; text-decoration:none; box-shadow: 0 0 10px var(--primary-glow);"><i class="fas fa-play" style="margin-right:4px;"></i> Watch Live</a>
                    <span style="background:rgba(255,255,255,0.1); color:#fff; padding:4px 12px; border-radius:20px; font-size:0.7rem; font-weight:800;" id="liveStatusBadge">OFFLINE</span>
                </div>
            </div>
            <div id="countdownTimer" style="background:rgba(0,0,0,0.4); padding:10px; border-radius:10px; text-align:center; font-size:0.85rem; font-weight:700; margin-bottom:16px; color:var(--text-muted);">No Active Match</div>
            <div style="display:flex; justify-content:space-between; text-align:center; align-items:center;">
                <div style="flex:1;"><div id="liveTeamA" style="font-size:0.9rem; font-weight:800; margin-bottom:4px; color:var(--text-muted);">-</div><div id="liveScoreA" style="font-size:1.8rem; font-weight:900; color:#fff;">0/0</div><div id="liveOversA" style="font-size:0.8rem; color:var(--accent); font-weight:700;"></div></div>
                <div style="font-weight:900; color:rgba(255,255,255,0.15); font-size:1.3rem;">V</div>
                <div style="flex:1;"><div id="liveTeamB" style="font-size:0.9rem; font-weight:800; margin-bottom:4px; color:var(--text-muted);">-</div><div id="liveScoreB" style="font-size:1.8rem; font-weight:900; color:#fff;">0/0</div><div id="liveOversB" style="font-size:0.8rem; color:var(--accent); font-weight:700;"></div></div>
            </div>
        </div>
        
        <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:20px;">
            <div class="card" style="text-align:center; padding:20px 12px; margin-bottom:0;"><h2 id="total-squad" style="font-size:2.2rem; color:var(--accent); line-height:1; margin-bottom:4px; text-shadow: 0 0 15px var(--accent-glow);">0</h2><span style="font-size:0.75rem; font-weight:800; color:var(--text-muted); letter-spacing: 1px;">PLAYERS</span></div>
            <div class="card" style="text-align:center; padding:20px 12px; margin-bottom:0;"><h2 id="total-matches" style="font-size:2.2rem; color:#fff; line-height:1; margin-bottom:4px;">0</h2><span style="font-size:0.75rem; font-weight:800; color:var(--text-muted); letter-spacing: 1px;">MATCHES</span></div>
        </div>
    </div>

    <button class="fab-score ripple-btn" onclick="playSound('click'); openWizardOrScoring()"><i class="fas fa-play"></i> Score Match</button>

    <div id="scoring_panel" class="section" style="padding: 0;">
        <div class="scoreboard-full-wrapper">
            
            <div class="score-top">
                <div class="score-badge-row" style="width: 100%;">
                    <div class="inning-badge" id="matchTargetDisplay">1st Innings</div>
                    <div style="font-size:0.75rem; color:var(--text-muted); font-weight:700;" id="padGroundName"><i class="fas fa-map-marker-alt"></i> Stadium</div>
                    <div class="live-dot"><i class="fas fa-circle"></i> Live</div>
                </div>
                
                <div class="score-advanced-data">
                    <span id="padPartnership">Partnership: 0 (0)</span>
                    <span id="padRRR" style="color:var(--accent);">Target: -</span>
                </div>
                
                <div class="batting-team-title" id="padBattingTeamName">Batting Team</div>
                <div class="main-score flip-animate" id="animatedScore"><span id="padRuns">0</span><span>/<span id="padWickets">0</span></span></div>
                
                <div class="win-prob-container" id="winProbBar" style="display:none;">
                    <div class="win-prob-bar-a" id="wpA"></div>
                    <div class="win-prob-bar-b" id="wpB"></div>
                </div>

                <div class="score-meta">
                    <div class="meta-box"><div class="meta-label">OVERS</div><div class="meta-value"><span id="padOvers">0.0</span><span style="opacity:0.5; font-size:1.1rem;">/<span id="padTotalOvers">10</span></span></div></div>
                    <div class="meta-box"><div class="meta-label">CRR</div><div class="meta-value" id="padCrr">0.00</div></div>
                </div>
            </div>

            <div class="score-bottom">
                <div class="timeline-container">
                    <div class="timeline-label">OVER <span id="currentOverNum">1</span></div>
                    <div style="display:flex; gap:8px;" id="padOverTimeline"><div style="font-size:0.8rem; color:var(--text-muted); font-weight:600;">Start of over...</div></div>
                </div>

                <div class="stats-list">
                    <div class="stat-row">
                        <div class="stat-name">
                            <span class="indicator active" id="indStriker"></span>
                            <div style="width: 100%;">
                                <div style="font-size: 0.65rem; color: var(--accent); font-weight: 800; letter-spacing: 1px; margin-bottom: 2px;">STRIKER (MANUAL SELECT)</div>
                                <select id="padStrikerSel" class="manual-select" onchange="manualChangeStriker(this.value)"></select>
                            </div>
                        </div>
                        <div class="stat-val">
                            <div id="padStrikerStats">0 (0)</div>
                            <div class="stat-sub" id="padStrikerSR">SR: 0.0</div>
                        </div>
                    </div>
                    <div class="stat-row" style="opacity: 0.8;">
                        <div class="stat-name">
                            <span class="indicator" style="background:transparent;"></span>
                            <div style="width: 100%;">
                                <div style="font-size: 0.65rem; color: var(--text-muted); font-weight: 800; letter-spacing: 1px; margin-bottom: 2px;">NON-STRIKER</div>
                                <select id="padNonStrikerSel" class="manual-select" onchange="manualChangeNonStriker(this.value)"></select>
                            </div>
                        </div>
                        <div class="stat-val">
                            <div id="padNonStrikerStats">0 (0)</div>
                            <div class="stat-sub">SR: <span id="padNonStrikerSR">0.0</span></div>
                        </div>
                    </div>
                    <div class="stat-row" style="border-top:1px dashed rgba(255,255,255,0.1); padding-top:12px; margin-top:4px;">
                        <div class="stat-name">
                            <i class="fas fa-baseball" style="color:var(--primary); font-size:1rem; margin-right:8px;"></i>
                            <div style="width: 100%;">
                                <div style="font-size: 0.65rem; color: var(--primary); font-weight: 800; letter-spacing: 1px; margin-bottom: 2px;">BOWLER (MANUAL SELECT)</div>
                                <select id="padBowlerSel" class="manual-select" onchange="manualChangeBowler(this.value)"></select>
                            </div>
                        </div>
                        <div class="stat-val">
                            <div id="padBowlerStats">0.0-0-0</div>
                            <div class="stat-sub" id="padBowlerEcon">Econ: 0.00</div>
                        </div>
                    </div>
                </div>

                <div class="keypad">
                    <div class="key-btn extra ripple-btn" onclick="playSound('click'); openDynamicRunPrompt('wd')">WD</div>
                    <div class="key-btn extra ripple-btn" onclick="playSound('click'); openDynamicRunPrompt('nb')">NB</div>
                    <div class="key-btn extra ripple-btn" onclick="playSound('click'); openDynamicRunPrompt('bye')">B</div>
                    <div class="key-btn extra ripple-btn" onclick="playSound('click'); openDynamicRunPrompt('lb')">LB</div>
                    
                    <div class="key-btn ripple-btn" onclick="playSound('click'); triggerScoreAnimation(); execBall(0)">0</div>
                    <div class="key-btn ripple-btn" onclick="playSound('click'); triggerScoreAnimation(); execBall(1)">1</div>
                    <div class="key-btn ripple-btn" onclick="playSound('click'); triggerScoreAnimation(); execBall(2)">2</div>
                    <div class="key-btn ripple-btn" onclick="playSound('click'); triggerScoreAnimation(); execBall(3)">3</div>
                    
                    <div class="key-btn four ripple-btn" onclick="playSound('cheer'); triggerCinematic('FOUR!', 'event-four'); execBall(4)">4</div>
                    <div class="key-btn ripple-btn" onclick="playSound('click'); triggerScoreAnimation(); execBall(5)">5</div>
                    <div class="key-btn six ripple-btn" onclick="playSound('cheer'); triggerCinematic('SIX!', 'event-six'); execBall(6)">6</div>
                    <div class="key-btn undo ripple-btn" onclick="playSound('click'); undoScore()"><i class="fas fa-undo"></i></div>
                    
                    <div class="key-btn out ripple-btn" onclick="playSound('horn'); triggerCinematic('OUT!', 'event-out'); openDynamicRunPrompt('out')">OUT</div>
                </div>

                <div style="display:flex; gap:10px; margin-bottom:10px;">
                    <button class="btn-outline ripple-btn" style="flex:1; border-color:var(--text-muted); color:var(--text-muted); padding:12px;" onclick="playSound('click'); pauseMatch()">Save & Pause</button>
                    <button class="btn-outline ripple-btn" style="flex:1; padding:12px;" id="btnNextInnings" onclick="playSound('click'); changeInnings()">End Innings</button>
                    <button class="btn-primary ripple-btn" style="flex:1; display:none; padding:12px;" id="btnEndMatch" onclick="playSound('click'); finishMatch()">Finish Match & Save</button>
                </div>
            </div>
        </div>
    </div>

    <div id="matches" class="section">
        <h4 style="margin-bottom:16px; color:#fff; font-size:1.1rem;"><i class="fas fa-trophy" style="color:var(--accent); margin-right:8px;"></i> MATCH CENTER</h4>
        
        <div class="search-container">
            <i class="fas fa-search"></i>
            <input type="text" id="matchSearch" class="search-input" placeholder="Search team, ground, or date..." onkeyup="filterMatches()">
        </div>

        <div class="match-tabs">
            <div class="match-tab active" id="tabHomeMatches" onclick="playSound('click'); switchMatchSubTab('home')">Home Matches</div>
            <div class="match-tab" id="tabAwayMatches" onclick="playSound('click'); switchMatchSubTab('away')">Away Matches</div>
        </div>

        <div id="homeMatchesContainer"><div style="color:var(--text-muted); font-size:0.9rem; text-align: center;">Syncing fixtures...</div></div>
        <div id="awayMatchesContainer" style="display:none;"><div style="color:var(--text-muted); font-size:0.9rem; text-align: center; padding: 20px;">No away fixtures scheduled.</div></div>
    </div>
    
    <div id="players" class="section">
        <h4 style="margin-bottom:16px; color:#fff; font-size:1.1rem;"><i class="fas fa-users" style="color:var(--accent); margin-right:8px;"></i> SQUAD DIRECTORY</h4>
        <div id="player-list"><div style="color:var(--text-muted); font-size:0.9rem;">Syncing roster...</div></div>
    </div>

    <div id="wallet" class="section">
        <div class="card text-center" style="padding:24px 20px;">
            <h3 style="margin-bottom:16px; color:var(--primary); font-weight:800; font-size:1.3rem;"><i class="fas fa-plus-circle"></i> Add Balance</h3>
            <select id="addMoneyMethod" class="login-input" style="background:rgba(0,0,0,0.3); padding:14px;" onchange="toggleAddMoneyNum()">
                <option value="">-- Select Payment Method --</option><option value="bKash">bKash</option><option value="Nagad">Nagad</option>
            </select>
            <div id="addMoneyInst" class="premium-number-box" style="display:none;">
                <div style="font-size: 0.8rem; color: var(--text-muted); margin-bottom: 4px; text-transform:uppercase; font-weight:700;">Official Agent Number</div>
                <div style="font-size: 1.8rem; font-weight: 900; color: #fff; letter-spacing: 2px;">01311768469</div>
                <div style="font-size: 0.8rem; color: var(--accent); margin-top: 6px; font-weight:600;"><i class="fas fa-info-circle"></i> Send Money via bKash/Nagad</div>
            </div>
            <input type="number" id="addMoneyAmount" class="login-input" placeholder="Amount (৳)" min="50">
            <input type="text" id="addMoneyTrx" class="login-input" placeholder="Transaction ID (TrxID)">
            <button class="btn-outline ripple-btn" style="border-color:var(--primary); color:var(--primary);" onclick="playSound('click'); processAddMoney()">Verify & Add to Wallet</button>
        </div>

        <div class="card text-center" style="padding:24px 20px;">
            <h3 style="margin-bottom:16px; color:var(--accent); font-weight:800; font-size:1.3rem;"><i class="fas fa-hand-holding-usd"></i> Team Fund</h3>
            <p style="color:var(--text-muted); font-size:0.85rem; margin-bottom:16px;">Donate from your wallet balance.</p>
            <div style="background:rgba(0,0,0,0.4); padding:16px; border-radius:12px; margin-bottom:16px; border:1px solid rgba(255,255,255,0.05);">
                <span style="font-size:0.9rem; color:var(--text-muted); font-weight:600;">Available Balance: </span>
                <span style="font-weight:800; color:var(--accent); font-size:1.2rem;"><span id="fundWalletBal">0</span> ৳</span>
            </div>
            <input type="number" id="donateAmount" class="login-input" placeholder="Donation Amount (৳)" min="10">
            <input type="text" id="donateReason" class="login-input" placeholder="Reason for donation (Mandatory)">
            <button class="btn-primary ripple-btn" onclick="playSound('click'); processDonation()">Donate Now</button>
        </div>
    </div>

    <div id="profile" class="section">
        <div class="card" style="text-align:center; padding: 30px 20px;">
            <div style="width:90px; height:90px; background:rgba(255,190,11,0.1); border:1px solid rgba(255,190,11,0.3); border-radius:50%; margin:0 auto 16px; display:flex; align-items:center; justify-content:center; font-size:2.2rem; font-weight:800; color:var(--accent); box-shadow:0 0 20px var(--accent-glow); overflow:hidden;" id="myAvatar">
                <img src="" id="myAvatarImg" style="display:none; width:100%; height:100%; object-fit:cover;">
                <span id="myAvatarText">-</span>
            </div>
            <h2 id="myName" style="margin-bottom:4px; font-size:1.5rem;">_</h2>
            <div style="font-size:0.9rem; font-weight:600; color:var(--text-muted); margin-bottom:8px;" id="myRole">_</div>
            <div style="font-size:0.85rem; font-weight:800; color:var(--accent); margin-bottom:10px; background:rgba(255,190,11,0.1); padding:4px 12px; border-radius:10px; display:inline-block;" id="myCode">ID: -</div>
            
            <div style="margin-bottom: 20px; text-align: left; padding: 0 10px;">
                <div style="display:flex; justify-content:space-between; font-size:0.75rem; font-weight:700; color:var(--text-muted);"><span>LEVEL <span id="myLevelText">1</span></span><span>Next Level</span></div>
                <div class="level-bar-bg"><div class="level-bar-fill" id="myLevelProgress"></div></div>
            </div>

            <div style="display:flex; justify-content:center; gap:10px; flex-wrap:wrap;">
                <button class="btn-small ripple-btn" onclick="playSound('click'); openEditProfile()" style="padding:10px 20px;"><i class="fas fa-pen"></i> Edit</button>
                <button class="btn-small ripple-btn" onclick="playSound('click'); document.getElementById('supportModal').classList.add('active')" style="padding:10px 20px; background:rgba(59,130,246,0.1); color:var(--info); border-color:rgba(59,130,246,0.3);"><i class="fas fa-headset"></i> Support</button>
                <button class="btn-small ripple-btn" onclick="playSound('click'); performLogout()" style="padding:10px 20px; background:rgba(255,42,70,0.1); color:var(--primary); border-color:rgba(255,42,70,0.3);"><i class="fas fa-sign-out-alt"></i> Logout</button>
            </div>
            
            <div class="achievement-grid">
                <div class="ach-badge"><div class="ach-icon"><i class="fas fa-star"></i></div><div class="ach-title" id="achMatches">0 Matches</div></div>
                <div class="ach-badge"><div class="ach-icon"><i class="fas fa-fire"></i></div><div class="ach-title" id="achRuns">0 Runs</div></div>
                <div class="ach-badge"><div class="ach-icon"><i class="fas fa-bowling-ball"></i></div><div class="ach-title" id="achWickets">0 Wkts</div></div>
            </div>
        </div>
        
        <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px;">
            <div class="card" style="text-align:center; margin:0; padding:20px 10px;"><div style="font-size:0.75rem; color:var(--text-muted); font-weight:700;">CAREER RUNS</div><div id="myRuns" style="font-size:1.6rem; font-weight:800; color:#fff; margin-top:4px;">0</div></div>
            <div class="card" style="text-align:center; margin:0; padding:20px 10px;"><div style="font-size:0.75rem; color:var(--text-muted); font-weight:700;">WICKETS</div><div id="myWickets" style="font-size:1.6rem; font-weight:800; color:var(--accent); margin-top:4px;">0</div></div>
            <div class="card" style="text-align:center; margin:0; padding:16px 10px; grid-column:span 2;">
                <div style="font-size:0.8rem; color:var(--text-muted); font-weight:700; margin-bottom:6px;">ADVANCED STATS</div>
                <div style="display:flex; justify-content:space-around;">
                    <div><div style="font-size:0.75rem; color:var(--primary);">Highest Score</div><div style="font-size:1.1rem; font-weight:800; color:#fff;" id="myHS">0 (0)</div></div>
                    <div><div style="font-size:0.75rem; color:var(--accent);">Best Bowling</div><div style="font-size:1.1rem; font-weight:800; color:#fff;" id="myBB">0 W / 0 R</div></div>
                </div>
            </div>
        </div>
    </div>
</div>

<nav class="nav-bar">
    <div class="nav-item active" onclick="playSound('click'); switchTab('home', this)"><i class="fas fa-home"></i></div>
    <div class="nav-item" onclick="playSound('click'); switchTab('matches', this)"><i class="fas fa-chart-bar"></i></div>
    <div class="nav-item" onclick="playSound('click'); switchTab('players', this)"><i class="fas fa-users"></i></div>
    <div class="nav-item" id="navWallet" onclick="playSound('click'); switchTab('wallet', this)"><i class="fas fa-wallet"></i></div>
    <div class="nav-item" onclick="playSound('click'); switchTab('profile', this)"><i class="fas fa-user-astronaut"></i></div>
</nav>

<div id="dynamicRunModal" class="modal">
    <div class="modal-content" style="text-align:center; max-width:320px;">
        <h3 style="color:#fff; margin-bottom:16px; font-size:1.2rem;" id="runPromptTitle">Runs Taken?</h3>
        <div style="display:grid; grid-template-columns:repeat(3, 1fr); gap:10px; margin-bottom:16px;">
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(0)">0</button>
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(1)">1</button>
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(2)">2</button>
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(3)">3</button>
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(4)">4</button>
            <button class="btn-small ripple-btn" style="padding:14px; font-size:1.1rem; font-weight:800; background:rgba(255,255,255,0.1);" onclick="playSound('click'); submitDynamicRun(6)">6</button>
        </div>
        <button class="btn-outline ripple-btn" style="border:none; color:var(--text-muted); font-size:0.9rem;" onclick="playSound('click'); document.getElementById('dynamicRunModal').classList.remove('active')">Cancel Input</button>
    </div>
</div>

<div id="matchDetailsModal" class="modal">
    <div class="modal-content" style="max-width:460px;">
        <h3 id="mdTitle" style="text-align:center; color:var(--primary); margin-bottom:16px; font-size:1.3rem; font-weight:800; text-transform:uppercase;">Match Scorecard</h3>
        <div id="mdContent" style="color:#fff; font-size:0.9rem;"></div>
        <div class="action-btns-row" style="display:flex; gap:10px; margin-top:20px;">
            <button class="btn-outline ripple-btn" style="flex:1;" onclick="playSound('click'); shareMatchResult()"><i class="fas fa-share-alt"></i> Share</button>
            <button class="btn-primary ripple-btn" style="flex:1;" onclick="playSound('click'); document.getElementById('matchDetailsModal').classList.remove('active')">Close</button>
        </div>
    </div>
</div>

<div id="playerDetailModal" class="modal">
    <div class="modal-content" style="text-align:center;">
        <div style="width:75px; height:75px; background:rgba(255,42,70,0.1); border:1px solid rgba(255,42,70,0.3); border-radius:50%; margin:0 auto 12px; display:flex; align-items:center; justify-content:center; font-size:2rem; font-weight:800; color:var(--primary); box-shadow:0 0 15px var(--primary-glow); overflow:hidden;" id="pdAvatar">-</div>
        <h2 id="pdName" style="font-size: 1.4rem; margin-bottom: 4px; color:#fff;">-</h2>
        <div style="font-size:0.85rem; font-weight:800; color:var(--accent); margin-bottom:6px; background:rgba(255,190,11,0.1); padding:2px 10px; border-radius:8px; display:inline-block;" id="pdCode">ID: -</div>
        <p id="pdRole" style="color:var(--text-muted); font-size:0.85rem; font-weight:600; margin-bottom:20px;">-</p>
        
        <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:20px;">
            <div style="background:rgba(0,0,0,0.3); border: 1px solid var(--border-light); padding:14px; border-radius:14px;">
                <div style="font-size:0.75rem; color:var(--text-muted); font-weight:700;">TOTAL RUNS</div>
                <div id="pdRuns1" style="font-size:1.4rem; font-weight:800; color:#fff; margin-top:4px;">0</div>
                <div style="font-size:0.7rem; color:var(--primary); font-weight:700; margin-top:4px;">High: <span id="pdHS1">0 (0)</span></div>
            </div>
            <div style="background:rgba(0,0,0,0.3); border: 1px solid var(--border-light); padding:14px; border-radius:14px;">
                <div style="font-size:0.75rem; color:var(--text-muted); font-weight:700;">WICKETS</div>
                <div id="pdWickets1" style="font-size:1.4rem; font-weight:800; color:var(--accent); margin-top:4px;">0</div>
                <div style="font-size:0.7rem; color:var(--accent); font-weight:700; margin-top:4px;">Best: <span id="pdBB1">0W / 0R</span></div>
            </div>
        </div>
        <button class="btn-outline ripple-btn" style="padding:12px;" onclick="playSound('click'); document.getElementById('playerDetailModal').classList.remove('active')">Close Profile</button>
    </div>
</div>

<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-app.js";
    import { getDatabase, ref, onValue, update, set, get, push } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-database.js";
    import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/9.23.0/firebase-auth.js";

    const firebaseConfig = { apiKey: "AIzaSyDmWfhjjHlWpUmCDDgW8NPsqSIhiixtlWg", authDomain: "tiger-s-prime.firebaseapp.com", databaseURL: "https://tiger-s-prime-default-rtdb.firebaseio.com", projectId: "tiger-s-prime", storageBucket: "tiger-s-prime.firebasestorage.app", messagingSenderId: "872358241180", appId: "1:872358241180:web:5801568845ac8749769e59" };
    const app = initializeApp(firebaseConfig); const database = getDatabase(app); const auth = getAuth(app);

    let allPlayers = [], allMatches = [], currentUserData = null, isLoginMode = true;

    window.playSound = (type) => {
        try {
            let el = document.getElementById(`sfx-${type}`);
            if(el) { el.currentTime = 0; el.play().catch(e=>console.log("Audio play blocked by browser")); }
        } catch(e) {}
    };

    window.showToast = (msg) => { const toast = document.getElementById('toast-msg'); toast.innerText = msg; toast.style.display = 'block'; setTimeout(() => toast.style.display='none', 3000); };
    
    function showLoader(show) { document.getElementById('global-loader').style.display = show ? 'flex' : 'none'; }
    function hideUltraLoader() { const loader = document.getElementById('ultra-loader'); if(loader) { loader.style.opacity = '0'; setTimeout(() => loader.style.display = 'none', 500); } }

    window.switchMatchSubTab = (tab) => {
        document.getElementById('tabHomeMatches').classList.toggle('active', tab==='home');
        document.getElementById('tabAwayMatches').classList.toggle('active', tab==='away');
        document.getElementById('homeMatchesContainer').style.display = tab==='home' ? 'block' : 'none';
        document.getElementById('awayMatchesContainer').style.display = tab==='away' ? 'block' : 'none';
    };

    window.switchTab = (tabId, btn) => {
        document.querySelectorAll('.section').forEach(s => s.classList.remove('active')); document.getElementById(tabId).classList.add('active');
        if(btn) { document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active')); btn.classList.add('active'); }
        if(tabId === 'profile' || tabId === 'wallet') loadMyProfile();
        document.querySelector('.fab-score').style.display = (tabId === 'home' || tabId === 'matches') ? 'flex' : 'none';
    };
    
    window.selectRadio = (gridId, el, val) => { document.querySelectorAll(`#${gridId} .radio-box`).forEach(b => b.classList.remove('active')); el.classList.add('active'); el.dataset.val = val; };

    window.handleImageSelect = (event, previewId) => {
        const file = event.target.files[0]; if(!file) return;
        const reader = new FileReader();
        reader.onload = (e) => {
            const img = new Image();
            img.onload = () => {
                const canvas = document.createElement('canvas'); const MAX_WIDTH = 250; const scaleSize = MAX_WIDTH / img.width;
                canvas.width = MAX_WIDTH; canvas.height = img.height * scaleSize;
                const ctx = canvas.getContext('2d'); ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                const dataUrl = canvas.toDataURL('image/jpeg', 0.85);
                const preview = document.getElementById(previewId);
                preview.src = dataUrl; preview.style.display = 'block'; preview.dataset.base64 = dataUrl;
            }
            img.src = e.target.result;
        }
        reader.readAsDataURL(file);
    };

    window.switchAuthTab = (mode) => {
        isLoginMode = mode === 'login';
        document.getElementById('tabLogin').classList.toggle('active', isLoginMode);
        document.getElementById('tabSignup').classList.toggle('active', !isLoginMode);
        document.getElementById('formLogin').classList.toggle('active', isLoginMode);
        document.getElementById('formSignup').classList.toggle('active', !isLoginMode);
    };

    // --- 100% FIXED AUTO LOGIN & SIGNUP SYNC ---
    onAuthStateChanged(auth, async (user) => {
        if (user) {
            document.getElementById('authOverlay').style.display = 'none'; 
            try {
                const snap = await get(ref(database, `players/${user.uid}`));
                if (snap.exists()) { 
                    currentUserData = snap.val(); 
                    if(!currentUserData.code || currentUserData.code === "N/A" || currentUserData.code === "NEW") {
                        let newCode = "TP-" + Math.floor(1000 + Math.random() * 9000);
                        await update(ref(database, `players/${user.uid}`), { code: newCode });
                        currentUserData.code = newCode;
                    }
                    setupRealtimeListeners(); 
                    loadMyProfile(); 
                }
            } catch(err) { console.log(err); }
            hideUltraLoader();
            showLoader(false);
        } else { 
            hideUltraLoader();
            showLoader(false);
            document.getElementById('authOverlay').style.display = 'flex'; 
        }
    });

    window.handleAuth = async (type) => {
        showLoader(true);
        try { 
            if(type === 'login') {
                const email = document.getElementById('loginEmail').value.trim(); 
                const pass = document.getElementById('loginPassword').value;
                if(!email || !pass) throw new Error("Please enter Email & Password");
                await signInWithEmailAndPassword(auth, email, pass); 
                // Auto login handle korbe
            } else {
                const name = document.getElementById('regName').value.trim(); 
                const email = document.getElementById('regEmail').value.trim(); 
                const pass = document.getElementById('regPassword').value; 
                const role = document.getElementById('regRole').value;
                const photoStr = document.getElementById('regPreview').dataset.base64 || '';
                
                if(!name || pass.length < 6) throw new Error("Invalid name or short password");
                
                const cred = await createUserWithEmailAndPassword(auth, email, pass);
                const uCode = "TP-" + Math.floor(1000 + Math.random() * 9000);
                const pData = { id: cred.user.uid, code: uCode, email: cred.user.email, name, role, photoUrl: photoStr, matches: 0, runs: 0, wickets: 0, balance: 0, highestScore: 0, hsBalls: 0, bestBowling: {w:0, r:0, b:0} };
                
                await set(ref(database, `players/${cred.user.uid}`), pData);
                
                currentUserData = pData;
                setupRealtimeListeners();
                loadMyProfile();
                document.getElementById('authOverlay').style.display = 'none';
                showLoader(false);
            }
        } catch (error) { 
            showToast(error.message); 
            showLoader(false); 
        }
    };

    window.performLogout = () => { signOut(auth).then(() => window.location.reload()); };

    window.openEditProfile = () => {
        if(!currentUserData) return;
        document.getElementById('editName').value = currentUserData.name || ''; document.getElementById('editRole').value = currentUserData.role || 'Batsman';
        if(currentUserData.photoUrl) { const img = document.getElementById('editPreview'); img.src = currentUserData.photoUrl; img.style.display = 'block'; img.dataset.base64 = currentUserData.photoUrl; }
        document.getElementById('editProfileModal').classList.add('active');
    };
    
    window.submitProfileEdit = async () => {
        if(!currentUserData) return;
        const newName = document.getElementById('editName').value.trim(); const newRole = document.getElementById('editRole').value; const newPhoto = document.getElementById('editPreview').dataset.base64 || currentUserData.photoUrl;
        if(!newName) return showToast("Name required"); showLoader(true);
        await update(ref(database, `players/${currentUserData.id}`), { name: newName, role: newRole, photoUrl: newPhoto });
        currentUserData.name = newName; currentUserData.role = newRole; currentUserData.photoUrl = newPhoto;
        document.getElementById('editProfileModal').classList.remove('active'); loadMyProfile(); showLoader(false); showToast("Profile Updated!");
    };

    function loadMyProfile() {
        if(!currentUserData) return;
        document.getElementById('myName').innerText = currentUserData.name; document.getElementById('myRole').innerText = (currentUserData.role||'').toUpperCase();
        document.getElementById('myCode').innerText = "ID: " + (currentUserData.code || "N/A");
        
        let runs = currentUserData.runs || 0; let wickets = currentUserData.wickets || 0; let matches = currentUserData.matches || 0;
        document.getElementById('myRuns').innerText = runs; document.getElementById('myWickets').innerText = wickets;
        document.getElementById('myHS').innerText = `${currentUserData.highestScore||0} (${currentUserData.hsBalls||0})`;
        
        let bb = currentUserData.bestBowling;
        document.getElementById('myBB').innerText = bb && bb.w>0 ? `${bb.w} W / ${bb.r} R` : `0 W / 0 R`;
        
        let bal = currentUserData.balance || 0;
        document.getElementById('headerBalance').innerText = bal; document.getElementById('fundWalletBal').innerText = bal;

        const img = document.getElementById('myAvatarImg'); const txt = document.getElementById('myAvatarText');
        if(currentUserData.photoUrl) { img.src = currentUserData.photoUrl; img.style.display = 'block'; txt.style.display = 'none'; document.getElementById('myAvatar').style.background = 'transparent'; document.getElementById('myAvatar').style.border = 'none'; } 
        else { img.style.display = 'none'; txt.style.display = 'block'; txt.innerText = currentUserData.name.charAt(0).toUpperCase(); }

        let totalPts = runs + (wickets * 15);
        let level = Math.floor(totalPts / 500) + 1;
        let progress = (totalPts % 500) / 5;
        document.getElementById('myLevelText').innerText = level;
        document.getElementById('myLevelProgress').style.width = progress + '%';
        
        document.getElementById('achMatches').innerText = `${matches} Matches`;
        document.getElementById('achRuns').innerText = `${runs} Runs`;
        document.getElementById('achWickets').innerText = `${wickets} Wkts`;
    }

    window.toggleAddMoneyNum = () => { const m = document.getElementById('addMoneyMethod').value; document.getElementById('addMoneyInst').style.display = m ? 'block' : 'none'; };
    window.processAddMoney = async () => {
        const method = document.getElementById('addMoneyMethod').value; const amount = parseInt(document.getElementById('addMoneyAmount').value); const trx = document.getElementById('addMoneyTrx').value.trim();
        if(!method || !amount || !trx) return showToast("Fill all fields");
        showLoader(true);
        const trxRef = ref(database, `usedTrx/${trx}`); const trxSnap = await get(trxRef);
        if(trxSnap.exists()) { showLoader(false); return showToast("TrxID already used!"); }
        if(trx.length >= 6) {
            await set(trxRef, { uid: currentUserData.id, amount, date: Date.now() });
            const newBal = (currentUserData.balance || 0) + amount;
            await update(ref(database, `players/${currentUserData.id}`), { balance: newBal });
            currentUserData.balance = newBal; loadMyProfile();
            document.getElementById('addMoneyAmount').value = ''; document.getElementById('addMoneyTrx').value = ''; showToast("Balance Added!");
        } else { showToast("Invalid TrxID format!"); }
        showLoader(false);
    };

    window.processDonation = async () => {
        const amount = parseInt(document.getElementById('donateAmount').value); const reason = document.getElementById('donateReason').value.trim();
        if(!amount || !reason) return showToast("Fill all fields. Reason is mandatory.");
        if(amount > (currentUserData.balance || 0)) return showToast("Insufficient Balance!");
        showLoader(true);
        const newBal = currentUserData.balance - amount;
        await update(ref(database, `players/${currentUserData.id}`), { balance: newBal });
        await push(ref(database, `donations`), { uid: currentUserData.id, name: currentUserData.name, amount, reason, date: new Date().toLocaleDateString() });
        currentUserData.balance = newBal; loadMyProfile();
        document.getElementById('donateAmount').value = ''; document.getElementById('donateReason').value = '';
        showToast("Donation Successful!"); showLoader(false);
    };

    window.openNotifications = () => {
        document.getElementById('notificationModal').classList.add('active');
        document.getElementById('notifBadge').style.display = 'none';
        localStorage.setItem('lastSeenNotice', Date.now());
    };

    let wizData = { t1Name:"", t2Name:"", t1Players:[], t2Players:[], overs:10, liveLink:"", ground:"" };
    let matchEngine = { isActive: false, matchId: "", innings: 1, target: null, batTeam: "", bowlTeam: "", runs: 0, wickets: 0, balls: 0, strikerIdx: -1, nonStrikerIdx: -1, bowlerIdx: -1, battingLineup: [], bowlingLineup: [], history: [], currentOverBalls: [], pShipRuns: 0, pShipBalls: 0 };

    window.openWizardOrScoring = () => { if(matchEngine.isActive) { switchTab('scoring_panel'); } else { document.getElementById('matchWizardModal').classList.add('active'); } };
    window.nextWizardStep = (step) => {
        if(step===2) { 
            wizData.t1Name=document.getElementById('wizTeam1').value||"Team Tigers"; 
            wizData.t2Name=document.getElementById('wizTeam2').value||"Team Avengers"; 
            wizData.overs=parseInt(document.getElementById('wizOvers').value)||10; 
            wizData.ground=document.getElementById('wizGroundName').value||"Unknown Stadium"; 
            wizData.liveLink=document.getElementById('wizLiveLink').value.trim();
            document.getElementById('labelT1').innerText=wizData.t1Name; document.getElementById('labelT2').innerText=wizData.t2Name; 
        }
        if(step===3) { if(wizData.t1Players.length<4 || wizData.t2Players.length<4) return showToast("Min 4 players per team required!"); document.getElementById('tossWinnerGrid').innerHTML=`<div class="radio-box active" onclick="selectRadio('tossWinnerGrid', this, 'T1')">${wizData.t1Name}</div><div class="radio-box" onclick="selectRadio('tossWinnerGrid', this, 'T2')">${wizData.t2Name}</div>`; document.querySelector('#tossWinnerGrid .active').dataset.val = 'T1'; }
        document.querySelectorAll('.wizard-step').forEach(s => s.classList.remove('active')); document.getElementById(`wizStep${step}`).classList.add('active');
    };

    window.addWizardPlayer = (teamNum) => {
        const ip = document.getElementById(`addP${teamNum}Input`); const name = ip.value.trim(); if(!name) return;
        const existingDBPlayer = allPlayers.find(p => p.name.toLowerCase() === name.toLowerCase());
        const codeText = existingDBPlayer ? existingDBPlayer.code : "NEW";
        const playerObj = { id: existingDBPlayer ? existingDBPlayer.id : null, code: codeText, name: existingDBPlayer ? existingDBPlayer.name : name, photoUrl: existingDBPlayer ? existingDBPlayer.photoUrl : null, batRuns:0, batBalls:0, bowlRuns:0, bowlBalls:0, wickets:0, out:false };
        if(teamNum===1) wizData.t1Players.push(playerObj); else wizData.t2Players.push(playerObj);
        ip.value = ""; 
        document.getElementById(`listT${teamNum}`).innerHTML = wizData[`t${teamNum}Players`].map(p=>{ return `<span class="added-player-tag" ${p.id?'style="border:1px solid var(--accent); color:var(--accent);"':''}><i class="fas ${p.id?'fa-check-circle':'fa-user'}"></i> ${p.name} <small style="opacity:0.6;margin-left:4px;">[${p.id?'OLD':'NEW'}]</small></span>`; }).join('');
    };

    window.prepareOpenersAndGoToStep4 = () => {
        let win = document.querySelector('#tossWinnerGrid .active').dataset.val==='T1'?wizData.t1Name:wizData.t2Name; let dec = document.querySelector('#tossDecisionGrid .active').dataset.val;
        if ((win===wizData.t1Name && dec==='Bat')||(win===wizData.t2Name && dec==='Bowl')){ matchEngine.batTeam=wizData.t1Name; matchEngine.bowlTeam=wizData.t2Name; matchEngine.battingLineup=JSON.parse(JSON.stringify(wizData.t1Players)); matchEngine.bowlingLineup=JSON.parse(JSON.stringify(wizData.t2Players)); }
        else { matchEngine.batTeam=wizData.t2Name; matchEngine.bowlTeam=wizData.t1Name; matchEngine.battingLineup=JSON.parse(JSON.stringify(wizData.t2Players)); matchEngine.bowlingLineup=JSON.parse(JSON.stringify(wizData.t1Players)); }
        document.getElementById('openerDesc').innerText=`${matchEngine.batTeam} is Batting First`;
        let bOpts = matchEngine.battingLineup.map((p,i)=>`<option value="${i}">${p.name}</option>`).join(''); let blOpts = matchEngine.bowlingLineup.map((p,i)=>`<option value="${i}">${p.name}</option>`).join('');
        document.getElementById('wizStriker').innerHTML=bOpts; document.getElementById('wizNonStriker').innerHTML=bOpts; document.getElementById('wizNonStriker').selectedIndex=1; document.getElementById('wizBowler').innerHTML=blOpts;
        nextWizardStep(4);
    };

    window.finalizeAndStartMatch = () => {
        const s = parseInt(document.getElementById('wizStriker').value); const ns = parseInt(document.getElementById('wizNonStriker').value);
        if(s===ns) return showToast("Striker & Non-Striker must differ");
        matchEngine.strikerIdx=s; matchEngine.nonStrikerIdx=ns; matchEngine.bowlerIdx=parseInt(document.getElementById('wizBowler').value);
        matchEngine.isActive=true; matchEngine.matchId = `M_${Date.now()}`; matchEngine.innings=1; matchEngine.target=null; matchEngine.runs=0; matchEngine.wickets=0; matchEngine.balls=0; matchEngine.history=[]; matchEngine.currentOverBalls=[]; matchEngine.pShipRuns=0; matchEngine.pShipBalls=0;
        wizData.t1FinalScore = ''; wizData.t1FinalOvers = '';
        document.getElementById('matchWizardModal').classList.remove('active'); switchTab('scoring_panel'); updateScoringUI();
    };

    window.pauseMatch = async () => {
        if(!matchEngine.isActive) return;
        showLoader(true);
        let mData = { id: matchEngine.matchId, date: new Date().toLocaleDateString(), teamA: wizData.t1Name, teamB: wizData.t2Name, scoreA: `${matchEngine.runs}/${matchEngine.wickets}`, scoreB: matchEngine.innings===2 ? `${matchEngine.runs}/${matchEngine.wickets}` : '0/0', result: 'Match Paused', status: "Paused", engineState: JSON.stringify(matchEngine), wizState: JSON.stringify(wizData), timestamp: Date.now() };
        await set(ref(database, `matches/${mData.id}`), mData);
        await update(ref(database, 'liveScore'), { active: false });
        matchEngine.isActive = false; showLoader(false); switchTab('matches', document.querySelectorAll('.nav-item')[1]); showToast("Match Saved & Paused!");
    };

    window.resumeMatch = (id) => {
        let m = allMatches.find(x => x.id === id);
        if(!m || !m.engineState) return showToast("Cannot load match data.");
        matchEngine = JSON.parse(m.engineState); wizData = JSON.parse(m.wizState);
        matchEngine.isActive = true; switchTab('scoring_panel'); updateScoringUI(); showToast("Match Resumed!");
    };

    function saveState() { matchEngine.history.push(JSON.stringify(matchEngine)); }
    window.undoScore = () => { if(matchEngine.history.length>0){ matchEngine=JSON.parse(matchEngine.history.pop()); updateScoringUI(); showToast("Reverted"); } };
    
    window.execBall = (runs) => {
        if(!matchEngine.isActive) return; 
        
        if(matchEngine.strikerIdx === -1 || matchEngine.nonStrikerIdx === -1) return showToast("Please Select Batsman Manually!");
        if(matchEngine.bowlerIdx === -1) return showToast("Please Select Bowler Manually!");

        saveState(); matchEngine.runs+=runs; matchEngine.balls++;
        matchEngine.pShipRuns+=runs; matchEngine.pShipBalls++;
        let st = matchEngine.battingLineup[matchEngine.strikerIdx]; let bl = matchEngine.bowlingLineup[matchEngine.bowlerIdx];
        st.batRuns+=runs; st.batBalls++; bl.bowlRuns+=runs; bl.bowlBalls++;
        matchEngine.currentOverBalls.push({ type: 'run', val: runs });
        if(runs%2!==0) swapStrike();
        checkOverOrInningsEnd(); updateScoringUI();
    };

    let pendingActionType = null;
    window.openDynamicRunPrompt = (type) => {
        if(!matchEngine.isActive) return; 
        
        if(matchEngine.strikerIdx === -1 || matchEngine.nonStrikerIdx === -1) return showToast("Please Select Batsman Manually!");
        if(matchEngine.bowlerIdx === -1) return showToast("Please Select Bowler Manually!");

        pendingActionType = type;
        document.getElementById('runPromptTitle').innerText = (type==='out') ? "Runs Completed Before Out?" : "Runs Scored?"; 
        document.getElementById('dynamicRunModal').classList.add('active');
    };
    window.submitDynamicRun = (runs) => { document.getElementById('dynamicRunModal').classList.remove('active'); if(pendingActionType === 'out') { execWicket(runs); } else { execExtra(pendingActionType, runs); } };

    window.execExtra = (type, runs) => {
        saveState(); let st = matchEngine.battingLineup[matchEngine.strikerIdx]; let bl = matchEngine.bowlingLineup[matchEngine.bowlerIdx];
        if(type==='wd') { matchEngine.runs += (1 + runs); matchEngine.pShipRuns += (1+runs); bl.bowlRuns += (1 + runs); matchEngine.currentOverBalls.push({ type: 'wd', val: runs>0?`Wd+${runs}`:'Wd' }); if(runs%2!==0) swapStrike(); }
        if(type==='nb') { matchEngine.runs += (1 + runs); matchEngine.pShipRuns += (1+runs); bl.bowlRuns += (1 + runs); st.batRuns += runs; st.batBalls++; matchEngine.pShipBalls++; matchEngine.currentOverBalls.push({ type: 'nb', val: runs>0?`Nb+${runs}`:'Nb' }); if(runs%2!==0) swapStrike(); }
        if(type==='bye' || type==='lb') { matchEngine.runs += runs; matchEngine.pShipRuns += runs; matchEngine.balls++; matchEngine.pShipBalls++; bl.bowlBalls++; st.batBalls++; matchEngine.currentOverBalls.push({ type: 'extra', val: `${runs}${type.charAt(0).toUpperCase()}` }); if(runs%2!==0) swapStrike(); }
        checkOverOrInningsEnd(); updateScoringUI();
    };

    window.execWicket = (runsCompleted) => {
        saveState(); matchEngine.wickets++; matchEngine.balls++;
        let st = matchEngine.battingLineup[matchEngine.strikerIdx]; let bl = matchEngine.bowlingLineup[matchEngine.bowlerIdx];
        matchEngine.runs += runsCompleted; matchEngine.pShipRuns += runsCompleted; matchEngine.pShipBalls++;
        st.batRuns += runsCompleted; st.batBalls++; bl.bowlBalls++; bl.wickets++; st.out=true;
        matchEngine.currentOverBalls.push({ type: 'wicket', val: runsCompleted>0?`W+${runsCompleted}`:'W' });
        
        matchEngine.pShipRuns = 0; matchEngine.pShipBalls = 0;
        
        document.body.classList.remove('shake-screen');
        void document.body.offsetWidth;
        document.body.classList.add('shake-screen');

        if(runsCompleted % 2 !== 0) swapStrike();

        if(runsCompleted % 2 !== 0) { matchEngine.nonStrikerIdx = -1; } else { matchEngine.strikerIdx = -1; }

        checkOverOrInningsEnd(); updateScoringUI();
        showToast("Wicket! Please Select New Batsman.");
    };

    function swapStrike() { let t=matchEngine.strikerIdx; matchEngine.strikerIdx=matchEngine.nonStrikerIdx; matchEngine.nonStrikerIdx=t; }
    
    function checkOverOrInningsEnd() {
        if(matchEngine.balls>0 && matchEngine.balls%6===0){ 
            swapStrike(); 
            matchEngine.currentOverBalls = []; 
            matchEngine.bowlerIdx = -1; 
            showToast("Over complete! Select New Bowler."); 
        }
        if(matchEngine.innings===2 && matchEngine.target && matchEngine.runs>=matchEngine.target){ matchEngine.isActive=false; setTimeout(finishMatch, 1500); }
        if(matchEngine.balls >= wizData.overs*6 || matchEngine.wickets >= matchEngine.battingLineup.length-1){
            if(matchEngine.innings===1){ document.getElementById('btnNextInnings').style.boxShadow='0 0 15px rgba(245,158,11,0.8)'; }
            else { matchEngine.isActive=false; setTimeout(finishMatch, 1500); }
        }
    }

    window.changeInnings = () => {
        if(matchEngine.innings!==1) return;
        wizData.t1FinalScore = `${matchEngine.runs}/${matchEngine.wickets}`;
        wizData.t1FinalOvers = `${Math.floor(matchEngine.balls/6)}.${matchEngine.balls%6}`;

        matchEngine.innings=2; matchEngine.target=matchEngine.runs+1;
        let tt=matchEngine.batTeam; matchEngine.batTeam=matchEngine.bowlTeam; matchEngine.bowlTeam=tt;
        let tl=matchEngine.battingLineup; matchEngine.battingLineup=matchEngine.bowlingLineup; matchEngine.bowlingLineup=tl;
        matchEngine.runs=0; matchEngine.wickets=0; matchEngine.balls=0; matchEngine.strikerIdx=-1; matchEngine.nonStrikerIdx=-1; matchEngine.bowlerIdx=-1; matchEngine.history=[]; matchEngine.currentOverBalls=[]; matchEngine.pShipRuns=0; matchEngine.pShipBalls=0;
        
        document.getElementById('btnNextInnings').style.display='none'; document.getElementById('btnEndMatch').style.display='block'; updateScoringUI();
    };

    function updateScoringUI() {
        if(!matchEngine.isActive && matchEngine.innings===1) return;
        document.getElementById('padBattingTeamName').innerText = matchEngine.batTeam;
        
        let grEl = document.getElementById('padGroundName');
        if(grEl) grEl.innerHTML = `<i class="fas fa-map-marker-alt"></i> ${wizData.ground || 'Unknown Ground'}`;

        let ovs = Math.floor(matchEngine.balls/6); let bls = matchEngine.balls%6;
        document.getElementById('padRuns').innerText = matchEngine.runs; 
        document.getElementById('padWickets').innerText = matchEngine.wickets;
        document.getElementById('padOvers').innerText = `${ovs}.${bls}`; 
        document.getElementById('padTotalOvers').innerText = wizData.overs;
        document.getElementById('matchTargetDisplay').innerText = matchEngine.innings===1?"1st Innings":"2nd Innings";
        
        document.getElementById('padPartnership').innerText = `Partnership: ${matchEngine.pShipRuns || 0} (${matchEngine.pShipBalls || 0})`;
        if(matchEngine.innings === 2 && matchEngine.target) {
            let remRuns = matchEngine.target - matchEngine.runs;
            let remBalls = (wizData.overs * 6) - matchEngine.balls;
            let rrr = remBalls > 0 ? ((remRuns / remBalls) * 6).toFixed(2) : "0.00";
            document.getElementById('padRRR').innerText = `Target: ${matchEngine.target} (RRR: ${rrr})`;
            
            let wpBox = document.getElementById('winProbBar');
            wpBox.style.display = 'flex';
            let prob = Math.min(Math.max((matchEngine.runs / matchEngine.target) * 100, 5), 95);
            document.getElementById('wpA').style.width = prob + '%';
            document.getElementById('wpB').style.width = (100 - prob) + '%';
        } else {
            document.getElementById('padRRR').innerText = `1st Innings`;
            document.getElementById('winProbBar').style.display = 'none';
        }

        let crr = matchEngine.balls > 0 ? ((matchEngine.runs / matchEngine.balls) * 6).toFixed(2) : "0.00";
        document.getElementById('padCrr').innerText = crr;
        document.getElementById('currentOverNum').innerText = ovs + 1;

        const timelineEl = document.getElementById('padOverTimeline');
        if(matchEngine.currentOverBalls.length === 0) { timelineEl.innerHTML = '<div style="font-size:0.8rem; color:#9CA3AF; font-weight:600;">Start of over...</div>'; } 
        else {
            timelineEl.innerHTML = matchEngine.currentOverBalls.map(b => {
                let cls = 'ball-dot';
                if(b.type === 'run' && b.val === 4) cls += ' four';
                if(b.type === 'run' && b.val === 6) cls += ' six';
                if(b.type === 'wicket') cls += ' out';
                if(b.type === 'wd' || b.type === 'nb' || b.type === 'extra') cls += ' extra';
                return `<div class="${cls}">${b.val}</div>`;
            }).join('');
        }
        
        const sS=document.getElementById('padStrikerSel'); const nsS=document.getElementById('padNonStrikerSel'); const bS=document.getElementById('padBowlerSel');
        
        let batLineup = matchEngine.battingLineup || [];
        let bowlLineup = matchEngine.bowlingLineup || [];

        let bO= `<option value="-1">-- Select Batsman --</option>` + batLineup.map((p,i)=>`<option value="${i}" ${p.out?'disabled':''}>${p.name}</option>`).join('');
        let blO= `<option value="-1">-- Select Bowler --</option>` + bowlLineup.map((p,i)=>`<option value="${i}">${p.name}</option>`).join('');
        
        sS.innerHTML = bO; nsS.innerHTML = bO; bS.innerHTML = blO;
        sS.value = matchEngine.strikerIdx; nsS.value = matchEngine.nonStrikerIdx; bS.value = matchEngine.bowlerIdx;
        
        let st = batLineup[matchEngine.strikerIdx]; let nst = batLineup[matchEngine.nonStrikerIdx]; let bl = bowlLineup[matchEngine.bowlerIdx];
        
        if(st) {
            document.getElementById('padStrikerStats').innerText=`${st.batRuns} (${st.batBalls})`;
            let sr = st.batBalls > 0 ? ((st.batRuns / st.batBalls)*100).toFixed(1) : "0.0";
            let srEl = document.getElementById('padStrikerSR');
            if(srEl) { srEl.innerText = `SR: ${sr}`; if(sr > 150 && st.batBalls > 5) srEl.classList.add('fire-effect'); else srEl.classList.remove('fire-effect'); }
        } else {
            document.getElementById('padStrikerStats').innerText=`0 (0)`;
            let srEl = document.getElementById('padStrikerSR');
            if(srEl) { srEl.innerText = `SR: 0.0`; srEl.classList.remove('fire-effect'); }
        }
        
        if(nst) {
            document.getElementById('padNonStrikerStats').innerText=`${nst.batRuns} (${nst.batBalls})`;
            let nsr = nst.batBalls > 0 ? ((nst.batRuns / nst.batBalls)*100).toFixed(1) : "0.0";
            let nsrEl = document.getElementById('padNonStrikerSR');
            if(nsrEl) { nsrEl.innerText = `SR: ${nsr}`; if(nsr > 150 && nst.batBalls > 5) nsrEl.parentElement.classList.add('fire-effect'); else nsrEl.parentElement.classList.remove('fire-effect'); }
        } else {
            document.getElementById('padNonStrikerStats').innerText=`0 (0)`;
            let nsrEl = document.getElementById('padNonStrikerSR');
            if(nsrEl) { nsrEl.innerText = `0.0`; nsrEl.parentElement.classList.remove('fire-effect'); }
        }
        
        if(bl) {
            let bo = Math.floor(bl.bowlBalls/6); let bb = bl.bowlBalls%6;
            document.getElementById('padBowlerStats').innerText=`${bo}.${bb} - ${bl.bowlRuns} - ${bl.wickets}`;
            let bOversCalc = bl.bowlBalls / 6;
            let econ = bOversCalc > 0 ? (bl.bowlRuns / bOversCalc).toFixed(2) : "0.00";
            document.getElementById('padBowlerEcon').innerText = `Econ: ${econ}`;
        } else {
            document.getElementById('padBowlerStats').innerText=`0.0-0-0`;
            let beEl = document.getElementById('padBowlerEcon');
            if(beEl) beEl.innerText = `Econ: 0.00`;
        }

        let d = { active: true, teamA: wizData.t1Name, teamB: wizData.t2Name, scoreA: matchEngine.innings === 1 ? `${matchEngine.runs}/${matchEngine.wickets}` : wizData.t1FinalScore, scoreB: matchEngine.innings === 2 ? `${matchEngine.runs}/${matchEngine.wickets}` : '0/0', oversA: matchEngine.innings === 1 ? `${ovs}.${bls}` : wizData.t1FinalOvers, oversB: matchEngine.innings === 2 ? `${ovs}.${bls}` : '', liveLink: wizData.liveLink || '' };
        update(ref(database, 'liveScore'), d);
    }

    window.manualChangeStriker = (val) => { matchEngine.strikerIdx=parseInt(val); updateScoringUI(); showToast("Striker Changed"); }
    window.manualChangeNonStriker = (val) => { matchEngine.nonStrikerIdx=parseInt(val); updateScoringUI(); showToast("Non-Striker Changed"); }
    window.manualChangeBowler = (val) => { matchEngine.bowlerIdx=parseInt(val); updateScoringUI(); showToast("Bowler Changed"); }

    window.finishMatch = async () => {
        showLoader(true);
        let winnerTeam = ""; let wonBy = "";

        if (matchEngine.runs >= matchEngine.target) {
            winnerTeam = matchEngine.batTeam;
            let wktDiff = matchEngine.battingLineup.length - 1 - matchEngine.wickets;
            wonBy = `${winnerTeam} Won By ${wktDiff} Wickets`;
        } else {
            winnerTeam = matchEngine.bowlTeam;
            let runDiff = matchEngine.target - 1 - matchEngine.runs;
            wonBy = `${winnerTeam} Won By ${runDiff} Runs`;
        }
        
        let mData = { 
            id: matchEngine.matchId, 
            date: new Date().toLocaleString('en-US', { year: 'numeric', month: 'short', day: 'numeric', hour: '2-digit', minute: '2-digit' }), 
            teamA: wizData.t1Name, teamB: wizData.t2Name, 
            scoreA: wizData.t1FinalScore || `${matchEngine.runs}/${matchEngine.wickets}`, 
            scoreB: matchEngine.innings===2 ? `${matchEngine.runs}/${matchEngine.wickets}` : '0/0', 
            result: wonBy, status: "Completed", 
            teamAStats: matchEngine.innings===1 ? matchEngine.battingLineup : matchEngine.bowlingLineup, 
            teamBStats: matchEngine.innings===1 ? matchEngine.bowlingLineup : matchEngine.battingLineup, 
            wizState: JSON.stringify(wizData),
            timestamp: Date.now() 
        };
        
        await set(ref(database, `matches/${mData.id}`), mData);
        await update(ref(database, 'liveScore'), { active: false });

        const updateCareer = async (p) => {
            if(!p.id) return;
            const refP = ref(database, `players/${p.id}`); const s = await get(refP);
            if(s.exists()) {
                let d = s.val(); let r = (d.runs||0) + p.batRuns; let w = (d.wickets||0) + p.wickets; let m = (d.matches||0) + 1;
                let hs = d.highestScore || 0; let hsb = d.hsBalls || 0;
                if(p.batRuns > hs) { hs = p.batRuns; hsb = p.batBalls; }
                let bb = d.bestBowling || {w:0, r:0, b:0};
                if(p.wickets > bb.w || (p.wickets === bb.w && p.bowlRuns < bb.r)) { bb = {w: p.wickets, r: p.bowlRuns, b: p.bowlBalls}; }
                await update(refP, { runs: r, wickets: w, matches: m, highestScore: hs, hsBalls: hsb, bestBowling: bb });
            }
        };
        if(mData.teamAStats) for(let p of mData.teamAStats) await updateCareer(p);
        if(mData.teamBStats) for(let p of mData.teamBStats) await updateCareer(p);

        showLoader(false); 
        
        document.getElementById('celebWinner').innerText = winnerTeam.toUpperCase() + " WON!";
        document.getElementById('celebMargin').innerText = wonBy;
        document.getElementById('celebrationOverlay').classList.add('active');
        
        matchEngine.isActive=false;
    };

    window.closeCelebration = () => {
        document.getElementById('celebrationOverlay').classList.remove('active');
        switchTab('matches', document.querySelectorAll('.nav-item')[1]);
    };

    // --- 100% FIXED PROFILE CLICK ISSUE ---
    window.viewOtherPlayer = (id) => {
        try {
            let p = allPlayers.find(x => x.id === id); 
            if(!p) return;
            
            document.getElementById('pdName').innerText = p.name || 'Unknown'; 
            document.getElementById('pdCode').innerText = "ID: " + (p.code || "N/A");
            document.getElementById('pdRole').innerText = (p.role || 'Player').toUpperCase(); 
            
            document.getElementById('pdRuns1').innerText = p.runs || 0; 
            document.getElementById('pdWickets1').innerText = p.wickets || 0;
            document.getElementById('pdHS1').innerText = `${p.highestScore || 0} (${p.hsBalls || 0})`;
            document.getElementById('pdBB1').innerText = (p.bestBowling && p.bestBowling.w > 0) ? `${p.bestBowling.w}W / ${p.bestBowling.r}R` : `0W / 0R`;
            
            const av = document.getElementById('pdAvatar');
            if(p.photoUrl){ 
                av.innerHTML=`<img src="${p.photoUrl}" style="width:100%; height:100%; object-fit:cover;">`; 
                av.style.background='transparent'; 
            } else { 
                av.innerHTML = p.name ? p.name.charAt(0).toUpperCase() : 'P'; 
                av.style.background='rgba(255,42,70,0.1)'; 
            }
            
            document.getElementById('playerDetailModal').classList.add('active');
        } catch(e) {
            console.error("Profile view error: ", e);
            showToast("Failed to load profile.");
        }
    };

    window.viewMatchDetails = (id) => {
        let m = allMatches.find(x => x.id === id); if(!m) return;
        
        let wData = m.wizState ? JSON.parse(m.wizState) : {};
        let ground = wData.ground || "Unknown Stadium";
        let dateFull = m.date;

        let allStats = [...(m.teamAStats||[]), ...(m.teamBStats||[])];
        let mom = allStats.reduce((prev, current) => {
            let prevPoints = (prev.batRuns || 0) + ((prev.wickets || 0) * 20);
            let currPoints = (current.batRuns || 0) + ((current.wickets || 0) * 20);
            return (currPoints > prevPoints) ? current : prev;
        }, {});

        document.getElementById('mdTitle').innerText = `${m.teamA} vs ${m.teamB}`;
        
        let html = `
        <div style="background:var(--gold-gradient); border-radius:16px; padding:16px; text-align:center; margin-bottom:20px; color:#000; box-shadow:0 10px 30px rgba(255, 215, 0, 0.3);">
            <div style="font-size:0.75rem; font-weight:800; letter-spacing:3px; text-transform:uppercase; margin-bottom:4px;"><i class="fas fa-crown"></i> MAN OF THE MATCH</div>
            <div style="font-size:1.6rem; font-weight:900;">${mom.name || 'No Data'}</div>
            <div style="font-size:0.9rem; font-weight:700;">${mom.batRuns||0} Runs & ${mom.wickets||0} Wickets</div>
        </div>
        
        <div style="text-align:center; margin-bottom: 20px;">
            <div style="font-size:0.8rem; color:var(--text-muted); font-weight:700; margin-bottom:4px;">${dateFull} • ${ground}</div>
            <div style="font-size:1.1rem; color:#fff; font-weight:800;">${m.result}</div>
        </div>
        `;
        
        const renderTable = (teamName, teamScore, stats) => {
            if(!stats || stats.length===0) return '';
            let t = `
            <div style="background:rgba(255,42,70,0.1); padding:10px 12px; border-radius:12px; display:flex; justify-content:space-between; align-items:center; margin:20px 0 10px; border:1px solid rgba(255,42,70,0.3);">
                <div style="color:#fff; font-weight:900; font-size:1.1rem;">${teamName}</div>
                <div style="color:var(--primary); font-weight:900; font-size:1.2rem;">${teamScore}</div>
            </div>`;
            t += `<table class="scorecard-table"><thead><tr><th>BATSMAN</th><th>R</th><th>B</th></tr></thead><tbody>`;
            stats.forEach(p => { if(p.batBalls>0) t += `<tr><td>${p.name} ${p.out?'<span style="color:var(--primary); font-size:0.7rem;">(W)</span>':''} ${p.code?`<span class="player-code-badge">${p.code}</span>`:''}</td><td style="font-weight:800;">${p.batRuns}</td><td>${p.batBalls}</td></tr>`; });
            t += `</tbody></table>`;
            t += `<table class="scorecard-table" style="margin-top:10px;"><thead><tr><th>BOWLER</th><th>O</th><th>R</th><th>W</th></tr></thead><tbody>`;
            stats.forEach(p => { if(p.bowlBalls>0) t += `<tr><td>${p.name}</td><td>${Math.floor(p.bowlBalls/6)}.${p.bowlBalls%6}</td><td>${p.bowlRuns}</td><td style="color:var(--accent); font-weight:900;">${p.wickets}</td></tr>`; });
            t += `</tbody></table>`;
            return t;
        };

        html += renderTable(m.teamA, m.scoreA, m.teamAStats);
        html += renderTable(m.teamB, m.scoreB, m.teamBStats);
        document.getElementById('mdContent').innerHTML = html;
        document.getElementById('matchDetailsModal').classList.add('active');
    };

    window.shareMatchResult = () => {
        let content = document.getElementById('mdContent').innerText;
        if(navigator.share) {
            navigator.share({ title: 'Tigers Prime Match Result', text: content });
        } else { showToast("Share API not supported."); }
    };

    function setupRealtimeListeners() {
        onValue(ref(database, 'players'), (snap) => {
            allPlayers = snap.exists() ? Object.keys(snap.val()).map(k => ({ id: k, ...snap.val()[k] })) : [];
            let squadElem = document.getElementById('total-squad');
            if(squadElem) squadElem.innerText = allPlayers.length; 
            renderPlayersList(allPlayers);
            let dl = document.getElementById('dbPlayersList');
            if(dl) dl.innerHTML = allPlayers.map(p => `<option value="${p.name}">`).join('');
        });
        
        onValue(ref(database, 'matches'), (snap) => {
            allMatches = snap.exists() ? Object.keys(snap.val()).map(k => ({ id: k, ...snap.val()[k] })).sort((a,b)=>(b.timestamp||0)-(a.timestamp||0)) : [];
            let tm = document.getElementById('total-matches');
            if(tm) tm.innerText = allMatches.filter(m=>m.status==='Completed').length; 
            renderMatches(allMatches);
        });
        
        onValue(ref(database, 'liveScore'), (snap) => {
            const tickerContent = document.getElementById('mainTickerContent');
            if(snap.exists() && snap.val().active) {
                let d = snap.val();
                if(tickerContent) tickerContent.innerHTML = `<i class="fas fa-star" style="color:var(--accent); margin:0 8px;"></i> WELCOME TO TIGERS PRIME <i class="fas fa-circle" style="color:var(--primary); font-size:0.6rem; margin:0 8px; animation:blink 1s infinite;"></i> 🔴 LIVE NOW: ${d.teamA} ${d.scoreA} vs ${d.teamB} ${d.scoreB} <i class="fas fa-bolt" style="color:var(--accent); margin:0 8px;"></i>`;

                let el1 = document.getElementById('liveTeamA'); if(el1) el1.innerText=d.teamA||'-'; 
                let el2 = document.getElementById('liveScoreA'); if(el2) el2.innerText=d.scoreA||'0/0'; 
                let el3 = document.getElementById('liveOversA'); if(el3) el3.innerText=d.oversA?`(${d.oversA} ov)`:'';
                let el4 = document.getElementById('liveTeamB'); if(el4) el4.innerText=d.teamB||'-'; 
                let el5 = document.getElementById('liveScoreB'); if(el5) el5.innerText=d.scoreB||'0/0'; 
                let el6 = document.getElementById('liveOversB'); if(el6) el6.innerText=d.oversB?`(${d.oversB} ov)`:'';
                
                let bge = document.getElementById('liveStatusBadge');
                if(bge) { bge.innerText='ON AIR'; bge.style.background = 'var(--primary)'; bge.style.boxShadow = '0 0 10px var(--primary-glow)'; }
                let ct = document.getElementById('countdownTimer');
                if(ct) { ct.innerText='MATCH IN PROGRESS'; ct.style.color = '#fff'; }

                const watchBtn = document.getElementById('liveWatchBtn');
                if(watchBtn) { if(d.liveLink) { watchBtn.style.display = 'inline-block'; watchBtn.href = d.liveLink; } else { watchBtn.style.display = 'none'; } }
            } else { 
                if(tickerContent) tickerContent.innerHTML = `<i class="fas fa-star" style="color:var(--accent); margin:0 8px;"></i> WELCOME TO TIGERS PRIME • ELITE SCORING ENGINE <i class="fas fa-trophy" style="color:var(--accent); margin:0 8px;"></i> NO LIVE MATCH CURRENTLY <i class="fas fa-bolt" style="color:var(--accent); margin:0 8px;"></i> PREPARE FOR THE NEXT BATTLE`;
                
                let bge = document.getElementById('liveStatusBadge');
                if(bge) { bge.innerText='OFFLINE'; bge.style.background = 'rgba(255,255,255,0.1)'; bge.style.boxShadow = 'none'; }
                let ct = document.getElementById('countdownTimer');
                if(ct) { ct.innerText='No Match Running'; ct.style.color = 'var(--text-muted)'; }
                let wb = document.getElementById('liveWatchBtn');
                if(wb) wb.style.display = 'none';
            }
        });

        onValue(ref(database, 'notices'), (snap) => {
            if(snap.exists()){
                const arr = Object.values(snap.val()).sort((a,b)=>b.timestamp-a.timestamp);
                let html = arr.map(n=>`<div class="notification-item"><strong style="font-size:0.75rem; color:var(--accent);">${n.date||'Update'}</strong><div style="font-size:0.9rem; margin-top:2px; font-weight:600; color:#fff;">${n.text}</div></div>`).join('');
                let nl = document.getElementById('noticeList'); if(nl) nl.innerHTML = html;
                let fl = document.getElementById('fullNotificationList'); if(fl) fl.innerHTML = html;
                let lastSeen = localStorage.getItem('lastSeenNotice') || 0;
                let unread = arr.filter(n => n.timestamp > lastSeen).length;
                let badge = document.getElementById('notifBadge');
                if(badge) { if(unread > 0) { badge.style.display = 'flex'; badge.innerText = unread; } else { badge.style.display = 'none'; } }
            }
        });
    }

    function renderPlayersList(players) {
        const pl = document.getElementById('player-list');
        if(!pl) return;
        if(!players.length) { pl.innerHTML='<div style="font-size:0.85rem; color:var(--text-muted); text-align:center; padding:20px;">No personnel found</div>'; return; }
        pl.innerHTML = players.map(p=>`
            <div class="card" style="padding:14px 16px; margin-bottom:10px; display:flex; align-items:center; cursor:pointer;" onclick="viewOtherPlayer('${p.id}')">
                ${p.photoUrl ? `<img src="${p.photoUrl}" style="width:45px; height:45px; border-radius:50%; margin-right:12px; border:1px solid rgba(255,190,11,0.3); object-fit:cover;">` : `<div style="width:45px; height:45px; border-radius:50%; background:rgba(255,190,11,0.1); border:1px solid rgba(255,190,11,0.3); margin-right:12px; display:flex; align-items:center; justify-content:center; font-weight:800; color:var(--accent); font-size:1.1rem;">${p.name.charAt(0).toUpperCase()}</div>`}
                <div style="flex:1;">
                    <div style="font-weight:700; font-size:0.95rem; margin-bottom:2px; display:flex; align-items:center; gap:6px;">${p.name} <span style="font-size:0.65rem; background:rgba(255,255,255,0.1); padding:2px 6px; border-radius:6px; color:var(--accent);">${p.code||'N/A'}</span></div>
                    <div style="color:var(--text-muted); font-size:0.75rem; font-weight:600;">HS: <span style="color:var(--primary);">${p.highestScore||0}</span> | BB: <span style="color:var(--accent);">${p.bestBowling?p.bestBowling.w+'/'+p.bestBowling.r:'0/0'}</span></div>
                </div>
                <div style="text-align:right;"><span style="color:#fff; font-weight:800; font-size:0.95rem; display:block;">${p.runs||0} R</span><span style="color:var(--accent); font-weight:800; font-size:0.8rem;">${p.wickets||0} W</span></div>
            </div>
        `).join('');
    }

    window.filterMatches = () => {
        let input = document.getElementById('matchSearch').value.toLowerCase();
        let cards = document.querySelectorAll('.dream-card');
        cards.forEach(card => {
            let text = card.innerText.toLowerCase();
            card.style.display = text.includes(input) ? "block" : "none";
        });
    };

    function renderMatches(mArr) {
        const hContainer = document.getElementById('homeMatchesContainer');
        if(!hContainer) return;
        if(!mArr.length) { hContainer.innerHTML='<div style="font-size:0.85rem; color:var(--text-muted); text-align:center; padding:20px;">No match logs</div>'; return; }
        
        hContainer.innerHTML = mArr.map(m => {
            let isPaused = m.status === 'Paused';
            let isFinished = m.status === 'Completed';
            let statusBadge = isFinished ? `<span class="badge-status badge-finished"><i class="fas fa-check-circle"></i> Finished</span>` : `<span class="badge-status"><i class="fas fa-satellite-dish"></i> Upcoming/Paused</span>`;
            
            let btnAction = isPaused ? `<button class="btn-primary ripple-btn" style="padding:10px;" onclick="playSound('click'); resumeMatch('${m.id}')">Resume Match</button>` : `<button class="btn-outline ripple-btn" style="padding:10px; border-color:var(--accent); color:var(--accent);" onclick="playSound('click'); viewMatchDetails('${m.id}')">View Scorecard</button>`;
            
            let wData = m.wizState ? JSON.parse(m.wizState) : {};
            let overs = wData.overs || '20';
            let ground = wData.ground || 'Unknown Ground';
            
            return `
            <div class="dream-card">
                <div class="dream-header">
                    <div class="dream-header-title">🏏 ${m.teamA} VS ${m.teamB}</div>
                    ${statusBadge}
                </div>
                <div class="dream-body">
                    <div class="dream-info-row"><i class="far fa-calendar-alt"></i> ${m.date || ''}</div>
                    <div class="dream-info-row"><i class="fas fa-map-marker-alt"></i> ${ground}</div>
                    <div class="dream-info-row"><i class="fas fa-bullseye"></i> ${overs} Overs Match</div>
                    
                    ${isFinished ? `
                    <div style="display:flex; justify-content:space-between; align-items:center; margin-top:8px; background:rgba(0,0,0,0.3); padding:10px; border-radius:10px; border:1px solid rgba(255,255,255,0.05);">
                        <div style="text-align:center;"><div style="font-size:0.7rem; color:var(--text-muted);">${m.teamA}</div><div style="font-size:1.2rem; font-weight:900; color:#fff;">${m.scoreA}</div></div>
                        <div style="font-size:1rem; font-weight:900; color:var(--text-muted);">V</div>
                        <div style="text-align:center;"><div style="font-size:0.7rem; color:var(--text-muted);">${m.teamB}</div><div style="font-size:1.2rem; font-weight:900; color:#fff;">${m.scoreB}</div></div>
                    </div>` : ''}

                </div>
                <div class="dream-footer">
                    ${isFinished ? `🏆 ${m.result}` : 'Teams Announced • Match Not Finished'}
                </div>
                <div style="padding: 0 16px 16px;">${btnAction}</div>
            </div>`;
        }).join('');
    }

    function initParticles() {
        const container = document.getElementById('particles-container');
        if(!container) return;
        setInterval(() => {
            let p = document.createElement('div');
            p.className = 'particle';
            let size = Math.random() * 10 + 5;
            p.style.width = size + 'px'; p.style.height = size + 'px';
            p.style.left = Math.random() * 100 + 'vw';
            p.style.animationDuration = Math.random() * 5 + 5 + 's';
            container.appendChild(p);
            setTimeout(() => { p.remove(); }, 10000);
        }, 800);
    }

    window.triggerCinematic = (text, colorClass) => {
        const overlay = document.getElementById('cinematicPopup'); const textEl = document.getElementById('cinematicText');
        const particles = document.getElementById('cinematicParticles');
        if(!overlay || !textEl) return;
        
        textEl.className = `cinematic-text ${colorClass}`; textEl.innerText = text;
        if(particles) particles.className = colorClass === 'event-six' ? 'event-six-particles' : '';

        overlay.classList.add('active');
        if (navigator.vibrate) navigator.vibrate([100, 50, 100]);
        setTimeout(() => { overlay.classList.remove('active'); triggerScoreAnimation(); }, 1800);
    };

    window.triggerScoreAnimation = () => {
        const scoreEl = document.getElementById('animatedScore');
        if(scoreEl) { scoreEl.classList.remove('flip-animate'); void scoreEl.offsetWidth; scoreEl.classList.add('flip-animate'); }
    };

    document.addEventListener('mousemove', function(e) {
        document.querySelectorAll('.card').forEach(card => {
            const rect = card.getBoundingClientRect();
            const x = e.clientX - rect.left; const y = e.clientY - rect.top;
            const centerX = rect.width / 2; const centerY = rect.height / 2;
            if(x > 0 && x < rect.width && y > 0 && y < rect.height) {
                const rotateX = ((y - centerY) / centerY) * -3;
                const rotateY = ((x - centerX) / centerX) * 3;
                card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) translateY(-3px) scale(1.01)`;
            } else { card.style.transform = `perspective(1000px) rotateX(0deg) rotateY(0deg) translateY(0) scale(1)`; }
        });
    });

    initParticles(); 
</script>
</body>
</html>
