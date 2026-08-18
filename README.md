<!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>小明的RSV之旅 | Sanofi</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

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
    </style>
</head>
<body>

<div id="app-wrapper">

<!-- Particles Container -->
<div class="particles-container" id="particles"></div>

<!-- Score Popup Container -->
<div id="scorePopupContainer"></div>

<!-- ==================== DISCLAIMER SCREEN ==================== -->
<div id="screen-disclaimer" class="screen active">
    <div class="disclaimer-logo">🏥</div>
    <div class="disclaimer-title">小明的RSV之旅</div>
    <div class="disclaimer-subtitle">沉浸式临床决策体验 · 医生视角</div>

    <div class="disclaimer-box">
        <p>
            <strong>⚠️ 重要声明</strong><br><br>
            本故事为<strong>示意性情景</strong>，用于说明真实世界RSV疾病负担数据。<br>
            <strong>非真实病例。</strong><br><br>
            所有统计数据均来自已发表的科学文献，参考文献列于页面底部。本材料仅供医疗专业人员参考，不构成临床诊疗建议。
        </p>
    </div>

    <div class="info-pills">
        <span class="info-pill">🎮 互动决策</span>
        <span class="info-pill">📊 真实数据</span>
        <span class="info-pill">🏆 成就系统</span>
        <span class="info-pill">⏱️ 约5分钟</span>
    </div>

    <button class="btn-primary pulse" id="btn-start">开始体验 →</button>
</div>

<!-- ==================== CHAPTER 1 ==================== -->
<div id="screen-ch1" class="screen">
    <div class="progress-header">
        <span class="progress-label">第1章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:10%"></div></div>
        <span class="progress-score" id="score-ch1">⭐ 0分</span>
    </div>

    <div class="chapter-header">
        <span class="chapter-tag">Chapter 1 · 第一章</span>
        <span class="chapter-icon">👶</span>
        <div class="chapter-title">意外的开始</div>
        <div class="chapter-subtitle">一个普通的门诊早晨…</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header">
            <span>🏥</span>
            <span>儿科门诊 · 上午9:15</span>
        </div>
        <div class="scene-card-body">
            <div class="scene-text">
                小明的妈妈抱着2个月大的儿子走进诊室，神情略显担忧。<br><br>
                <strong>「医生，他昨天开始有点咳嗽，今天好像有点发烧，但精神还好。」</strong><br><br>
                小明是足月顺产，出生体重3.2kg，无任何基础疾病，按时接种疫苗，家庭环境良好。
            </div>
            <div class="symptom-bubbles" style="margin-top:14px">
                <span class="symptom-bubble">🤧 轻微咳嗽</span>
                <span class="symptom-bubble">🌡️ 低热 37.8°C</span>
                <span class="symptom-bubble">😊 精神尚可</span>
                <span class="symptom-bubble">🍼 进食正常</span>
            </div>
        </div>
    </div>

    <div class="doctor-note">
        <div class="doctor-note-label">📋 临床记录</div>
        <div class="doctor-note-text">「健康足月婴儿，2个月龄，无合并症。轻微上呼吸道症状，生命体征基本稳定。」</div>
    </div>

    <div class="data-callout">
        <div class="data-callout-icon">💡</div>
        <div class="data-callout-number">72%</div>
        <div class="data-callout-text"><strong>健康婴儿悖论</strong><br>RSV住院病例中，大多数发生在<strong>健康足月婴儿</strong>中，而非高危群体</div>
        <div class="data-callout-ref">参考文献²</div>
    </div>

    <div class="decision-section">
        <div class="decision-title">🩺 您的初步判断是？</div>
        <button class="btn-choice" id="ch1-btn-A">
            <span class="choice-icon">😌</span>
            <span class="choice-text">A. 普通感冒，安抚家长，嘱咐观察，无需特殊处理</span>
        </button>
        <button class="btn-choice" id="ch1-btn-B">
            <span class="choice-icon">🔍</span>
            <span class="choice-text">B. 需要进一步评估，考虑RSV等病毒感染的可能性</span>
        </button>
        <button class="btn-choice" id="ch1-btn-C">
            <span class="choice-icon">🚑</span>
            <span class="choice-text">C. 立即转介医院进行全面评估</span>
        </button>
    </div>

    <div id="feedback-ch1" class="feedback-card">
        <div class="feedback-icon" id="fb1-icon"></div>
        <div class="feedback-title" id="fb1-title"></div>
        <div class="feedback-text" id="fb1-text"></div>
    </div>

    <div id="btn-ch1-next" style="padding:0 20px 30px; display:none">
        <button class="btn-next" id="btn-go-ch2">继续故事 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 2 ==================== -->
<div id="screen-ch2" class="screen">
    <div class="progress-header">
        <span class="progress-label">第2章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:30%"></div></div>
        <span class="progress-score" id="score-ch2">⭐ 0分</span>
    </div>

    <div class="chapter-header">
        <span class="chapter-tag">Chapter 2 · 第二章</span>
        <span class="chapter-icon">🌡️</span>
        <div class="chapter-title">病情发展</div>
        <div class="chapter-subtitle">3天后，小明再次来到诊室…</div>
    </div>

    <div class="timeline" style="margin-top:20px">
        <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-day">第1天</div>
                <div class="timeline-text">轻微咳嗽，低热 37.8°C，精神尚可</div>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot" style="background:#FF9800"></div>
            <div class="timeline-content">
                <div class="timeline-day" style="color:#E65100">第2天</div>
                <div class="timeline-text">咳嗽加重，夜间哭闹增多，进食减少</div>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot" style="background:#F44336"></div>
            <div class="timeline-content">
                <div class="timeline-day" style="color:#C62828">第3天 · 今日</div>
                <div class="timeline-text">呼吸急促，鼻翼扇动，肋间凹陷，精神萎靡</div>
            </div>
        </div>
    </div>

    <div class="scene-card">
        <div class="scene-card-header">
            <span>⚠️</span>
            <span>症状明显加重</span>
        </div>
        <div class="scene-card-body">
            <div class="vitals-row">
                <div class="vital-box alert">
                    <div class="vital-icon">💨</div>
                    <div class="vital-value">68次/分</div>
                    <div class="vital-label">呼吸频率</div>
                </div>
                <div class="vital-box alert">
                    <div class="vital-icon">🌡️</div>
                    <div class="vital-value">38.5°C</div>
                    <div class="vital-label">体温</div>
                </div>
                <div class="vital-box alert">
                    <div class="vital-icon">🩸</div>
                    <div class="vital-value">94%</div>
                    <div class="vital-label">SpO₂</div>
                </div>
            </div>
            <div class="symptom-bubbles">
                <span class="symptom-bubble severe">😰 呼吸急促</span>
                <span class="symptom-bubble severe">👃 鼻翼扇动</span>
                <span class="symptom-bubble severe">🫁 肋间凹陷</span>
                <span class="symptom-bubble severe">😴 精神萎靡</span>
            </div>
        </div>
    </div>

    <div class="doctor-note">
        <div class="doctor-note-label">📋 临床记录</div>
        <div class="doctor-note-text">「症状明显进展。呼吸频率升高，SpO₂ 94%，出现呼吸窘迫体征。需要立即评估并决定处置方案。」</div>
    </div>

    <div class="data-callout" style="background: linear-gradient(135deg, #FFF3E0, #FFE0B2); border-color: #FF9800;">
        <div class="data-callout-icon">📈</div>
        <div class="data-callout-number" style="color:#E65100">40%</div>
        <div class="data-callout-text">初次RSV感染中，高达<strong>40%</strong>会进展为<strong>下呼吸道感染(LRTI)</strong></div>
        <div class="data-callout-ref">参考文献⁵</div>
    </div>

    <div class="decision-section">
        <div class="decision-title">🚨 您的处置决定是？</div>
        <button class="btn-choice" id="ch2-btn-A">
            <span class="choice-icon">💊</span>
            <span class="choice-text">A. 开具抗生素，嘱咐回家休息，3天后复诊</span>
        </button>
        <button class="btn-choice" id="ch2-btn-B">
            <span class="choice-icon">🏥</span>
            <span class="choice-text">B. 立即安排住院，给予支持性治疗和密切监测</span>
        </button>
        <button class="btn-choice" id="ch2-btn-C">
            <span class="choice-icon">🚑</span>
            <span class="choice-text">C. 紧急转介急诊，要求立即评估和积极处理</span>
        </button>
    </div>

    <div id="feedback-ch2" class="feedback-card">
        <div class="feedback-icon" id="fb2-icon"></div>
        <div class="feedback-title" id="fb2-title"></div>
        <div class="feedback-text" id="fb2-text"></div>
    </div>

    <div id="btn-ch2-next" style="padding:0 20px 30px; display:none">
        <button class="btn-next" id="btn-go-ch3">继续故事 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 3 ==================== -->
