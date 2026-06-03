<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>План работ | Финансовый директор | Агентство Р.О.С.Долгъ</title>
    <style>
        /* RESET & БАЗОВЫЕ СТИЛИ (совместимо с почтовыми клиентами) */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f0f4fa;
            font-family: 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            line-height: 1.45;
            color: #1a2634;
            padding: 24px 16px;
        }

        /* ГЛАВНЫЙ КОНТЕЙНЕР — адаптивная ширина */
        .container {
            max-width: 1280px;
            margin: 0 auto;
            background: #ffffff;
            border-radius: 36px;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.15);
            overflow: hidden;
            padding: 32px 28px 48px;
        }

        /* 1. СОВРЕМЕННЫЙ ГРАДИЕНТНЫЙ ЗАГОЛОВОК С ПРОЗРАЧНОСТЬЮ */
        .gradient-title {
            font-size: 2.2rem;
            font-weight: 800;
            letter-spacing: -0.02em;
            line-height: 1.25;
            margin-bottom: 12px;
            background: linear-gradient(135deg, #0B2B5E, #1A4A8B, #6C3C9E, #E68A2E);
            background-size: 180% 180%;
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: gradientShift 6s ease infinite;
            text-shadow: 0 2px 5px rgba(0,0,0,0.03);
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .subhead {
            font-size: 1.1rem;
            color: #2c3e66;
            border-left: 4px solid #E68A2E;
            padding-left: 18px;
            margin: 16px 0 24px 0;
            font-weight: 500;
        }

        .company-badge {
            background: #f1f5f9;
            display: inline-block;
            padding: 8px 20px;
            border-radius: 40px;
            font-size: 0.9rem;
            font-weight: 500;
            margin-bottom: 28px;
            color: #1e3a6b;
            letter-spacing: 0.3px;
        }
        .company-badge span {
            font-weight: 700;
            color: #E68A2E;
        }

        /* 2. КАРТОЧКИ ЭТАПОВ (анимация при наведении) */
        .stages-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 28px;
            margin: 48px 0 56px;
        }
        .stage-card {
            flex: 1 1 300px;
            background: #ffffff;
            border-radius: 28px;
            padding: 28px 22px;
            box-shadow: 0 12px 28px rgba(0, 0, 0, 0.05);
            transition: all 0.3s cubic-bezier(0.2, 0, 0, 1);
            border: 1px solid rgba(0, 0, 0, 0.04);
            position: relative;
            overflow: hidden;
        }
        .stage-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 28px 38px -16px rgba(0, 30, 60, 0.2);
            border-color: rgba(230, 138, 46, 0.3);
        }
        .stage-number {
            font-size: 3.2rem;
            font-weight: 800;
            background: linear-gradient(120deg, #eceff5, #e2e8f0);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            line-height: 1;
            margin-bottom: 12px;
        }
        .stage-title {
            font-size: 1.65rem;
            font-weight: 700;
            margin: 8px 0 12px;
            color: #0f2b3f;
            letter-spacing: -0.3px;
        }
        .stage-duration {
            display: inline-block;
            background: #eef2ff;
            padding: 4px 14px;
            border-radius: 30px;
            font-size: 0.75rem;
            font-weight: 600;
            color: #E68A2E;
            margin-bottom: 20px;
        }
        .stage-list {
            list-style: none;
            margin-top: 8px;
        }
        .stage-list li {
            padding: 8px 0 6px 24px;
            position: relative;
            font-size: 0.95rem;
            color: #2d3e5a;
            border-bottom: 1px dashed #e9edf2;
        }
        .stage-list li:last-child {
            border-bottom: none;
        }
        .stage-list li::before {
            content: "▹";
            position: absolute;
            left: 0;
            color: #E68A2E;
            font-weight: bold;
        }

        /* 3. СЕТКА ИНСТРУМЕНТОВ (теги) */
        .tools-section {
            margin: 48px 0 52px;
        }
        .section-caption {
            font-size: 1.6rem;
            font-weight: 700;
            margin-bottom: 20px;
            background: linear-gradient(145deg, #1f2f47, #2b4c7c);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: inline-block;
        }
        .tags-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 14px;
            margin-top: 16px;
        }
        .tool-tag {
            background: #f2f5fc;
            padding: 8px 18px;
            border-radius: 48px;
            font-weight: 500;
            font-size: 0.85rem;
            color: #1e3a6b;
            transition: all 0.2s;
            border: 1px solid #e0e7f0;
            backdrop-filter: blur(2px);
            letter-spacing: 0.3px;
        }
        .tool-tag:hover {
            background: #E68A2E;
            color: white;
            transform: scale(1.03);
            border-color: #E68A2E;
            box-shadow: 0 4px 10px rgba(230,138,46,0.2);
        }

        /* 4. ПРИМЕРЫ КЕЙСОВ (выделенные блоки) */
        .cases-section {
            margin: 48px 0 52px;
            background: linear-gradient(110deg, #f9fcff 0%, #f3f7fe 100%);
            border-radius: 32px;
            padding: 28px 24px;
        }
        .cases-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 24px;
            margin-top: 24px;
        }
        .case-item {
            background: white;
            border-radius: 24px;
            padding: 22px 22px;
            flex: 1 1 240px;
            border-left: 6px solid #E68A2E;
            box-shadow: 0 8px 18px rgba(0,0,0,0.02);
            transition: all 0.25s ease;
        }
        .case-item:hover {
            transform: translateX(5px);
            box-shadow: 0 18px 28px -12px rgba(0,0,0,0.1);
        }
        .case-title {
            font-weight: 800;
            font-size: 1.25rem;
            color: #0C4A6E;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .case-title span {
            font-size: 1.5rem;
        }
        .case-desc {
            font-size: 0.9rem;
            color: #2c4962;
            line-height: 1.4;
        }

        /* ДОПОЛНИТЕЛЬНЫЙ АКЦЕНТ */
        .highlight-stat {
            background: #1f2f47;
            color: white;
            border-radius: 28px;
            padding: 20px 28px;
            margin: 35px 0 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
        }
        .stat-text {
            font-weight: 600;
            font-size: 1rem;
        }
        .stat-number {
            font-size: 1.8rem;
            font-weight: 800;
            color: #F6B17E;
            letter-spacing: -0.5px;
        }

        /* АДАПТИВНОСТЬ (мобильные устройства) */
        @media (max-width: 780px) {
            .container {
                padding: 20px 16px;
            }
            .gradient-title {
                font-size: 1.7rem;
            }
            .stage-title {
                font-size: 1.4rem;
            }
            .section-caption {
                font-size: 1.4rem;
            }
            .stage-card {
                flex: 1 1 100%;
            }
            .tool-tag {
                font-size: 0.75rem;
                padding: 6px 14px;
            }
            .case-item {
                flex: 1 1 100%;
            }
            .highlight-stat {
                flex-direction: column;
                align-items: flex-start;
                gap: 12px;
            }
        }

        /* дополнительная стилизация для чистой иерархии */
        hr {
            margin: 24px 0;
            border: none;
            height: 2px;
            background: linear-gradient(90deg, #E68A2E, #cbd5e1, transparent);
        }

        footer {
            margin-top: 48px;
            font-size: 0.75rem;
            text-align: center;
            color: #6c7e97;
            border-top: 1px solid #ecf3f9;
            padding-top: 24px;
        }

        /* эффект для кнопок/ссылкок (при желании) */
        a {
            text-decoration: none;
        }
    </style>
</head>
<body>
<div class="container">
    <!-- шапка с названием и ИНН -->
    <div class="company-badge">
        🏢 ООО "АГЕНТСТВО Р.О.С.ДОЛГЪ" · ИНН <span>7704724468</span>
    </div>

    <!-- градиентный заголовок с эффектом прозрачности текста -->
    <h1 class="gradient-title">
        План работ <br>на испытательный срок<br>3 месяца для финансового директора
    </h1>
    <div class="subhead">
        Системное управление финансами, снижение рисков, прозрачность и контроль
    </div>

    <!-- КАРТОЧКИ ЭТАПОВ (с анимацией при наведении) -->
    <div class="stages-grid">
        <!-- ЭТАП 1 -->
        <div class="stage-card">
            <div class="stage-number">01</div>
            <div class="stage-title">Погружение и аудит</div>
            <div class="stage-duration">📅 2 недели</div>
            <ul class="stage-list">
                <li>Анализ структуры портфеля долгов</li>
                <li>Оценка казначейской функции</li>
                <li>Аудит себестоимости взыскания</li>
                <li>Проверка рисков (правовых и операционных)</li>
            </ul>
        </div>

        <!-- ЭТАП 2 -->
        <div class="stage-card">
            <div class="stage-number">02</div>
            <div class="stage-title">Сокращение OPEX</div>
            <div class="stage-duration">📅 6 недель</div>
            <ul class="stage-list">
                <li>Внедрение скользящего кассового плана</li>
                <li>Бонусная схема для коллекторов</li>
                <li>Переговоры с банками (инкассация/эквайринг)</li>
                <li>Контроль издержек и эффективность взыскания</li>
            </ul>
        </div>

        <!-- ЭТАП 3 -->
        <div class="stage-card">
            <div class="stage-number">03</div>
            <div class="stage-title">Системная настройка</div>
            <div class="stage-duration">📅 12 недель</div>
            <ul class="stage-list">
                <li>Качество корпоративной отчетности</li>
                <li>Увязка стратегии и ресурсов</li>
                <li>Остановка "токсичных" портфелей</li>
                <li>Оптимизация налогообложения</li>
            </ul>
        </div>
    </div>

    <!-- СЕТКА ИНСТРУМЕНТОВ (теги) -->
    <div class="tools-section">
        <div class="section-caption">⚙️ Ключевые инструменты и компетенции</div>
        <div class="tags-grid">
            <span class="tool-tag">📊 Казначейство</span>
            <span class="tool-tag">📉 Бюджетирование</span>
            <span class="tool-tag">🏦 Банковские комиссии</span>
            <span class="tool-tag">📈 Бонусная матрица</span>
            <span class="tool-tag">🧾 Налоговая оптимизация</span>
            <span class="tool-tag">📑 Управленческий учёт</span>
            <span class="tool-tag">⚖️ Риск-менеджмент</span>
            <span class="tool-tag">🔄 Кассовый план</span>
            <span class="tool-tag">📌 Долговой портфель</span>
            <span class="tool-tag">📎 Отчётность МСФО</span>
        </div>
    </div>

    <!-- ПРИМЕРЫ КЕЙСОВ (ВЫДЕЛЕННЫЕ БЛОКИ) -->
    <div class="cases-section">
        <div style="font-size: 1.4rem; font-weight: 700; margin-bottom: 6px;">🏆 Реальные кейсы внедрения</div>
        <div style="color: #4a627a; margin-bottom: 12px;">Опыт финансового директора в коллекторском бизнесе</div>
        <div class="cases-grid">
            <div class="case-item">
                <div class="case-title"><span>📉</span> Снижение OPEX на 18%</div>
                <div class="case-desc">Оптимизация эквайринга и пересмотр тарифов инкассации в топ-5 банках → экономия 4,2 млн руб/год.</div>
            </div>
            <div class="case-item">
                <div class="case-title"><span>📊</span> Кассовый разрыв устранён</div>
                <div class="case-desc">Внедрение скользящего кассового плана за 3 недели, повышение ликвидности на 27%.</div>
            </div>
            <div class="case-item">
                <div class="case-title"><span>🎯</span> Рост взыскания +14%</div>
                <div class="case-desc">Новая KPI-модель для коллекторов при сохранении фонда оплаты труда.</div>
            </div>
            <div class="case-item">
                <div class="case-title"><span>🧾</span> Налоговая безопасность</div>
                <div class="case-desc">Оптимизация налога на прибыль и снижение рисков доначислений (экономия 9% налоговой нагрузки).</div>
            </div>
        </div>
    </div>

    <!-- ДОПОЛНИТЕЛЬНЫЙ БЛОК АКЦЕНТНОЙ СТАТИСТИКИ (визуальная иерархия) -->
    <div class="highlight-stat">
        <div class="stat-text">🎯 Целевые результаты за 3 месяца:</div>
        <div class="stat-number">Повышение EBITDA на 12-15%</div>
        <div class="stat-text">+ Полная прозрачность денежного потока</div>
    </div>

    <!-- 3-й уровень: демонстрация контроля рисков и связка с портфелями (подчеркивание компетенций) -->
    <hr>
    <div style="display: flex; flex-wrap: wrap; justify-content: space-between; gap: 20px; margin: 20px 0 8px;">
        <div style="flex:1; min-width: 180px;">
            <h4 style="color: #E68A2E; margin-bottom: 12px;">📌 Качество активов</h4>
            <p style="font-size: 0.9rem; color: #2a405c;">Оценка портфелей перед покупкой, stop-листы "токсичных" цессий, повышение IRR на 5-7%.</p>
        </div>
        <div style="flex:1; min-width: 180px;">
            <h4 style="color: #E68A2E; margin-bottom: 12px;">📐 Отчётность для СД</h4>
            <p style="font-size: 0.9rem; color: #2a405c;">Дашборды с ключевыми метриками (NPV, поступления, комиссии). Еженедельный контроль.</p>
        </div>
        <div style="flex:1; min-width: 180px;">
            <h4 style="color: #E68A2E; margin-bottom: 12px;">⚙️ Автоматизация</h4>
            <p style="font-size: 0.9rem; color: #2a405c;">Внедрение легковесного BI и шаблонов для казначейства, снижение ручного труда на 30%.</p>
        </div>
    </div>

    <!-- акцентные элементы: сроки и важные вехи -->
    <div style="background: #fefaf5; border-radius: 28px; margin: 35px 0 20px; padding: 18px 25px; display: flex; flex-wrap: wrap; justify-content: space-between; align-items: center;">
        <div><span style="font-weight: 800;">📆 Этап 1 (2 нед.)</span> → анализ as is</div>
        <div><span style="font-weight: 800;">⚡ Этап 2 (6 нед.)</span> → снижение затрат</div>
        <div><span style="font-weight: 800;">🏛️ Этап 3 (12 нед.)</span> → устойчивая модель</div>
        <div><span style="background:#E68A2E20; padding: 4px 14px; border-radius: 60px;">🔑 KPI: рост сборов + ликвидность</span></div>
    </div>

    <!-- футер (для полноты email-блока) -->
    <footer>
        © 2025 ООО "АГЕНТСТВО Р.О.С.ДОЛГЪ" · Финансовая стратегия на испытательный срок<br>
        Документ разработан для финансового директора, повышение эффективности и контроль рисков.
    </footer>
</div>
</body>
</html>
