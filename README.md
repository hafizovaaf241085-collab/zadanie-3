const fs = require('fs');
const path = require('path');

// Содержимое вашего файла (можно также читать из внешнего .txt)
// Для удобства я скопировал текст из вашего сообщения.
// Если хотите читать из файла — раскомментируйте строки ниже и удалите многострочную строку.
const inputText = `================================================================================
ПЛАН РАБОТ НА ИСПЫТАТЕЛЬНЫЙ СРОК (3 месяца) ДЛЯ ФИНАНСОВОГО ДИРЕКТОРА
ООО "АГЕНТСТВО Р.О.С.ДОЛГЪ" (ИНН 7704724468)
!!! Без УЧЕТА УТРАТЫ ЛИЦЕНЗИИ ПКО 12.11.2025
================================================================================

... (весь ваш текст, который был в файле) ...`;

// Если хотите читать из внешнего файла, используйте:
// const inputText = fs.readFileSync('plan.txt', 'utf8');

// Преобразование текста в HTML
function textToHtml(text) {
    const lines = text.split(/\r?\n/);
    let html = '<!DOCTYPE html>\n<html lang="ru">\n<head>\n';
    html += '<meta charset="UTF-8">\n';
    html += '<meta name="viewport" content="width=device-width, initial-scale=1.0">\n';
    html += '<title>План для финансового директора | Р.О.С.Долгъ</title>\n';
    html += '<style>\n';
    html += 'body { font-family: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; line-height: 1.5; max-width: 1200px; margin: 0 auto; padding: 20px; background: #f5f7fb; color: #1e293b; }\n';
    html += '.container { background: white; border-radius: 24px; padding: 30px; box-shadow: 0 8px 20px rgba(0,0,0,0.05); }\n';
    html += 'h1 { font-size: 2rem; border-left: 5px solid #dc2626; padding-left: 20px; margin-top: 0; }\n';
    html += 'h2 { font-size: 1.5rem; margin-top: 2rem; padding-bottom: 0.5rem; border-bottom: 2px solid #e2e8f0; color: #0f172a; }\n';
    html += 'h3 { font-size: 1.25rem; margin: 1.5rem 0 0.5rem; color: #334155; }\n';
    html += '.section { margin-bottom: 2rem; }\n';
    html += '.card { background: #f8fafc; border-radius: 20px; padding: 1.2rem 1.5rem; margin: 1rem 0; border-left: 4px solid #3b82f6; }\n';
    html += 'pre { background: #1e293b; color: #e2e8f0; padding: 1rem; border-radius: 12px; overflow-x: auto; font-family: "Fira Code", monospace; }\n';
    html += 'table { width: 100%; border-collapse: collapse; margin: 1rem 0; }\n';
    html += 'th, td { border: 1px solid #cbd5e1; padding: 10px; text-align: left; vertical-align: top; }\n';
    html += 'th { background: #eef2ff; }\n';
    html += '.badge { display: inline-block; background: #dc2626; color: white; font-size: 0.75rem; padding: 0.2rem 0.6rem; border-radius: 20px; margin-right: 0.5rem; }\n';
    html += 'hr { margin: 2rem 0; border: none; height: 1px; background: linear-gradient(to right, #cbd5e1, transparent); }\n';
    html += 'footer { text-align: center; margin-top: 3rem; font-size: 0.85rem; color: #64748b; }\n';
    html += '</style>\n</head>\n<body>\n<div class="container">\n';

    let inPre = false;
    for (let line of lines) {
        // Обработка заголовков с === или --- (как в вашем файле)
        if (line.startsWith('===') || line.startsWith('---')) continue;

        // Основные заголовки уровня 1 (с "ЭТАП" или "КЛЮЧЕВЫЕ МЕТРИКИ" и т.д.)
        if (line.match(/^ЭТАП \d+\./i) || line.match(/^КЛЮЧЕВЫЕ МЕТРИКИ/i) || line.match(/^ЗОНЫ КРАСНЫХ ФЛАГОВ/i) || line.match(/^ПЛАН РАЗВИТИЯ SOFT SKILLS/i) || line.match(/^ИТОГОВАЯ РЕКОМЕНДАЦИЯ/i)) {
            html += `<h2>${escapeHtml(line)}</h2>\n`;
            continue;
        }

        // Заголовки уровня 2 (с "ДЕЙСТВИЕ", "МЕТРИКА", "КРАСНЫЙ ФЛАГ", "НАВЫК")
        if (line.match(/^ДЕЙСТВИЕ \d+\.\d+\./i) || line.match(/^МЕТРИКА \d+\./i) || line.match(/^КРАСНЫЙ ФЛАГ \d+\./i) || line.match(/^НАВЫК \d+\./i)) {
            html += `<h3>${escapeHtml(line)}</h3>\n`;
            continue;
        }

        // Обработка строк, начинающихся с "   Расшифровка:" или "   Что сделать:"
        if (line.trim().startsWith('Расшифровка:')) {
            html += `<div class="card"><strong>📖 Расшифровка:</strong> ${escapeHtml(line.replace(/^\s*Расшифровка:\s*/, ''))}</div>\n`;
            continue;
        }
        if (line.trim().startsWith('Что сделать:')) {
            html += `<div class="card"><strong>🔧 Что сделать:</strong> ${escapeHtml(line.replace(/^\s*Что сделать:\s*/, ''))}</div>\n`;
            continue;
        }
        if (line.trim().startsWith('Пояснение:')) {
            html += `<div class="card"><strong>⚠️ Пояснение:</strong> ${escapeHtml(line.replace(/^\s*Пояснение:\s*/, ''))}</div>\n`;
            continue;
        }
        if (line.trim().startsWith('Действия:')) {
            html += `<div class="card"><strong>✅ Действия:</strong> ${escapeHtml(line.replace(/^\s*Действия:\s*/, ''))}</div>\n`;
            continue;
        }
        if (line.trim().startsWith('Как освоить:')) {
            html += `<div class="card"><strong>📚 Как освоить:</strong> ${escapeHtml(line.replace(/^\s*Как освоить:\s*/, ''))}</div>\n`;
            continue;
        }

        // Маркированные списки (строки, начинающиеся с "   - " или "     - ")
        if (line.match(/^\s{2,}- /)) {
            html += `<li>${escapeHtml(line.replace(/^\s*-\s*/, ''))}</li>\n`;
            continue;
        }

        // Простые строки
        if (line.trim() !== '') {
            html += `<p>${escapeHtml(line)}</p>\n`;
        } else {
            html += `<br>\n`;
        }
    }

    html += `<footer>Сгенерировано скриптом для GitHub Pages • ${new Date().toLocaleString()}</footer>\n`;
    html += `</div>\n</body>\n</html>`;
    return html;
}

function escapeHtml(str) {
    return str.replace(/[&<>]/g, function(m) {
        if (m === '&') return '&amp;';
        if (m === '<') return '&lt;';
        if (m === '>') return '&gt;';
        return m;
    }).replace(/[\uD800-\uDBFF][\uDC00-\uDFFF]/g, function(c) {
        return c;
    });
}

// Генерация HTML
const fullHtml = textToHtml(inputText);

// Запись в файл index.html
fs.writeFileSync('index.html', fullHtml, 'utf8');
console.log('✅ index.html успешно создан!');

// Подсказка по публикации на GitHub
console.log('\n📌 Чтобы получить HTML-ссылку на GitHub:');
console.log('1. Создайте репозиторий на GitHub (например, "finance-plan")');
console.log('2. Загрузите туда этот скрипт и сгенерированный index.html');
console.log('3. В настройках репозитория включите GitHub Pages (ветка main, папка /root)');
console.log('4. Ссылка будет: https://ВАШ_ЛОГИН.github.io/НАЗВАНИЕ_РЕПОЗИТОРИЯ/');
console.log('\n💡 Если вы хотите сразу открыть локально: запустите любой HTTP-сервер, например:');
console.log('   npx serve .   или   python -m http.server 8000');