<div id="screen-ch3" class="screen">
    <div class="progress-header">
        <span class="progress-label">第3章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:50%"></div></div>
        <span class="progress-score" id="score-ch3">⭐ 0分</span>
    </div>

    <div class="chapter-header">
        <span class="chapter-tag">Chapter 3 · 第三章</span>
        <span class="chapter-icon">🔬</span>
        <div class="chapter-title">诊断确认</div>
        <div class="chapter-subtitle">实验室结果出来了…</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header">
            <span>🧪</span>
            <span>检验报告 · 已确认</span>
        </div>
        <div class="scene-card-body">
            <div class="scene-text">小明已收入儿科病房。鼻咽拭子RSV抗原检测结果回报：</div>
            <div style="background:#E8F8E8;border:2px solid #4CAF50;border-radius:12px;padding:16px;margin-top:14px;text-align:center;">
                <div style="font-size:32px;margin-bottom:6px">✅</div>
                <div style="font-size:18px;font-weight:800;color:#2E7D32">RSV 抗原检测：阳性</div>
                <div style="font-size:13px;color:#555;margin-top:6px">呼吸道合胞病毒感染确诊</div>
            </div>
        </div>
    </div>

    <div class="doctor-note">
        <div class="doctor-note-label">📋 临床记录</div>
        <div class="doctor-note-text">「RSV感染确诊。目前给予支持性治疗：吸氧、雾化、补液。密切监测呼吸状态。」</div>
    </div>

    <div style="padding: 0 20px 20px;">
        <div class="decision-title">🧠 知识挑战：RSV疾病负担</div>
        <div style="background:var(--purple-pale);border-radius:14px;padding:18px;margin-bottom:16px;">
            <div style="font-size:15px;font-weight:700;color:var(--purple-dark);margin-bottom:14px;line-height:1.5">
                📊 RSV占5岁以下儿童急性呼吸道感染的比例是多少？
            </div>
            <button class="quiz-option" id="q1-a">30%</button>
            <button class="quiz-option" id="q1-b">60%以上</button>
            <button class="quiz-option" id="q1-c">20%</button>
        </div>
    </div>

    <div id="feedback-ch3" class="feedback-card">
        <div class="feedback-icon" id="fb3-icon"></div>
        <div class="feedback-title" id="fb3-title"></div>
        <div class="feedback-text" id="fb3-text"></div>
    </div>

    <div id="badge-data-detective" class="badge-earned" style="display:none">
        <div class="badge-icon">🔍</div>
        <div class="badge-title">🏅 成就解锁：数据侦探</div>
        <div class="badge-desc">正确识别RSV疾病负担数据</div>
    </div>

    <div class="stat-grid" style="margin-top:0">
        <div class="stat-item">
            <div class="stat-item-icon">👶</div>
            <div class="stat-item-number">>60%</div>
            <div class="stat-item-label">5岁以下儿童急性呼吸道感染</div>
            <div class="stat-item-ref">参考文献¹</div>
        </div>
        <div class="stat-item">
            <div class="stat-item-icon">🍼</div>
            <div class="stat-item-number">>80%</div>
            <div class="stat-item-label">1岁以下婴儿急性呼吸道感染</div>
            <div class="stat-item-ref">参考文献¹</div>
        </div>
        <div class="stat-item">
            <div class="stat-item-icon">🌍</div>
            <div class="stat-item-number">33.1M</div>
            <div class="stat-item-label">全球每年RSV相关LRTI病例</div>
            <div class="stat-item-ref">参考文献³</div>
        </div>
        <div class="stat-item">
            <div class="stat-item-icon">📈</div>
            <div class="stat-item-number">40%</div>
            <div class="stat-item-label">初次RSV感染进展为LRTI</div>
            <div class="stat-item-ref">参考文献⁵</div>
        </div>
    </div>

    <div id="btn-ch3-next" style="padding:0 20px 30px; display:none">
        <button class="btn-next" id="btn-go-ch4">继续故事 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 4 ==================== -->
