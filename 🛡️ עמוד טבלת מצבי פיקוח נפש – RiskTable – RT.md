## 🛡️ עמוד טבלת מצבי פיקוח נפש – **RiskTable – RT**

📅 לועזי: **Friday, 28.11.2025**
📅 עברי: **ח׳ בכסלו תשפ״ו** ([Hebcal][1])
⏰ שעה נוכחית (ישראל, UTC+2): **19:50**

---

### 🎯 מה ביקשת?

עמוד אינטרנטי נוסף בתוך **LifeGuard – LG**, שכל כולו **טבלה מסודרת**:
🟢 מתי מותר / חובה לחלל שבת להצלת חיים
🔴 מתי בדרך־כלל אסור, כי אין פיקוח נפש

העמוד הבא הוא קובץ HTML מוכן לשמירה, למשל בשם:
`cases.html` או `lifeguard-table.html` בתוך מאגר **LifeGuard**.

---

## 🧾 קובץ HTML לעמוד טבלת מצבי פיקוח נפש

העתק והדבק לקובץ חדש במאגר (`cases.html` לדוגמה):

```html
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <title>LifeGuard – טבלת מצבי פיקוח נפש</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="description" content="טבלת מצבי פיקוח נפש בשבת – מתי חובה לחלל שבת להצלת חיים ומתי אין היתר. כלי לימוד וכיס במערכת LifeGuard – LG." />
  <style>
    :root {
      --bg: #040714;
      --bg-card: #0e1424;
      --accent: #ffcc33;
      --accent-soft: #ffd96633;
      --accent-strong: #ffb600;
      --text-main: #f7f7ff;
      --text-muted: #b6b9d5;
      --danger: #ff4d6a;
      --ok: #4be3a2;
      --border-soft: #262c44;
      --shadow-soft: 0 18px 45px rgba(0, 0, 0, 0.7);
      --radius-xl: 24px;
      --radius-lg: 18px;
      --radius-pill: 999px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: radial-gradient(circle at top, #202a4a 0, #050814 45%, #000000 100%);
      color: var(--text-main);
      min-height: 100vh;
      padding: 32px 12px;
      display: flex;
      justify-content: center;
    }

    .page {
      width: 100%;
      max-width: 1200px;
      margin: 0 auto;
      background: linear-gradient(135deg, #050814f0, #050814ee);
      border-radius: 32px;
      border: 1px solid #ffffff18;
      box-shadow: var(--shadow-soft);
      padding: 26px 18px 22px;
      backdrop-filter: blur(20px);
    }

    @media (min-width: 900px) {
      .page {
        padding: 30px 26px 24px;
      }
    }

    .header {
      margin-bottom: 20px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
    }

    .badge {
      padding: 6px 14px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--accent-soft);
      background: radial-gradient(circle at top left, #ffcc3344, #000000aa);
      font-size: 12px;
      letter-spacing: 0.03em;
      text-transform: uppercase;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .title {
      font-size: clamp(26px, 3.4vw, 34px);
      font-weight: 800;
      letter-spacing: 0.03em;
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: baseline;
    }

    .title span.highlight {
      background: linear-gradient(135deg, #ffdd55, #ffb347, #ffd966);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .subtitle {
      font-size: 14px;
      color: var(--text-muted);
      max-width: 720px;
      line-height: 1.6;
    }

    .meta-row {
      margin-top: 4px;
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      font-size: 12px;
      color: var(--text-muted);
    }

    .meta-pill {
      padding: 5px 12px;
      border-radius: var(--radius-pill);
      background: #ffffff08;
      border: 1px solid #ffffff18;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .table-wrap {
      margin-top: 18px;
      background: var(--bg-card);
      border-radius: var(--radius-xl);
      border: 1px solid var(--border-soft);
      overflow: hidden;
      box-shadow: 0 12px 30px rgba(0, 0, 0, 0.65);
    }

    .table-header {
      padding: 12px 16px;
      border-bottom: 1px solid #ffffff1a;
      background: linear-gradient(135deg, #161c33, #101628);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      font-size: 13px;
    }

    .table-header h2 {
      font-size: 16px;
      display: flex;
      gap: 6px;
      align-items: center;
    }

    .legend {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      font-size: 11px;
      color: var(--text-muted);
    }

    .legend span {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      padding: 3px 8px;
      border-radius: var(--radius-pill);
      background: #ffffff08;
      border: 1px solid #ffffff15;
    }

    .dot-ok,
    .dot-danger,
    .dot-gray {
      width: 8px;
      height: 8px;
      border-radius: 999px;
    }

    .dot-ok { background: var(--ok); }
    .dot-danger { background: var(--danger); }
    .dot-gray { background: #9ca0b8; }

    .table-scroll {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      min-width: 780px;
      font-size: 13px;
    }

    thead {
      background: #111729;
    }

    th, td {
      padding: 9px 10px;
      text-align: right;
      vertical-align: top;
      border-bottom: 1px solid #1b2138;
    }

    th {
      font-weight: 600;
      color: #fbeec0;
      position: sticky;
      top: 0;
      background: #111729;
      z-index: 1;
    }

    tbody tr:nth-child(odd) {
      background: #060918;
    }

    tbody tr:nth-child(even) {
      background: #080d1c;
    }

    tbody tr:hover {
      background: #131a32;
    }

    td small {
      color: var(--text-muted);
      display: block;
      margin-top: 2px;
      line-height: 1.4;
    }

    .col-num {
      width: 34px;
      text-align: center;
      color: #c6c9e6;
      font-weight: 600;
    }

    .badge-ok,
    .badge-maybe,
    .badge-no {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 3px 9px;
      border-radius: var(--radius-pill);
      font-size: 11px;
      font-weight: 600;
    }

    .badge-ok {
      background: #03241a;
      color: #9af2c9;
      border: 1px solid #33d3a5;
    }

    .badge-maybe {
      background: #241703;
      color: #ffd27a;
      border: 1px solid #ffb347;
    }

    .badge-no {
      background: #260612;
      color: #ff9bb0;
      border: 1px solid #ff4d6a;
    }

    .note-box {
      margin-top: 14px;
      padding: 10px 12px;
      border-radius: var(--radius-lg);
      background: #160c2050;
      border: 1px solid #bb86fc55;
      font-size: 12px;
      color: #f2e2ff;
      line-height: 1.6;
    }

    .note-box strong {
      color: #ffdd55;
    }

    .footer {
      margin-top: 20px;
      padding-top: 12px;
      border-top: 1px solid #ffffff24;
      font-size: 12px;
      color: var(--text-muted);
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .footer-links {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    .footer a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 500;
    }

    .footer a:hover {
      text-decoration: underline;
    }

    .hashtags {
      font-size: 11px;
      opacity: 0.86;
    }

    .rap {
      margin-top: 10px;
      padding: 8px 10px;
      border-radius: var(--radius-lg);
      background: #00000080;
      border: 1px dashed #ffffff35;
      white-space: pre-line;
      line-height: 1.7;
    }
  </style>
</head>
<body>
  <div class="page">
    <header class="header">
      <div class="badge-row">
        <div class="badge">🛡️ LifeGuard – LG · RiskTable – RT</div>
        <div class="badge">פיקוח נפש דוחה שבת · טבלת מצבים</div>
      </div>

      <h1 class="title">
        טבלת מצבי
        <span class="highlight">פיקוח נפש בשבת</span>
      </h1>

      <p class="subtitle">
        הטבלה מרכזת מצבים רפואיים ודחופים, ומסמנת מתי <strong>חובה</strong> לחלל שבת להצלת חיים,
        ומתי בדרך־כלל אין היתר. בשטח – תמיד מצילים חיים קודם, ורק אחר כך שואלים.
      </p>

      <div class="meta-row">
        <div class="meta-pill">📅 28.11.2025 · ח׳ בכסלו תשפ״ו</div>
        <div class="meta-pill">⏰ 19:50 · שעון ישראל</div>
        <div class="meta-pill">📂 חלק ממערכת LifeGuard – LG</div>
      </div>
    </header>

    <section class="table-wrap">
      <div class="table-header">
        <h2>📊 מתי מותר / חובה לחלל שבת – ומתי אסור</h2>
        <div class="legend">
          <span><span class="dot-ok"></span> חובה/מותר לחלל שבת</span>
          <span><span class="dot-danger"></span> בדרך־כלל אסור</span>
          <span><span class="dot-gray"></span> תלוי־מצב / להתייעץ בזמן שאינו חירום</span>
        </div>
      </div>

      <div class="table-scroll">
        <table>
          <thead>
            <tr>
              <th class="col-num">#</th>
              <th>מצב</th>
              <th>דוגמאות</th>
              <th>הגדרת פיקוח נפש</th>
              <th>פעולות מותרות בשבת</th>
              <th>הערות / קו מנחה</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="col-num">1</td>
              <td>איבוד הכרה / חוסר תגובה</td>
              <td>
                אדם שוכב ואינו מגיב, נשימה לא סדירה, התעלפות ממושכת.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש ודאי</span>
                <small>חובה לפעול מיד.</small>
              </td>
              <td>
                📞 הזעקת אמבולנס, 🚗 נסיעה לבית חולים, 💡 הדלקת אורות, 📱 שימוש בטלפון.
              </td>
              <td>
                כל שנייה חשובה. לא מחכים לראות “אם יעבור לבד”.
              </td>
            </tr>

            <tr>
              <td class="col-num">2</td>
              <td>כאבים חזקים בחזה / חשד להתקף לב</td>
              <td>
                לחץ בחזה, הקרנה ליד שמאל/לסת, הזעה קרה, קוצר נשימה.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
                <small>נחשב מצב מסוכן.</small>
              </td>
              <td>
                הזמנת ניידת טיפול נמרץ, נסיעה דחופה, שימוש בתרופות שניתנו להנחיה.
              </td>
              <td>
                לא מנסים “להירגע קצת” – פועלים מיד כמו באמצע השבוע.
              </td>
            </tr>

            <tr>
              <td class="col-num">3</td>
              <td>קוצר נשימה חמור / חנק</td>
              <td>
                קושי לנשום, צפצופים חריפים, סימני חנק, צבע פנים משתנה.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
              </td>
              <td>
                קריאה לעזרה, פעולות החייאה בסיסיות אם יודעים, שימוש במכשירים רפואיים.
              </td>
              <td>
                מצב מסוכן בכל גיל. תמיד מצילים חיים גם בשבת.
              </td>
            </tr>

            <tr>
              <td class="col-num">4</td>
              <td>דימום חמור / טראומה מתאונה</td>
              <td>
                תאונת דרכים, נפילה מגובה, דימום שאינו נעצר, פציעת ראש חזקה.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
              </td>
              <td>
                עצירת דימום, הזמנת אמבולנס, נסיעה דחופה, שימוש בציוד רפואי.
              </td>
              <td>
                גם אם הנפגע מדבר – ייתכן נזק פנימי. מתייחסים כמסוכן.
              </td>
            </tr>

            <tr>
              <td class="col-num">5</td>
              <td>סימני שבץ מוחי</td>
              <td>
                חולשה פתאומית בפנים/יד/רגל, דיבור משובש, ראייה כפולה או בלבול.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
              </td>
              <td>
                פינוי מיד לבית חולים, כל שימוש נדרש ברכב / טלפון / ציוד.
              </td>
              <td>
                יש חלון זמן קצר לטיפול. חובה להזדרז אפילו יותר מבחול.
              </td>
            </tr>

            <tr>
              <td class="col-num">6</td>
              <td>חום גבוה מאוד בתינוקות וילדים</td>
              <td>
                תינוק קטן עם חום גבוה, חולשה קיצונית, קושי לשתות/לנשום.
              </td>
              <td>
                <span class="badge-ok">לעיתים פיקוח נפש</span>
                <small>בפרט בגיל רך.</small>
              </td>
              <td>
                יצירת קשר עם רופא / מוקד רפואי, נסיעה לקבלת טיפול לפי ההנחיה.
              </td>
              <td>
                עדיף לדבר מראש עם רופא באמצע השבוע איך לפעול במצבים שכיחים.
              </td>
            </tr>

            <tr>
              <td class="col-num">7</td>
              <td>יולדת</td>
              <td>
                צירים סדירים, ירידת מים, כאבים חזקים לפני לידה.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
              </td>
              <td>
                נסיעה מוסדרת לבית חולים, הדלקת אור, שימוש בטלפון וכדומה.
              </td>
              <td>
                ההלכה רואה ביולדת מצב של פיקוח נפש – מטפלים בה כראוי.
              </td>
            </tr>

            <tr>
              <td class="col-num">8</td>
              <td>חולה כרוני במצב החמרה</td>
              <td>
                חולה לב, סוכרת, נשימה וכו׳ – מחמיר באופן משמעותי בשבת.
              </td>
              <td>
                <span class="badge-ok">לעיתים פיקוח נפש</span>
              </td>
              <td>
                מותר לבצע כל פעולה שהרופא הנחה להצלת חייו או מניעת סכנה.
              </td>
              <td>
                מומלץ לקבל מראש הוראות כתובות מהרופא והפוסק לשבת.
              </td>
            </tr>

            <tr>
              <td class="col-num">9</td>
              <td>סכנת נפש נפשית</td>
              <td>
                אדם שמביע רצון לפגוע בעצמו, התנהגות מסכנת חיים, חוסר שליטה מוחלט.
              </td>
              <td>
                <span class="badge-ok">פיקוח נפש</span>
              </td>
              <td>
                פנייה מיידית לגורמי טיפול וחירום, שימוש בכל אמצעי תקשורת ותנועה.
              </td>
              <td>
                גם במצב נפשי – דין פיקוח נפש, ומצווה להציל בכל דרך.
              </td>
            </tr>

            <tr>
              <td class="col-num">10</td>
              <td>ספק סכנה ממשי</td>
              <td>
                לא ברור עד כמה המצב חמור, אך יש יסוד לחוש לסכנת חיים.
              </td>
              <td>
                <span class="badge-ok">ספק פיקוח נפש = פיקוח נפש</span>
              </td>
              <td>
                נוהגים כאילו ודאי פיקוח נפש – פועלים מיד.
              </td>
              <td>
                כלל יסוד: בספק – מצילים חיים, לא מחמירים על חשבון האדם.
              </td>
            </tr>

            <tr>
              <td class="col-num">11</td>
              <td>מחלה קלה (צינון, כאב גרון קל וכדומה)</td>
              <td>
                מצונן, כאב גרון פשוט, תחושת חולשה קלה ללא סימני סכנה.
              </td>
              <td>
                <span class="badge-no">אין פיקוח נפש בדרך־כלל</span>
              </td>
              <td>
                נמנעים מחילול שבת. אפשר להשתמש באמצעים המותרים בשבת לפי ההלכה.
              </td>
              <td>
                מבררים מראש עם רב כיצד לנהוג בתרופות ופעולות קלות בשבת.
              </td>
            </tr>

            <tr>
              <td class="col-num">12</td>
              <td>טיפול אלקטיבי / בדיקה שניתן לדחות</td>
              <td>
                בדיקות שגרה, טיפולים מתוכננים, צילום שאפשר לחכות אתו.
              </td>
              <td>
                <span class="badge-no">אין פיקוח נפש</span>
              </td>
              <td>
                קובעים לזמן אחר, לא מחללים שבת.
              </td>
              <td>
                אם יש שינוי והופכת לסכנה – עוברת לקטגוריית פיקוח נפש.
              </td>
            </tr>

            <tr>
              <td class="col-num">13</td>
              <td>כאבים בינוניים ללא סימן סכנה</td>
              <td>
                כאב ראש חזק, כאבי גב, שן כואבת ללא נפיחות חמורה או חום גבוה.
              </td>
              <td>
                <span class="badge-maybe">לא פיקוח נפש, אך גורם סבל</span>
              </td>
              <td>
                משתמשים בהיתרים המוכרים בשבת (כדורים שהונחו מראש, גוי וכדומה) לפי פסק הלכה.
              </td>
              <td>
                נושא להדרכה מוקדמת מרב – לא בזמן החירום.
              </td>
            </tr>

            <tr>
              <td class="col-num">14</td>
              <td>ילד מפוחד / חבלה קלה</td>
              <td>
                מכה קלה, שפשוף, דמעות מפחד ללא סימני סכנה גופנית.
              </td>
              <td>
                <span class="badge-maybe">בדרך־כלל לא פיקוח נפש</span>
              </td>
              <td>
                עידוד, טיפול בסיסי מותר, ללא נסיעות ופעולות חשמל כבדות.
              </td>
              <td>
                אם מופיעים סימני סכנה – המצב משתנה ומטפלים כפיקוח נפש.
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>

    <div class="note-box">
      ⚠️ <strong>תזכורת הלכתית–מעשית:</strong><br />
      הטבלה היא סיכום עקרונות. בכל מצב חירום בשטח – <strong>מצילים חיים מיד</strong>, מזעיקים כוחות רפואה וחירום, ועושים כל מה שנדרש כמו באמצע השבוע.  
      שאלות הלכתיות פרטיות ודיוקים – מתאימים לזמן רגוע, יחד עם רופא ופוסק.
    </div>

    <footer class="footer">
      <div>
        ✡️ פסוק יסוד לפיקוח נפש:  
        <strong>“וָחַי בָּהֶם”</strong> – שתהא חיותך על־ידי המצוות ולא שימות בהן (ויקרא י״ח, ה׳).
      </div>

      <div class="footer-links">
        <span>© 2025 LifeGuard – LG · RiskTable – RT</span>
        <span>•</span>
        <a href="https://github.com/AnLoMinus/LifeGuard" target="_blank" rel="noopener">
          מאגר GitHub: LifeGuard
        </a>
        <span>•</span>
        <a href="https://anlominus.github.io/LifeGuard/" target="_blank" rel="noopener">
          אתר ראשי: LifeGuard – LG
        </a>
        <span>•</span>
        <span>Created for קדושת החיים · AnLoMinus x LifeGuard</span>
      </div>

      <div class="rap">
        🎤 LifeGuard – Rap Hook (Heb/Eng Mix)  
        LifeGuard mode כשיש ניצוץ של סכנה,  
        שוברים את השגרה רק כדי לשמור נשמה.  
        שבת זה אור – אבל החיים מעל הכול,  
        Pikuach Nefesh first – ככה מצילים את הכול.
      </div>

      <div class="hashtags">
        #LifeGuard #RiskTable #PikuachNefesh #פיקוח_נפש #שבת #הלכה_למעשה #AnLoMinus
      </div>
    </footer>
  </div>
</body>
</html>
```

---

### 🧱 איך לשלב את העמוד באתר LifeGuard – LG

1. שמור את הקובץ כ־`cases.html` במאגר `LifeGuard`.
2. בעמוד הראשי (`index.html`) אפשר להוסיף כפתור/קישור:

   ```html
   <a class="btn-ghost" href="cases.html">📊 טבלת מצבי פיקוח נפש</a>
   ```

---

### ✨ משפט קודש מסכם

> **“לֹא תַעֲמֹד עַל דַּם רֵעֶךָ”** (ויקרא י״ט, ט״ז) –
> כל מי שמציל נפש אחת, מחיה עולם שלם.

🔢 **מספר המידות:** 18

[1]: https://www.hebcal.com/converter?utm_source=chatgpt.com "Hebrew Date Converter - November 28, 2025 / 8th of ..."
