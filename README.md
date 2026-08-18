    :root {
        --purple: #7C3F9E;
        --purple-light: #9B5FC4;
        --purple-pale: #F3EBFF;
        --purple-dark: #5A2D75;
        --pink: #FFB6C1;
        --blue: #87CEEB;
        --green: #90EE90;
        --yellow: #FFD700;
        --red: #FF6B6B;
        --white: #FFFFFF;
        --gray: #F5F5F5;
        --text: #2C2C2C;
        --text-light: #666;
    }

    html, body {
        width: 100%;
        min-height: 100%;
        overflow-x: hidden;
        overflow-y: auto;
        -webkit-overflow-scrolling: touch;
    }

    body {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang HK", "Microsoft YaHei", sans-serif;
        background: #1a0a2e;
        color: var(--text);
        font-size: 16px;
    }

    /* ===== SCREENS ===== */
    .screen {
        display: none;
        width: 100%;
        max-width: 600px;
        margin: 0 auto;
        background: white;
        position: relative;
    }
    .screen.active { display: block; }

    /* ===== DISCLAIMER SCREEN ===== */
    #screen-disclaimer {
        background: linear-gradient(160deg, #1a0a2e 0%, #3d1a6e 50%, #7C3F9E 100%);
        min-height: 100vh;
    }
    #screen-disclaimer.active {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 40px 30px;
    }

    .disclaimer-logo {
        font-size: 60px;
        margin-bottom: 20px;
        animation: float 3s ease-in-out infinite;
    }
    @keyframes float {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-10px); }
    }

    .disclaimer-title {
        color: white;
        font-size: 26px;
        font-weight: 800;
        text-align: center;
        margin-bottom: 8px;
        line-height: 1.3;
    }
    .disclaimer-subtitle {
        color: rgba(255,255,255,0.7);
        font-size: 14px;
        text-align: center;
        margin-bottom: 30px;
    }
    .disclaimer-box {
        background: rgba(255,255,255,0.12);
        border: 1px solid rgba(255,255,255,0.25);
        border-radius: 16px;
        padding: 22px;
        margin-bottom: 25px;
        backdrop-filter: blur(10px);
        width: 100%;
        max-width: 480px;
    }
    .disclaimer-box p {
        color: rgba(255,255,255,0.9);
        font-size: 13px;
        line-height: 1.7;
        text-align: center;
    }
    .disclaimer-box strong { color: #FFD700; }

    .info-pills {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        justify-content: center;
        margin-bottom: 30px;
    }
    .info-pill {
        background: rgba(255,255,255,0.15);
        color: white;
        font-size: 12px;
        padding: 6px 14px;
        border-radius: 20px;
        border: 1px solid rgba(255,255,255,0.2);
    }

    /* ===== BUTTONS ===== */
    .btn-primary {
        background: linear-gradient(135deg, #FFD700, #FFA500);
        color: #1a0a2e;
        border: none;
        padding: 16px 40px;
        border-radius: 50px;
        font-size: 17px;
        font-weight: 800;
        cursor: pointer;
        width: 100%;
        max-width: 320px;
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 6px 20px rgba(255,215,0,0.4);
        letter-spacing: 0.5px;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
        display: block;
    }
    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 10px 28px rgba(255,215,0,0.5); }
    .btn-primary:active { transform: translateY(0); }

    .btn-choice {
        background: white;
        border: 2px solid var(--purple);
        color: var(--purple);
        padding: 14px 20px;
        border-radius: 12px;
        font-size: 15px;
        font-weight: 600;
        cursor: pointer;
        width: 100%;
        text-align: left;
        transition: background 0.2s, color 0.2s, transform 0.2s, box-shadow 0.2s;
        margin-bottom: 12px;
        line-height: 1.4;
        display: flex;
        align-items: flex-start;
        gap: 10px;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
    }
    .btn-choice:hover, .btn-choice:active {
        background: var(--purple);
        color: white;
        transform: translateX(4px);
        box-shadow: 0 4px 15px rgba(124,63,158,0.3);
    }
    .btn-choice .choice-icon { font-size: 20px; flex-shrink: 0; margin-top: 1px; }
    .btn-choice .choice-text { flex: 1; }

    .btn-next {
        background: linear-gradient(135deg, var(--purple), var(--purple-light));
        color: white;
        border: none;
        padding: 16px 30px;
        border-radius: 50px;
        font-size: 16px;
        font-weight: 700;
        cursor: pointer;
        width: 100%;
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 4px 15px rgba(124,63,158,0.35);
        margin-top: 10px;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
        display: block;
        min-height: 52px;
    }
    .btn-next:hover { transform: translateY(-2px); box-shadow: 0 8px 22px rgba(124,63,158,0.45); }
    .btn-next:active { transform: translateY(0); }

    .btn-replay {
        background: transparent;
        border: 2px solid var(--purple);
        color: var(--purple);
        padding: 14px 30px;
        border-radius: 50px;
        font-size: 15px;
        font-weight: 700;
        cursor: pointer;
        width: 100%;
        transition: background 0.2s;
        margin-top: 12px;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
        display: block;
        min-height: 52px;
    }
    .btn-replay:hover { background: var(--purple-pale); }

    /* ===== PROGRESS BAR ===== */
    .progress-header {
        background: var(--purple-dark);
        padding: 14px 20px;
        display: flex;
        align-items: center;
        gap: 12px;
        position: sticky;
        top: 0;
        z-index: 100;
    }
    .progress-label { color: rgba(255,255,255,0.8); font-size: 12px; white-space: nowrap; font-weight: 600; }
    .progress-bar-wrap { flex: 1; background: rgba(255,255,255,0.2); border-radius: 10px; height: 8px; overflow: hidden; }
    .progress-bar-fill { height: 100%; background: linear-gradient(90deg, #FFD700, #FFA500); border-radius: 10px; transition: width 0.6s ease; }
    .progress-score { color: #FFD700; font-size: 13px; font-weight: 800; white-space: nowrap; }

    /* ===== CHAPTER HEADER ===== */
    .chapter-header {
        background: linear-gradient(135deg, var(--purple-dark), var(--purple));
        padding: 30px 25px 25px;
        color: white;
        text-align: center;
    }
    .chapter-tag {
        display: inline-block;
        background: rgba(255,255,255,0.2);
        color: rgba(255,255,255,0.9);
        font-size: 11px;
        font-weight: 700;
        padding: 4px 14px;
        border-radius: 20px;
        margin-bottom: 12px;
        letter-spacing: 1px;
        text-transform: uppercase;
    }
    .chapter-icon { font-size: 52px; margin-bottom: 12px; display: block; }
    .chapter-title { font-size: 22px; font-weight: 800; margin-bottom: 6px; line-height: 1.3; }
    .chapter-subtitle { font-size: 14px; opacity: 0.8; line-height: 1.5; }

    /* ===== SCENE CARD ===== */
    .scene-card {
        background: white;
        margin: 20px;
        border-radius: 16px;
        overflow: hidden;
        box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    }
    .scene-card-header {
        background: var(--purple-pale);
        padding: 14px 18px;
        display: flex;
        align-items: center;
        gap: 10px;
        border-bottom: 1px solid #e8d9ff;
    }
    .scene-card-header span { font-size: 13px; font-weight: 700; color: var(--purple); }
    .scene-card-body { padding: 18px; }
    .scene-text { font-size: 15px; color: var(--text); line-height: 1.7; }

    /* ===== DOCTOR NOTE ===== */
    .doctor-note {
        background: #FFFBF0;
        border-left: 4px solid #FFD700;
        margin: 0 20px 20px;
        padding: 16px 18px;
        border-radius: 0 12px 12px 0;
    }
    .doctor-note-label {
        font-size: 11px;
        font-weight: 700;
        color: #B8860B;
        text-transform: uppercase;
        letter-spacing: 1px;
        margin-bottom: 6px;
        display: flex;
        align-items: center;
        gap: 6px;
    }
    .doctor-note-text { font-size: 14px; color: #555; line-height: 1.6; font-style: italic; }

    /* ===== DATA CALLOUT ===== */
    .data-callout {
        background: linear-gradient(135deg, var(--purple-pale), #e8d9ff);
        border: 2px solid var(--purple);
        border-radius: 16px;
        padding: 20px;
        margin: 0 20px 20px;
        text-align: center;
    }
    .data-callout-icon { font-size: 32px; margin-bottom: 8px; }
    .data-callout-number { font-size: 42px; font-weight: 900; color: var(--purple); line-height: 1; margin-bottom: 6px; }
    .data-callout-text { font-size: 14px; color: var(--text); line-height: 1.5; }
    .data-callout-ref { font-size: 11px; color: var(--text-light); margin-top: 6px; }

    /* ===== DECISION SECTION ===== */
    .decision-section { padding: 0 20px 20px; }
    .decision-title {
        font-size: 16px;
        font-weight: 800;
        color: var(--purple-dark);
        margin-bottom: 16px;
        display: flex;
        align-items: center;
        gap: 8px;
    }

    /* ===== FEEDBACK CARD ===== */
    .feedback-card {
        border-radius: 14px;
        padding: 18px;
        margin: 0 20px 20px;
        display: none;
        animation: slideUp 0.4s ease;
    }
    @keyframes slideUp {
        from { opacity: 0; transform: translateY(15px); }
        to { opacity: 1; transform: translateY(0); }
    }
    .feedback-card.good { background: linear-gradient(135deg, #E8F8E8, #D4F0D4); border: 2px solid #4CAF50; }
    .feedback-card.warn { background: linear-gradient(135deg, #FFF8E1, #FFF0C0); border: 2px solid #FFC107; }
    .feedback-card.info { background: linear-gradient(135deg, #E3F2FD, #BBDEFB); border: 2px solid #2196F3; }
    .feedback-icon { font-size: 28px; margin-bottom: 8px; }
    .feedback-title { font-size: 16px; font-weight: 800; margin-bottom: 6px; }
    .feedback-card.good .feedback-title { color: #2E7D32; }
    .feedback-card.warn .feedback-title { color: #E65100; }
    .feedback-card.info .feedback-title { color: #1565C0; }
    .feedback-text { font-size: 14px; line-height: 1.6; color: var(--text); }

    /* ===== QUIZ ===== */
    .quiz-option {
        background: white;
        border: 2px solid #ddd;
        color: var(--text);
        padding: 14px 18px;
        border-radius: 12px;
        font-size: 15px;
        font-weight: 600;
        cursor: pointer;
        width: 100%;
        text-align: center;
        transition: border-color 0.2s, color 0.2s;
        margin-bottom: 10px;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
        display: block;
        min-height: 50px;
    }
    .quiz-option:hover { border-color: var(--purple); color: var(--purple); }
    .quiz-option.correct { background: #E8F8E8; border-color: #4CAF50; color: #2E7D32; }
    .quiz-option.wrong { background: #FFEBEE; border-color: #F44336; color: #C62828; }
    .quiz-option:disabled { cursor: default; }

    /* ===== STAT GRID ===== */
    .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin: 0 20px 20px; }
    .stat-item {
        background: var(--purple-pale);
        border-radius: 14px;
        padding: 18px 14px;
        text-align: center;
        border: 2px solid #e8d9ff;
        transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
    }
    .stat-item:hover { border-color: var(--purple); transform: translateY(-3px); box-shadow: 0 6px 18px rgba(124,63,158,0.15); }
    .stat-item-icon { font-size: 28px; margin-bottom: 6px; }
    .stat-item-number { font-size: 26px; font-weight: 900; color: var(--purple); line-height: 1; margin-bottom: 4px; }
    .stat-item-label { font-size: 12px; color: var(--text-light); line-height: 1.4; }
    .stat-item-ref { font-size: 10px; color: #aaa; margin-top: 3px; }

    /* ===== TIMELINE ===== */
    .timeline { margin: 0 20px 20px; position: relative; padding-left: 30px; }
    .timeline::before {
        content: '';
        position: absolute;
        left: 10px; top: 0; bottom: 0;
        width: 3px;
        background: linear-gradient(to bottom, var(--purple), var(--purple-light));
        border-radius: 3px;
    }
    .timeline-item { position: relative; margin-bottom: 20px; animation: fadeIn 0.5s ease; }
    @keyframes fadeIn {
        from { opacity: 0; transform: translateX(-10px); }
        to { opacity: 1; transform: translateX(0); }
    }
    .timeline-dot {
        position: absolute;
        left: -24px; top: 4px;
        width: 14px; height: 14px;
        background: var(--purple);
        border-radius: 50%;
        border: 3px solid white;
        box-shadow: 0 0 0 2px var(--purple);
    }
    .timeline-content {
        background: white;
        border: 1px solid #e8d9ff;
        border-radius: 12px;
        padding: 14px 16px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    .timeline-day { font-size: 11px; font-weight: 700; color: var(--purple); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 4px; }
    .timeline-text { font-size: 14px; color: var(--text); line-height: 1.5; }

    /* ===== HK CHART ===== */
    .hk-chart {
        margin: 0 20px 20px;
        background: white;
        border-radius: 16px;
        padding: 20px;
        border: 2px solid #e8d9ff;
        box-shadow: 0 4px 15px rgba(0,0,0,0.06);
    }
    .hk-chart-title { font-size: 14px; font-weight: 700; color: var(--purple-dark); margin-bottom: 16px; text-align: center; }
    .month-bars { display: flex; align-items: flex-end; gap: 4px; height: 80px; margin-bottom: 8px; }
    .month-bar-wrap {
        flex: 1;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        justify-content: flex-end;
        cursor: pointer;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
    }
    .month-bar { width: 100%; border-radius: 4px 4px 0 0; transition: opacity 0.2s, transform 0.2s; min-height: 4px; }
    .month-bar.rsv { background: linear-gradient(to top, var(--purple), var(--purple-light)); }
    .month-bar.flu { background: linear-gradient(to top, #87CEEB, #B0E0FF); }
    .month-bar-wrap:hover .month-bar { opacity: 0.8; transform: scaleY(1.05); transform-origin: bottom; }
    .month-label { font-size: 9px; color: var(--text-light); margin-top: 4px; text-align: center; }
    .chart-legend { display: flex; justify-content: center; gap: 20px; margin-top: 10px; }
    .legend-item { display: flex; align-items: center; gap: 6px; font-size: 12px; color: var(--text-light); }
    .legend-dot { width: 12px; height: 12px; border-radius: 3px; }

    /* ===== BADGE ===== */
    .badge-earned {
        background: linear-gradient(135deg, #FFD700, #FFA500);
        border-radius: 16px;
        padding: 20px;
        margin: 0 20px 20px;
        text-align: center;
        box-shadow: 0 6px 20px rgba(255,165,0,0.3);
        animation: badgePop 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }
    @keyframes badgePop {
        0% { transform: scale(0.5); opacity: 0; }
        100% { transform: scale(1); opacity: 1; }
    }
    .badge-icon { font-size: 40px; margin-bottom: 6px; }
    .badge-title { font-size: 16px; font-weight: 800; color: #1a0a2e; margin-bottom: 4px; }
    .badge-desc { font-size: 13px; color: rgba(26,10,46,0.7); }

    /* ===== ENDING SCREENS ===== */
    .ending-header { padding: 40px 25px 30px; text-align: center; }
    .ending-header.good { background: linear-gradient(135deg, #2E7D32, #4CAF50); }
    .ending-header.warn { background: linear-gradient(135deg, #E65100, #FF9800); }
    .ending-header.best { background: linear-gradient(135deg, var(--purple-dark), var(--purple)); }
    .ending-icon { font-size: 64px; margin-bottom: 16px; display: block; }
    .ending-title { font-size: 24px; font-weight: 800; color: white; margin-bottom: 8px; line-height: 1.3; }
    .ending-subtitle { font-size: 15px; color: rgba(255,255,255,0.85); line-height: 1.5; }

    /* ===== FINAL SUMMARY ===== */
    .summary-section { padding: 25px 20px; background: var(--gray); }
    .summary-title { font-size: 18px; font-weight: 800; color: var(--purple-dark); margin-bottom: 16px; text-align: center; }
    .summary-item {
        background: white;
        border-radius: 12px;
        padding: 16px;
        margin-bottom: 12px;
        display: flex;
        align-items: flex-start;
        gap: 14px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.06);
    }
    .summary-item-icon { font-size: 28px; flex-shrink: 0; }
    .summary-item-number { font-size: 22px; font-weight: 900; color: var(--purple); line-height: 1; }
    .summary-item-text { font-size: 13px; color: var(--text-light); line-height: 1.5; margin-top: 3px; }

    /* ===== ACHIEVEMENTS ===== */
    .achievements-section { padding: 20px; }
    .achievements-title { font-size: 16px; font-weight: 800; color: var(--purple-dark); margin-bottom: 14px; text-align: center; }
    .achievements-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
    .achievement-item {
        background: white;
        border: 2px solid #e8d9ff;
        border-radius: 12px;
        padding: 14px 12px;
        text-align: center;
        transition: all 0.3s;
    }
    .achievement-item.earned { border-color: #FFD700; background: linear-gradient(135deg, #FFFBF0, #FFF8E1); box-shadow: 0 3px 12px rgba(255,215,0,0.2); }
    .achievement-item.locked { opacity: 0.4; filter: grayscale(1); }
    .achievement-item-icon { font-size: 28px; margin-bottom: 6px; }
    .achievement-item-name { font-size: 12px; font-weight: 700; color: var(--text); line-height: 1.3; }

    /* ===== CTA ===== */
    .cta-section { background: linear-gradient(135deg, var(--purple-dark), var(--purple)); padding: 30px 25px; text-align: center; }
    .cta-title { font-size: 18px; font-weight: 800; color: white; margin-bottom: 10px; }
    .cta-text { font-size: 14px; color: rgba(255,255,255,0.85); line-height: 1.6; margin-bottom: 20px; }
    .btn-whatsapp {
        background: #25D366;
        color: white;
        border: none;
        padding: 14px 30px;
        border-radius: 50px;
        font-size: 16px;
        font-weight: 700;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        gap: 8px;
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 4px 15px rgba(37,211,102,0.4);
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
    }
    .btn-whatsapp:hover { transform: translateY(-2px); box-shadow: 0 8px 22px rgba(37,211,102,0.5); }

    /* ===== REFERENCES ===== */
    .references-section { background: #F9F9F9; padding: 20px; }
    .ref-toggle {
        background: none;
        border: 1px solid #ddd;
        color: var(--text-light);
        padding: 10px 18px;
        border-radius: 8px;
        font-size: 13px;
        cursor: pointer;
        width: 100%;
        text-align: left;
        display: flex;
        justify-content: space-between;
        align-items: center;
        touch-action: manipulation;
        -webkit-tap-highlight-color: transparent;
    }
    .ref-content { display: none; margin-top: 12px; font-size: 11px; color: #777; line-height: 1.7; }
    .ref-content.open { display: block; }
    .ref-item { margin-bottom: 6px; }

    /* ===== FOOTER ===== */
    .footer { background: #2C2C2C; color: #aaa; padding: 25px 20px; font-size: 11px; line-height: 1.7; }
    .footer p { margin-bottom: 10px; }
    .footer-company { color: white; font-weight: 700; font-size: 13px; margin-bottom: 6px; }
    .mat-code { text-align: center; padding: 12px; background: #F5F5F5; font-size: 11px; color: #888; font-weight: 600; }

    /* ===== PARTICLES ===== */
    .particles-container {
        position: fixed;
        top: 0; left: 0;
        width: 100%; height: 100%;
        pointer-events: none;
        z-index: 9999;
        overflow: hidden;
    }
    .particle {
        position: absolute;
        width: 10px; height: 10px;
        border-radius: 50%;
        animation: particleFall 2s ease-in forwards;
    }
    @keyframes particleFall {
        0% { transform: translateY(-20px) rotate(0deg); opacity: 1; }
        100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
    }

    /* ===== PULSE ===== */
    @keyframes pulse {
        0%, 100% { transform: scale(1); }
        50% { transform: scale(1.05); }
    }
    .pulse { animation: pulse 2s ease-in-out infinite; }

    /* ===== SEPARATOR ===== */
    .sep { height: 1px; background: #eee; margin: 0 20px 20px; }

    /* ===== SYMPTOM BUBBLES ===== */
    .symptom-bubbles { display: flex; flex-wrap: wrap; gap: 8px; margin: 12px 0; }
    .symptom-bubble {
        background: #FFE8E8;
        border: 1px solid #FFB6B6;
        color: #C62828;
        font-size: 13px;
        padding: 6px 14px;
        border-radius: 20px;
        font-weight: 600;
        animation: bubbleIn 0.4s ease;
    }
    @keyframes bubbleIn {
        from { transform: scale(0); opacity: 0; }
        to { transform: scale(1); opacity: 1; }
    }
    .symptom-bubble.severe { background: #FFEBEE; border-color: #F44336; color: #B71C1C; }

    /* ===== VITAL SIGNS ===== */
    .vitals-row { display: flex; gap: 10px; margin: 12px 0; }
    .vital-box {
        flex: 1;
        background: white;
        border: 2px solid #e8d9ff;
        border-radius: 12px;
        padding: 12px 8px;
        text-align: center;
    }
    .vital-box.alert { border-color: #F44336; background: #FFEBEE; }
    .vital-icon { font-size: 20px; margin-bottom: 4px; }
    .vital-value { font-size: 18px; font-weight: 800; color: var(--purple); }
    .vital-box.alert .vital-value { color: #C62828; }
    .vital-label { font-size: 10px; color: var(--text-light); margin-top: 2px; }

    /* ===== PICU MONITOR ===== */
    .picu-monitor {
        background: #0a1628;
        border-radius: 16px;
        padding: 20px;
        margin: 0 20px 20px;
        border: 3px solid #1a3a5c;
    }
    .monitor-title { color: #4CAF50; font-size: 12px; font-weight: 700; letter-spacing: 2px; margin-bottom: 14px; text-align: center; }
    .monitor-row { display: flex; justify-content: space-between; margin-bottom: 12px; }
    .monitor-item { text-align: center; }
    .monitor-value { font-size: 22px; font-weight: 900; font-family: monospace; }
    .monitor-value.green { color: #4CAF50; }
    .monitor-value.yellow { color: #FFD700; }
    .monitor-value.red { color: #F44336; animation: blink 1s infinite; }
    @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } }
    .monitor-label { font-size: 10px; color: #4a6a8a; margin-top: 2px; letter-spacing: 1px; }
    .ecg-line { height: 40px; background: #0a1628; border-radius: 8px; overflow: hidden; position: relative; margin-top: 10px; }
    .ecg-svg { width: 100%; height: 100%; }

    /* ===== SCORE POPUP ===== */
    .score-popup {
        position: fixed;
        top: 80px; right: 20px;
        background: linear-gradient(135deg, #FFD700, #FFA500);
        color: #1a0a2e;
        padding: 10px 18px;
        border-radius: 50px;
        font-size: 16px;
        font-weight: 800;
        z-index: 1000;
        animation: scoreAnim 1.5s ease forwards;
        pointer-events: none;
    }
    @keyframes scoreAnim {
        0% { transform: translateY(0) scale(0.5); opacity: 0; }
        30% { transform: translateY(-10px) scale(1.1); opacity: 1; }
        70% { transform: translateY(-20px) scale(1); opacity: 1; }
        100% { transform: translateY(-40px) scale(0.8); opacity: 0; }
    }

    /* ===== DESKTOP CENTERING WRAPPER ===== */
    #app-wrapper {
        width: 100%;
        min-height: 100vh;
        background: #1a0a2e;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    /* ===== RESPONSIVE ===== */
    @media (max-width: 400px) {
        .chapter-title { font-size: 19px; }
        .data-callout-number { font-size: 36px; }
        .stat-item-number { font-size: 22px; }
    }
</style># A