<div id="screen-ch4" class="screen">
    <div class="progress-header">
        <span class="progress-label">第4章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:70%"></div></div>
        <span class="progress-score" id="score-ch4">⭐ 0分</span>
    </div>

    <div class="chapter-header">
        <span class="chapter-tag">Chapter 4 · 第四章</span>
        <span class="chapter-icon">🇭🇰</span>
        <div class="chapter-title">香港的现实</div>
        <div class="chapter-subtitle">查阅本地流行病学数据…</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header">
            <span>📊</span>
            <span>香港卫生防护中心 · 监测数据</span>
        </div>
        <div class="scene-card-body">
            <div class="scene-text">在等待小明病情稳定的间隙，您打开了香港卫生防护中心的RSV监测报告，想了解本地的流行情况…</div>
        </div>
    </div>

    <div class="hk-chart">
        <div class="hk-chart-title">🇭🇰 香港RSV vs 流感 全年活动度对比<sup style="font-size:10px">⁴</sup></div>
        <div class="month-bars" id="hkChart"></div>
        <div style="display:flex;justify-content:space-between;padding:0 2px;">
            <span style="font-size:9px;color:#aaa">1月</span>
            <span style="font-size:9px;color:#aaa">12月</span>
        </div>
        <div class="chart-legend">
            <div class="legend-item"><div class="legend-dot" style="background:var(--purple)"></div><span>RSV</span></div>
            <div class="legend-item"><div class="legend-dot" style="background:#87CEEB"></div><span>季节性流感</span></div>
        </div>
        <div style="background:#FFF8E1;border-radius:10px;padding:12px;margin-top:14px;font-size:13px;color:#555;line-height:1.6;">
            💡 <strong>点击图表中的月份柱状图</strong>查看详情。RSV在香港<strong>全年流行</strong>，某些年份6-10月活动度较高，但无明显固定季节性规律，与流感的季节性模式不同。
        </div>
    </div>

    <div id="hk-tooltip" style="display:none;margin:0 20px 20px;background:var(--purple-pale);border:2px solid var(--purple);border-radius:12px;padding:16px;font-size:14px;color:var(--text);line-height:1.6;animation:slideUp 0.3s ease;"></div>

    <div class="data-callout">
        <div class="data-callout-icon">🏥</div>
        <div class="data-callout-number">1.5–2.4%</div>
        <div class="data-callout-text">香港住院RSV儿童中需要<strong>PICU支持</strong>的比例，平均在重症监护室停留<strong>3天</strong></div>
        <div class="data-callout-ref">参考文献⁷⁻⁸</div>
    </div>

    <div style="padding: 0 20px 20px;">
        <div class="decision-title">🧠 知识挑战：香港RSV特点</div>
        <div style="background:var(--purple-pale);border-radius:14px;padding:18px;">
            <div style="font-size:15px;font-weight:700;color:var(--purple-dark);margin-bottom:14px;line-height:1.5">
                📅 香港RSV的流行特点是？
            </div>
            <button class="quiz-option" id="q2-a">仅在冬季流行，与流感相似</button>
            <button class="quiz-option" id="q2-b">仅在夏季流行，6-8月为高峰</button>
            <button class="quiz-option" id="q2-c">全年流行，季节性不规律，难以预测</button>
        </div>
    </div>

    <div id="feedback-ch4" class="feedback-card">
        <div class="feedback-icon" id="fb4-icon"></div>
        <div class="feedback-title" id="fb4-title"></div>
        <div class="feedback-text" id="fb4-text"></div>
    </div>

    <div id="badge-local-expert" class="badge-earned" style="display:none">
        <div class="badge-icon">🇭🇰</div>
        <div class="badge-title">🏅 成就解锁：本地专家</div>
        <div class="badge-desc">掌握香港RSV流行病学特点</div>
    </div>

    <div id="btn-ch4-next" style="padding:0 20px 30px; display:none">
        <button class="btn-next" id="btn-go-ch5">进入最终章节 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 5A: MILD ENDING ==================== -->
<div id="screen-ch5a" class="screen">
    <div class="progress-header">
        <span class="progress-label">第5章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:90%"></div></div>
        <span class="progress-score" id="score-ch5a">⭐ 0分</span>
    </div>

    <div class="ending-header good">
        <span class="ending-icon">😊</span>
        <div class="ending-title">结局A：顺利康复</div>
        <div class="ending-subtitle">早期识别，适当处置，小明恢复良好</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header"><span>📅</span><span>住院第5天</span></div>
        <div class="scene-card-body">
            <div class="scene-text">经过5天的支持性治疗，小明的呼吸状况明显改善。SpO₂恢复至98%，体温正常，进食良好，精神活泼。</div>
            <div class="vitals-row" style="margin-top:14px">
                <div class="vital-box" style="border-color:#4CAF50;background:#E8F8E8">
                    <div class="vital-icon">💨</div>
                    <div class="vital-value" style="color:#2E7D32">42次/分</div>
                    <div class="vital-label">呼吸频率</div>
                </div>
                <div class="vital-box" style="border-color:#4CAF50;background:#E8F8E8">
                    <div class="vital-icon">🌡️</div>
                    <div class="vital-value" style="color:#2E7D32">36.8°C</div>
                    <div class="vital-label">体温</div>
                </div>
                <div class="vital-box" style="border-color:#4CAF50;background:#E8F8E8">
                    <div class="vital-icon">🩸</div>
                    <div class="vital-value" style="color:#2E7D32">98%</div>
                    <div class="vital-label">SpO₂</div>
                </div>
            </div>
        </div>
    </div>

    <div class="doctor-note">
        <div class="doctor-note-label">📋 临床记录</div>
        <div class="doctor-note-text">「临床反应良好。氧饱和度持续改善，呼吸窘迫症状消退。准备安排出院，嘱咐家长注意事项。」</div>
    </div>

    <div style="background:linear-gradient(135deg,#E8F8E8,#D4F0D4);border:2px solid #4CAF50;border-radius:16px;padding:20px;margin:0 20px 20px;text-align:center;">
        <div style="font-size:40px;margin-bottom:10px">🎉</div>
        <div style="font-size:17px;font-weight:800;color:#2E7D32;margin-bottom:8px">小明顺利出院</div>
        <div style="font-size:14px;color:#555;line-height:1.6">住院5天后，小明完全康复出院。<br>早期识别和适当的支持性治疗带来了良好的临床结局。</div>
    </div>

    <div id="badge-early-recognizer" class="badge-earned" style="display:none">
        <div class="badge-icon">⚡</div>
        <div class="badge-title">🏅 成就解锁：早期识别者</div>
        <div class="badge-desc">您的临床判断帮助小明及时获得治疗</div>
    </div>

    <div style="padding:0 20px 30px;">
        <button class="btn-next" id="btn-ch5a-final">查看总结与成就 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 5B: SEVERE ENDING ==================== -->
<div id="screen-ch5b" class="screen">
    <div class="progress-header">
        <span class="progress-label">第5章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:90%"></div></div>
        <span class="progress-score" id="score-ch5b">⭐ 0分</span>
    </div>

    <div class="ending-header warn">
        <span class="ending-icon">🚨</span>
        <div class="ending-title">结局B：重症病程</div>
        <div class="ending-subtitle">病情延误，小明需要PICU支持</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header"><span>⚠️</span><span>急诊室 · 深夜</span></div>
        <div class="scene-card-body">
            <div class="scene-text">由于处置延误，小明在家中病情急剧恶化。家长深夜紧急送往急诊室时，小明出现严重呼吸窘迫，SpO₂跌至85%，需要立即干预。</div>
            <div class="symptom-bubbles" style="margin-top:12px">
                <span class="symptom-bubble severe">😰 严重呼吸窘迫</span>
                <span class="symptom-bubble severe">🫁 重度支气管炎</span>
                <span class="symptom-bubble severe">💉 需要吸氧支持</span>
            </div>
        </div>
    </div>

    <div class="picu-monitor">
        <div class="monitor-title">⚕ PICU 监护室 · 实时监测</div>
        <div class="monitor-row">
            <div class="monitor-item">
                <div class="monitor-value red" id="hr-value">158</div>
                <div class="monitor-label">HR bpm</div>
            </div>
            <div class="monitor-item">
                <div class="monitor-value yellow" id="spo2-value">91%</div>
                <div class="monitor-label">SpO₂</div>
            </div>
            <div class="monitor-item">
                <div class="monitor-value yellow" id="rr-value">72</div>
                <div class="monitor-label">RR /min</div>
            </div>
            <div class="monitor-item">
                <div class="monitor-value green">37.9</div>
                <div class="monitor-label">TEMP °C</div>
            </div>
        </div>
        <div class="ecg-line">
            <svg class="ecg-svg" viewBox="0 0 300 40" preserveAspectRatio="none">
                <polyline points="0,20 20,20 25,5 30,35 35,20 55,20 60,5 65,35 70,20 90,20 95,5 100,35 105,20 125,20 130,5 135,35 140,20 160,20 165,5 170,35 175,20 195,20 200,5 205,35 210,20 230,20 235,5 240,35 245,20 265,20 270,5 275,35 280,20 300,20"
                      fill="none" stroke="#4CAF50" stroke-width="1.5"/>
            </svg>
        </div>
    </div>

    <div class="data-callout" style="background:linear-gradient(135deg,#FFEBEE,#FFCDD2);border-color:#F44336;">
        <div class="data-callout-icon">🏥</div>
        <div class="data-callout-number" style="color:#C62828">1.5–2.4%</div>
        <div class="data-callout-text">香港住院RSV儿童中需要<strong>PICU支持</strong>的比例<br>平均PICU停留时间：<strong>3天</strong></div>
        <div class="data-callout-ref">参考文献⁷⁻⁸</div>
    </div>

    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-dot" style="background:#F44336"></div>
            <div class="timeline-content">
                <div class="timeline-day" style="color:#C62828">PICU第1天</div>
                <div class="timeline-text">高流量吸氧，密切监测，静脉补液</div>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot" style="background:#FF9800"></div>
            <div class="timeline-content">
                <div class="timeline-day" style="color:#E65100">PICU第2天</div>
                <div class="timeline-text">SpO₂逐渐改善，呼吸频率下降，病情趋于稳定</div>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot" style="background:#4CAF50"></div>
            <div class="timeline-content">
                <div class="timeline-day" style="color:#2E7D32">PICU第3天</div>
                <div class="timeline-text">病情稳定，转回普通儿科病房继续观察</div>
            </div>
        </div>
    </div>

    <div style="background:linear-gradient(135deg,#FFF8E1,#FFF0C0);border:2px solid #FFC107;border-radius:16px;padding:20px;margin:0 20px 20px;text-align:center;">
        <div style="font-size:36px;margin-bottom:10px">💛</div>
        <div style="font-size:16px;font-weight:800;color:#E65100;margin-bottom:8px">小明最终康复</div>
        <div style="font-size:14px;color:#555;line-height:1.6">经过3天PICU支持和后续普通病房治疗，小明最终康复出院。<br><br><strong>即使重症病例也可以在适当的重症监护下康复，但预防和早期识别至关重要。</strong></div>
    </div>

    <div style="padding:0 20px 30px;">
        <button class="btn-next" id="btn-ch5b-final">查看总结与成就 →</button>
    </div>
</div>

<!-- ==================== CHAPTER 5C: OPTIMAL ENDING ==================== -->
<div id="screen-ch5c" class="screen">
    <div class="progress-header">
        <span class="progress-label">第5章</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:90%"></div></div>
        <span class="progress-score" id="score-ch5c">⭐ 0分</span>
    </div>

    <div class="ending-header best">
        <span class="ending-icon">⭐</span>
        <div class="ending-title">结局C：最优管理</div>
        <div class="ending-subtitle">最佳临床决策，小明获得最优治疗结局</div>
    </div>

    <div class="scene-card" style="margin-top:20px">
        <div class="scene-card-header"><span>✅</span><span>最优临床路径</span></div>
        <div class="scene-card-body">
            <div class="scene-text">您在第一次就诊时就高度警觉，及时安排住院评估，迅速确诊RSV，并给予规范的支持性治疗。小明的病情在早期干预下得到有效控制。</div>
            <div style="margin-top:14px">
                <div style="display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid #eee;">
                    <span style="font-size:20px">✅</span>
                    <span style="font-size:14px;color:#333">第1天：识别高风险症状，安排住院评估</span>
                </div>
                <div style="display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid #eee;">
                    <span style="font-size:20px">✅</span>
                    <span style="font-size:14px;color:#333">第2天：RSV确诊，开始规范支持性治疗</span>
                </div>
                <div style="display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid #eee;">
                    <span style="font-size:20px">✅</span>
                    <span style="font-size:14px;color:#333">第3天：病情稳定，无需PICU转介</span>
                </div>
                <div style="display:flex;align-items:center;gap:10px;padding:10px 0;">
                    <span style="font-size:20px">🎉</span>
                    <span style="font-size:14px;color:#2E7D32;font-weight:700">第3天：顺利出院，无并发症</span>
                </div>
            </div>
        </div>
    </div>

    <div class="doctor-note">
        <div class="doctor-note-label">📋 临床记录</div>
        <div class="doctor-note-text">「及时干预，适当管理。出色的临床病程。您对健康婴儿RSV疾病负担的临床意识发挥了关键作用。」</div>
    </div>

    <div style="background:linear-gradient(135deg,var(--purple-pale),#e8d9ff);border:2px solid var(--purple);border-radius:16px;padding:20px;margin:0 20px 20px;text-align:center;">
        <div style="font-size:40px;margin-bottom:10px">🏆</div>
        <div style="font-size:17px;font-weight:800;color:var(--purple-dark);margin-bottom:8px">最优临床结局</div>
        <div style="font-size:14px;color:#555;line-height:1.6">仅住院3天，无并发症，无需PICU。<br><strong>您对RSV疾病负担的认知，让小明获得了最好的治疗结局。</strong></div>
    </div>

    <div id="badge-clinical-master" class="badge-earned" style="display:none">
        <div class="badge-icon">🏆</div>
        <div class="badge-title">🏅 成就解锁：临床大师</div>
        <div class="badge-desc">完成最优临床决策路径，获得最佳结局</div>
    </div>

    <div style="padding:0 20px 30px;">
        <button class="btn-next" id="btn-ch5c-final">查看总结与成就 →</button>
    </div>
</div>

<!-- ==================== FINAL SCREEN ==================== -->
<div id="screen-final" class="screen">
    <div class="progress-header">
        <span class="progress-label">完成</span>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:100%"></div></div>
        <span class="progress-score" id="score-final">⭐ 0分</span>
    </div>

    <div style="background:linear-gradient(160deg,#1a0a2e 0%,#3d1a6e 50%,#7C3F9E 100%);padding:35px 25px;text-align:center;color:white;">
        <div style="font-size:52px;margin-bottom:14px">📖</div>
        <div style="font-size:22px;font-weight:800;margin-bottom:10px;line-height:1.3">小明的故事结束了</div>
        <div style="font-size:15px;opacity:0.85;line-height:1.6">但RSV的挑战仍在继续…<br>每一个健康婴儿都可能是下一个小明</div>
    </div>

    <div class="summary-section">
        <div class="summary-title">📊 关键数据回顾</div>
        <div class="summary-item">
            <div class="summary-item-icon">🌍</div>
            <div class="summary-item-content">
                <div class="summary-item-number">33.1百万</div>
                <div class="summary-item-text">全球每年5岁以下儿童RSV相关急性LRTI病例<sup>³</sup></div>
            </div>
        </div>
        <div class="summary-item">
            <div class="summary-item-icon">👶</div>
            <div class="summary-item-content">
                <div class="summary-item-number">>60% / >80%</div>
                <div class="summary-item-text">RSV占5岁以下儿童 / 1岁以下婴儿急性呼吸道感染的比例<sup>¹</sup></div>
            </div>
        </div>
        <div class="summary-item">
            <div class="summary-item-icon">🏥</div>
            <div class="summary-item-content">
                <div class="summary-item-number">大多数</div>
                <div class="summary-item-text">RSV住院病例发生在健康足月婴儿中，而非高危群体<sup>²</sup></div>
            </div>
        </div>
        <div class="summary-item">
            <div class="summary-item-icon">🇭🇰</div>
            <div class="summary-item-content">
                <div class="summary-item-number">全年流行</div>
                <div class="summary-item-text">香港RSV无明显固定季节性，全年均需保持警觉<sup>⁴</sup></div>
            </div>
        </div>
        <div class="summary-item">
            <div class="summary-item-icon">🚨</div>
            <div class="summary-item-content">
                <div class="summary-item-number">1.5–2.4%</div>
                <div class="summary-item-text">香港住院RSV儿童需要PICU支持，平均停留3天<sup>⁷⁻⁸</sup></div>
            </div>
        </div>
    </div>

    <div class="achievements-section">
        <div class="achievements-title">🏅 您的成就</div>
        <div class="achievements-grid" id="achievements-display"></div>
    </div>

    <div style="background:var(--purple-pale);padding:20px;">
        <div style="text-align:center;margin-bottom:16px;">
            <div style="font-size:22px;font-weight:800;color:var(--purple-dark);">您的最终得分</div>
            <div style="font-size:52px;font-weight:900;color:var(--purple);margin:8px 0;" id="final-score-display">0</div>
            <div style="font-size:14px;color:var(--text-light);" id="final-score-comment">感谢参与！</div>
        </div>
    </div>

    <div class="cta-section">
        <div class="cta-title">💬 了解更多RSV预防资讯</div>
        <div class="cta-text">更多临床证据与见解即将推出。<br>通过WhatsApp与我们联系，获取更多RSV预防资源和指导。</div>
        <button class="btn-whatsapp"><span>💬</span> 联系我们</button>
    </div>

    <div style="padding:20px;">
        <button class="btn-replay" id="btn-replay">🔄 重新体验，探索不同结局</button>
    </div>

    <div class="references-section">
        <button class="ref-toggle" id="ref-toggle-btn">
            <span>📚 参考文献</span>
            <span id="ref-arrow">▼</span>
        </button>
        <div class="ref-content" id="ref-content">
            <div class="ref-item">1. Piedimonte G, et al. Pediatr Rev. 2014;35(12):519-530</div>
            <div class="ref-item">2. 数据来自不同研究和不同年份。ªIncludes children ≥1 year of age. bData may include preterm healthy infants. cMay include infants with comorbid conditions. dLow weight born at term infants were excluded from the healthy cohort. (Hall CB, et al. Pediatrics. 2013;132(2):e341-e348; Arriola CS, et al. J Pediatric Infect Dis Soc. 2020;9(5):587-595; Rha B, et al. Pediatrics. 2020;146(1):e20193611; Hill H, et al. STOP RSV. Presented at: ESPID, May 8-12 2023; Sanchez-Luna M, et al. Curr Med Res Opin. 2016;32(4):693-698; Demont C, et al. BMC Infect Dis. 2021;21(1):730; Van Summeren JJGT, et al. BMC Infect Dis. 2021;21(1):705; Hartmann K, et al. J Infect Dis. 2022;jiac137; Yildiz GS, et al. Presented at: ESPID, May 8-12 2023; Ren L, Influenza Other Respir Viruses. 2023;17(8):e13180; Kobayashi, et al. Ped Intl. 2021;0:1-7; Buchan SA, et al. J Pediatric Infect Dis Soc. 2023;12(7):421-430; Ferone EA, et al. J Pediatr (Rio J). 2014;90(1):42-49; Bandeira T, Influenza Other Respir Viruses. 2023;17(1):e13066; Homaira N et al. Epidemiol Infect. 2016;144(8):1612-1621; Mazela J, Jackowska T, Viruses. 2024;16(5):704.)</div>
            <div class="ref-item">3. Shi T, et al. Lancet. 2017;390(10098):946-958</div>
            <div class="ref-item">4. Centre for Health Protection. Communicable Diseases Watch. 2025;21(1):1-5; 21(8):58-62</div>
            <div class="ref-item">5. Esposito S, et al. Front Immunol. 2022;13:880368</div>
            <div class="ref-item">6. Mazur NI, et al. Lancet Infect Dis. 2022;S1473-3099(22)00291-2</div>
            <div class="ref-item">7. Hon KL et al. Journal of Critical Care 2012;27:464-468</div>
            <div class="ref-item">8. Leung TF et al. Infection 2014;42:343-350</div>
        </div>
    </div>

    <div class="mat-code">MAT-HK-XXXXXXX-1.0-09/2026</div>

    <div class="footer">
        <p><strong style="color:white">免责声明</strong></p>
        <p>本故事为示意性情景，用于说明真实世界RSV疾病负担数据。非真实病例。本材料仅为医学和科学信息分享/交流目的而准备。在使用此处提及的任何产品之前，请参阅最新的完整本地处方信息。</p>
        <p>根据适用的隐私法以及赛诺菲针对医疗保健专业人员的全球隐私声明，我们提醒您，您有权访问、纠正和/或反对处理您的个人数据，以及要求个人数据的可携性、删除和/或限制处理。</p>
        <div style="margin-top:16px;padding-top:16px;border-top:1px solid #444;">
            <div class="footer-company">Sanofi Hong Kong Limited</div>
            <p>1/F & Section 212 on 2/F, AXA Southside,<br>38 Wong Chuk Hang Road, Wong Chuk Hang, H.K.<br>Tel: (852) 2506 8333</p>
            <p style="margin-top:10px;color:#666;">Copyright © 2006 - 2026 Sanofi - All rights reserved.</p>
        </div>
    </div>
</div>

</div><!-- end app-wrapper -->

<script>
    // ===== GAME STATE =====
    var gameState = {
        score: 0,
        ch1Choice: null,
        ch2Choice: null,
        ch3Correct: false,
        ch4Correct: false,
        badges: { earlyRecognizer: false, dataDetective: false, localExpert: false, clinicalMaster: false },
        ending: null
    };

    // ===== SCREEN MANAGEMENT =====
    function showScreen(id) {
        document.querySelectorAll('.screen').forEach(function(s) {
            s.classList.remove('active');
        });
        var el = document.getElementById(id);
        if (el) {
            el.classList.add('active');
            window.scrollTo(0, 0);
        }
        updateAllScores();
    }

    function startGame() {
        gameState = {
            score: 0,
            ch1Choice: null,
            ch2Choice: null,
            ch3Correct: false,
            ch4Correct: false,
            badges: { earlyRecognizer: false, dataDetective: false, localExpert: false, clinicalMaster: false },
            ending: null
        };
        showScreen('screen-ch1');
    }

    function updateAllScores() {
        var s = '⭐ ' + gameState.score + '分';
        ['ch1','ch2','ch3','ch4','ch5a','ch5b','ch5c','final'].forEach(function(id) {
            var el = document.getElementById('score-' + id);
            if (el) el.textContent = s;
        });
    }

    function addScore(pts) {
        gameState.score += pts;
        updateAllScores();
        showScorePopup('+' + pts + '分');
    }

    function showScorePopup(text) {
        var popup = document.createElement('div');
        popup.className = 'score-popup';
        popup.textContent = text;
        document.getElementById('scorePopupContainer').appendChild(popup);
        setTimeout(function() { if (popup.parentNode) popup.parentNode.removeChild(popup); }, 1500);
    }

    // ===== PARTICLES =====
    function launchParticles() {
        var colors = ['#7C3F9E','#FFD700','#FF69B4','#87CEEB','#90EE90','#FFA500'];
        var container = document.getElementById('particles');
        for (var i = 0; i < 30; i++) {
            (function(idx) {
                setTimeout(function() {
                    var p = document.createElement('div');
                    p.className = 'particle';
                    p.style.left = Math.random() * 100 + '%';
                    p.style.top = '-10px';
                    p.style.background = colors[Math.floor(Math.random() * colors.length)];
                    var sz = (6 + Math.random() * 8) + 'px';
                    p.style.width = sz;
                    p.style.height = sz;
                    p.style.animationDuration = (1.5 + Math.random()) + 's';
                    p.style.animationDelay = (Math.random() * 0.5) + 's';
                    container.appendChild(p);
                    setTimeout(function() { if (p.parentNode) p.parentNode.removeChild(p); }, 3000);
                }, idx * 60);
            })(i);
        }
    }

    // ===== DISABLE BUTTONS HELPER =====
    function disableChoiceButtons(screenId) {
        var screen = document.getElementById(screenId);
        if (!screen) return;
        var btns = screen.querySelectorAll('.btn-choice');
        btns.forEach(function(b) {
            b.disabled = true;
            b.style.opacity = '0.6';
            b.style.cursor = 'default';
        });
    }

    function disableQuizButtons(ids) {
        ids.forEach(function(id) {
            var el = document.getElementById(id);
            if (el) { el.disabled = true; el.style.cursor = 'default'; }
        });
    }

    function scrollToElement(id) {
        setTimeout(function() {
            var el = document.getElementById(id);
            if (el) el.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }, 300);
    }

    // ===== CHAPTER 1 =====
    function ch1Decision(choice) {
        if (gameState.ch1Choice) return;
        gameState.ch1Choice = choice;
        disableChoiceButtons('screen-ch1');

        var fb = document.getElementById('feedback-ch1');
        var icon = document.getElementById('fb1-icon');
        var title = document.getElementById('fb1-title');
        var text = document.getElementById('fb1-text');

        if (choice === 'A') {
            fb.className = 'feedback-card warn';
            icon.textContent = '⚠️';
            title.textContent = '需要更多警觉';
            text.textContent = '虽然轻微症状常见，但2个月大的婴儿出现呼吸道症状时需要保持高度警觉。研究显示，大多数RSV住院病例发生在健康足月婴儿中——这正是"健康婴儿悖论"。单纯观察可能错过早期干预的时机。';
        } else if (choice === 'B') {
            fb.className = 'feedback-card good';
            icon.textContent = '✅';
            title.textContent = '临床判断良好';
            text.textContent = '正确！对于2个月大的婴儿，即使症状轻微，也应考虑RSV等病毒感染的可能性。高达40%的初次RSV感染会进展为下呼吸道感染。进一步评估是明智的选择。';
            addScore(20);
        } else {
            fb.className = 'feedback-card info';
            icon.textContent = '🏥';
            title.textContent = '谨慎的选择';
            text.textContent = '对于症状轻微的婴儿，立即转介可能过于积极，但体现了对婴儿RSV风险的重视。在门诊进行初步评估后再决定是否转介，通常是更合适的流程。';
            addScore(10);
        }

        fb.style.display = 'block';
        document.getElementById('btn-ch1-next').style.display = 'block';
        scrollToElement('btn-ch1-next');
    }

    // ===== CHAPTER 2 =====
    function ch2Decision(choice) {
        if (gameState.ch2Choice) return;
        gameState.ch2Choice = choice;
        disableChoiceButtons('screen-ch2');

        var fb = document.getElementById('feedback-ch2');
        var icon = document.getElementById('fb2-icon');
        var title = document.getElementById('fb2-title');
        var text = document.getElementById('fb2-text');

        if (choice === 'A') {
            fb.className = 'feedback-card warn';
            icon.textContent = '❌';
            title.textContent = '处置不当';
            text.textContent = '抗生素对RSV等病毒感染无效。SpO₂ 94%、呼吸频率68次/分、肋间凹陷——这些都是需要住院的明确指征。延误处置将导致病情进一步恶化，增加PICU风险。';
        } else if (choice === 'B') {
            fb.className = 'feedback-card good';
            icon.textContent = '✅';
            title.textContent = '正确处置！';
            text.textContent = '非常好！SpO₂ 94%和明显的呼吸窘迫体征是住院的明确指征。及时住院给予支持性治疗（吸氧、雾化、补液）是RSV管理的标准方案，有助于避免病情进一步恶化。';
            addScore(30);
        } else {
            fb.className = 'feedback-card good';
            icon.textContent = '✅';
            title.textContent = '积极处置';
            text.textContent = '鉴于明显的呼吸窘迫体征，紧急转介急诊是合理的选择。SpO₂ 94%和肋间凹陷提示需要立即评估和干预。您的临床判断保护了小明。';
            addScore(25);
        }

        fb.style.display = 'block';
        document.getElementById('btn-ch2-next').style.display = 'block';
        scrollToElement('btn-ch2-next');
    }

    // ===== CHAPTER 3 QUIZ =====
    function answerQuiz(result, btnId) {
        disableQuizButtons(['q1-a','q1-b','q1-c']);

        var btn = document.getElementById(btnId);
        var fb = document.getElementById('feedback-ch3');
        var icon = document.getElementById('fb3-icon');
        var title = document.getElementById('fb3-title');
        var text = document.getElementById('fb3-text');

        if (result === 'correct') {
            btn.classList.add('correct');
            fb.className = 'feedback-card good';
            icon.textContent = '🎉';
            title.textContent = '答对了！';
            text.textContent = 'WHO数据显示，RSV占5岁以下儿童急性呼吸道感染的60%以上，在1岁以下婴儿中更超过80%。RSV是儿科呼吸道疾病的主要病原体。';
            gameState.ch3Correct = true;
            gameState.badges.dataDetective = true;
            addScore(25);
            launchParticles();
            setTimeout(function() {
                var badge = document.getElementById('badge-data-detective');
                if (badge) badge.style.display = 'block';
            }, 500);
        } else {
            btn.classList.add('wrong');
            var correct = document.getElementById('q1-b');
            if (correct) correct.classList.add('correct');
            fb.className = 'feedback-card info';
            icon.textContent = '💡';
            title.textContent = '正确答案是60%以上';
            text.textContent = 'WHO数据显示，RSV占5岁以下儿童急性呼吸道感染的60%以上，在1岁以下婴儿中更超过80%。这一数据远超许多医生的预期，体现了RSV在儿科呼吸道疾病中的主导地位。';
        }

        fb.style.display = 'block';
        document.getElementById('btn-ch3-next').style.display = 'block';
        scrollToElement('btn-ch3-next');
    }

    // ===== CHAPTER 4 QUIZ =====
    function answerQuiz2(result, btnId) {
        disableQuizButtons(['q2-a','q2-b','q2-c']);

        var btn = document.getElementById(btnId);
        var fb = document.getElementById('feedback-ch4');
        var icon = document.getElementById('fb4-icon');
        var title = document.getElementById('fb4-title');
        var text = document.getElementById('fb4-text');

        if (result === 'correct') {
            btn.classList.add('correct');
            fb.className = 'feedback-card good';
            icon.textContent = '🎉';
            title.textContent = '完全正确！';
            text.textContent = '香港卫生防护中心监测数据显示，RSV在香港全年流行，某些年份6-10月活动度较高，但无明显固定季节性规律。这与季节性流感的规律性季节高峰形成鲜明对比，意味着临床医生全年都需要保持对RSV的警觉。';
            gameState.ch4Correct = true;
            gameState.badges.localExpert = true;
            addScore(25);
            launchParticles();
            setTimeout(function() {
                var badge = document.getElementById('badge-local-expert');
                if (badge) badge.style.display = 'block';
            }, 500);
        } else {
            btn.classList.add('wrong');
            var correct = document.getElementById('q2-c');
            if (correct) correct.classList.add('correct');
            fb.className = 'feedback-card info';
            icon.textContent = '💡';
            title.textContent = '正确答案：全年流行，季节性不规律';
            text.textContent = '香港RSV监测数据显示，RSV全年均有流行，无明显固定季节性。这与流感的规律性季节高峰不同，提示临床医生在任何季节都不应忽视RSV的可能性。';
        }

        fb.style.display = 'block';
        document.getElementById('btn-ch4-next').style.display = 'block';
        scrollToElement('btn-ch4-next');
    }

    // ===== HK CHART =====
    function buildHKChart() {
        var months = ['1','2','3','4','5','6','7','8','9','10','11','12'];
        var rsvData = [35,30,28,32,45,70,85,90,80,65,40,35];
        var fluData = [80,75,60,30,20,15,10,12,15,25,50,75];
        var maxVal = 90;
        var tooltips = [
            '1月：RSV活动度中等，全年均需警觉',
            '2月：RSV持续流行，无明显季节性低谷',
            '3月：RSV活动度相对较低',
            '4月：RSV活动度开始上升',
            '5月：RSV活动度升高，进入活跃期',
            '6月：RSV活动度显著升高，部分年份出现高峰',
            '7月：RSV高活动期，某些年份达到峰值',
            '8月：RSV活动度最高，与流感形成鲜明对比',
            '9月：RSV仍处于高活动期',
            '10月：RSV活动度开始下降',
            '11月：RSV活动度回落，流感开始上升',
            '12月：流感进入高峰，RSV仍有流行'
        ];

        var container = document.getElementById('hkChart');
        if (!container) return;
        container.innerHTML = '';

        months.forEach(function(m, i) {
            var wrap = document.createElement('div');
            wrap.className = 'month-bar-wrap';

            var rsvBar = document.createElement('div');
            rsvBar.className = 'month-bar rsv';
            rsvBar.style.height = (rsvData[i] / maxVal * 70) + 'px';

            var fluBar = document.createElement('div');
            fluBar.className = 'month-bar flu';
            fluBar.style.height = (fluData[i] / maxVal * 70) + 'px';
            fluBar.style.marginTop = '2px';

            var label = document.createElement('div');
            label.className = 'month-label';
            label.textContent = m + '月';

            wrap.appendChild(rsvBar);
            wrap.appendChild(fluBar);
            wrap.appendChild(label);

            (function(month, tip, rsv, flu) {
                wrap.addEventListener('click', function() {
                    var tooltip = document.getElementById('hk-tooltip');
                    if (tooltip) {
                        tooltip.style.display = 'block';
                        tooltip.innerHTML = '<strong>📅 ' + month + '月</strong><br>' + tip +
                            '<br><br>🟣 RSV活动度：' + rsv + '%　🔵 流感活动度：' + flu + '%';
                    }
                });
            })(m, tooltips[i], rsvData[i], fluData[i]);

            container.appendChild(wrap);
        });
    }

    // ===== CHAPTER 5 ROUTING =====
    function goToChapter5() {
        var ch1 = gameState.ch1Choice;
        var ch2 = gameState.ch2Choice;

        if (ch2 === 'B' && ch1 === 'B') {
            gameState.ending = 'C';
            gameState.badges.clinicalMaster = true;
            gameState.badges.earlyRecognizer = true;
            addScore(30);
            showScreen('screen-ch5c');
            setTimeout(function() {
                var badge = document.getElementById('badge-clinical-master');
                if (badge) badge.style.display = 'block';
                launchParticles();
            }, 600);
        } else if (ch2 === 'A') {
            gameState.ending = 'B';
            showScreen('screen-ch5b');
            startPICUMonitor();
        } else {
            gameState.ending = 'A';
            gameState.badges.earlyRecognizer = true;
            addScore(15);
            showScreen('screen-ch5a');
            setTimeout(function() {
                var badge = document.getElementById('badge-early-recognizer');
                if (badge) badge.style.display = 'block';
                launchParticles();
            }, 600);
        }
    }

    // ===== PICU MONITOR =====
    function startPICUMonitor() {
        var hrEl = document.getElementById('hr-value');
        var spo2El = document.getElementById('spo2-value');
        var rrEl = document.getElementById('rr-value');
        if (!hrEl) return;
        var tick = 0;
        var interval = setInterval(function() {
            tick++;
            if (tick > 20) { clearInterval(interval); return; }
            hrEl.textContent = 158 + Math.floor(Math.random() * 10 - 5);
            spo2El.textContent = (91 + Math.floor(Math.random() * 4 - 2)) + '%';
            rrEl.textContent = 72 + Math.floor(Math.random() * 6 - 3);
        }, 1500);
    }

    // ===== FINAL SCREEN =====
    function goToFinal() {
        showScreen('screen-final');
        buildAchievements();
        updateFinalScore();
        launchParticles();
    }

    function buildAchievements() {
        var allBadges = [
            { key: 'earlyRecognizer', icon: '⚡', name: '早期识别者' },
            { key: 'dataDetective', icon: '🔍', name: '数据侦探' },
            { key: 'localExpert', icon: '🇭🇰', name: '本地专家' },
            { key: 'clinicalMaster', icon: '🏆', name: '临床大师' }
        ];
        var grid = document.getElementById('achievements-display');
        if (!grid) return;
        grid.innerHTML = '';
        allBadges.forEach(function(b) {
            var item = document.createElement('div');
            item.className = 'achievement-item ' + (gameState.badges[b.key] ? 'earned' : 'locked');
            item.innerHTML = '<div class="achievement-item-icon">' + b.icon + '</div><div class="achievement-item-name">' + b.name + '</div>';
            grid.appendChild(item);
        });
    }

    function updateFinalScore() {
        var el = document.getElementById('final-score-display');
        var comment = document.getElementById('final-score-comment');
        if (el) el.textContent = gameState.score + '分';
        var msg = '';
        if (gameState.score >= 100) msg = '🏆 卓越！您是RSV临床专家！';
        else if (gameState.score >= 70) msg = '⭐ 优秀！您对RSV疾病负担有深入认识';
        else if (gameState.score >= 40) msg = '👍 良好！建议重新体验探索更多路径';
        else msg = '💡 感谢参与！建议重新体验了解更多';
        if (comment) comment.textContent = msg;
    }

    // ===== BIND ALL EVENTS =====
    function bindEvents() {
        // Start button
        var btnStart = document.getElementById('btn-start');
        if (btnStart) btnStart.addEventListener('click', startGame);

        // Chapter 1 choices
        var ch1A = document.getElementById('ch1-btn-A');
        var ch1B = document.getElementById('ch1-btn-B');
        var ch1C = document.getElementById('ch1-btn-C');
        if (ch1A) ch1A.addEventListener('click', function() { ch1Decision('A'); });
        if (ch1B) ch1B.addEventListener('click', function() { ch1Decision('B'); });
        if (ch1C) ch1C.addEventListener('click', function() { ch1Decision('C'); });

        // Chapter 1 next
        var btnGoCh2 = document.getElementById('btn-go-ch2');
        if (btnGoCh2) btnGoCh2.addEventListener('click', function() { showScreen('screen-ch2'); });

        // Chapter 2 choices
        var ch2A = document.getElementById('ch2-btn-A');
        var ch2B = document.getElementById('ch2-btn-B');
        var ch2C = document.getElementById('ch2-btn-C');
        if (ch2A) ch2A.addEventListener('click', function() { ch2Decision('A'); });
        if (ch2B) ch2B.addEventListener('click', function() { ch2Decision('B'); });
        if (ch2C) ch2C.addEventListener('click', function() { ch2Decision('C'); });

        // Chapter 2 next
        var btnGoCh3 = document.getElementById('btn-go-ch3');
        if (btnGoCh3) btnGoCh3.addEventListener('click', function() { showScreen('screen-ch3'); });

        // Chapter 3 quiz
        var q1a = document.getElementById('q1-a');
        var q1b = document.getElementById('q1-b');
        var q1c = document.getElementById('q1-c');
        if (q1a) q1a.addEventListener('click', function() { answerQuiz('wrong', 'q1-a'); });
        if (q1b) q1b.addEventListener('click', function() { answerQuiz('correct', 'q1-b'); });
        if (q1c) q1c.addEventListener('click', function() { answerQuiz('wrong', 'q1-c'); });

        // Chapter 3 next
        var btnGoCh4 = document.getElementById('btn-go-ch4');
        if (btnGoCh4) btnGoCh4.addEventListener('click', function() {
            showScreen('screen-ch4');
            buildHKChart();
        });

        // Chapter 4 quiz
        var q2a = document.getElementById('q2-a');
        var q2b = document.getElementById('q2-b');
        var q2c = document.getElementById('q2-c');
        if (q2a) q2a.addEventListener('click', function() { answerQuiz2('wrong', 'q2-a'); });
        if (q2b) q2b.addEventListener('click', function() { answerQuiz2('wrong', 'q2-b'); });
        if (q2c) q2c.addEventListener('click', function() { answerQuiz2('correct', 'q2-c'); });

        // Chapter 4 next
        var btnGoCh5 = document.getElementById('btn-go-ch5');
        if (btnGoCh5) btnGoCh5.addEventListener('click', goToChapter5);

        // Ending screens → final
        var ch5aFinal = document.getElementById('btn-ch5a-final');
        var ch5bFinal = document.getElementById('btn-ch5b-final');
        var ch5cFinal = document.getElementById('btn-ch5c-final');
        if (ch5aFinal) ch5aFinal.addEventListener('click', goToFinal);
        if (ch5bFinal) ch5bFinal.addEventListener('click', goToFinal);
        if (ch5cFinal) ch5cFinal.addEventListener('click', goToFinal);

        // Replay
        var btnReplay = document.getElementById('btn-replay');
        if (btnReplay) btnReplay.addEventListener('click', function() { showScreen('screen-disclaimer'); });

        // References toggle
        var refToggle = document.getElementById('ref-toggle-btn');
        if (refToggle) refToggle.addEventListener('click', function() {
            var content = document.getElementById('ref-content');
            var arrow = document.getElementById('ref-arrow');
            if (content.classList.contains('open')) {
                content.classList.remove('open');
                arrow.textContent = '▼';
            } else {
                content.classList.add('open');
                arrow.textContent = '▲';
            }
        });
    }

    // ===== INIT =====
    document.addEventListener('DOMContentLoaded', function() {
        bindEvents();
        showScreen('screen-disclaimer');
    });
</script>
</body>
</html>
