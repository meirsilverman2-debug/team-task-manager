# תרחיש הפרויקט — סימולציית צוות פיתוח

מדריך מבוסס תרחיש לתרגול עבודה משולשת עם Git ו-GitHub: שלושה מפתחים, ריפו אחד, זרימת עבודה מלאה — מ-Clone ועד Conflict ו-Revert.

---

## רקע

הצוות קיבל משימה לבנות מערכת **Team Task Manager**.

**שלושה מפתחים:**

- תלמיד 1  
- תלמיד 2  
- תלמיד 3

כולם עובדים על אותו Repository.

**המטרה:** להגיע למצב שבו כולם עושים Clone, יוצרים Branch, עובדים במקביל, פותחים PR, מבצעים Review, עושים Merge, נתקלים ב-Conflict — ופותרים אותו.

---

## שלב 1 — מנהל הצוות

תלמיד 1 הוא ה-**Team Lead**. הוא יוצר את ה-Repository:

team-task-manager

ולאחר מכן:

git clone REPO\_URL

יוצר קובץ README עם התוכן:

Team Task Manager

**Commit:**

git add .

git commit \-m "initial project"

**Push:**

git push origin main

**מה כולם לומדים:** יצירת Repository, Commit ראשון, Push ראשון.

---

## שלב 2 — כל הצוות מבצע Clone

**תלמיד 2:**

git clone REPO\_URL

**תלמיד 3:**

git clone REPO\_URL

**מה לומדים:** כולם עובדים על אותו פרויקט.

---

## שלב 3 — חלוקת משימות

המוצר דורש שלושה חלקים: משתמשים, משימות, דוחות.

| תלמיד | אחריות |
| :---- | :---- |
| תלמיד 1 | Users |
| תלמיד 2 | Tasks |
| תלמיד 3 | Reports |

---

## שלב 4 — Branches

כולם יוצרים Branch נפרד:

\# תלמיד 1

git checkout \-b feature-users

\# תלמיד 2

git checkout \-b feature-tasks

\# תלמיד 3

git checkout \-b feature-reports

**מה לומדים:** לא עובדים על `main`.

---

## שלב 5 — עבודה במקביל

כולם עובדים באותו זמן, כל אחד על קובץ משלו:

- תלמיד 1 יוצר `users.txt`  
- תלמיד 2 יוצר `tasks.txt`  
- תלמיד 3 יוצר `reports.txt`

כל אחד מריץ:

git status

git add .

git commit \-m "feat: ..."

**מה לומדים:** כל אחד עובד בנפרד.

---

## שלב 6 — Push

כולם:

git push origin BRANCH\_NAME

**מה לומדים:** הקוד עובר ל-GitHub.

---

## שלב 7 — Pull Requests

כולם פותחים PR. ב-GitHub זה מופיע כ-**Compare & Pull Request**.

**מה לומדים:** לא עושים Merge לבד.

---

## שלב 8 — Code Review

עכשיו נכנסת עבודת הצוות — כל אחד בודק את חברו במעגל:

תלמיד 1 בודק את תלמיד 2

תלמיד 2 בודק את תלמיד 3

תלמיד 3 בודק את תלמיד 1

חובה לרשום הערה — גם אם זו רק `Looks good`.

**מה לומדים:** תהליך Review.

---

## שלב 9 — Merge

לאחר אישור, מבצעים Merge. עכשיו `main` מכיל: `users.txt`, `tasks.txt`, `reports.txt`.

**מה לומדים:** הכנסת קוד לפרויקט המרכזי.

---

## שלב 10 — Sync

כולם מעדכנים את המחשב שלהם:

git checkout main

git pull

**מה לומדים:** לקבל את העבודה של שאר הצוות.

---

## שלב 11 — פיצ'ר חדש

מנהל המוצר מבקש להוסיף עדיפות למשימות. עכשיו כולם יעבדו על אותו קובץ — וכאן מתחילה הבעיה.

כולם:

git checkout \-b feature-priority

---

## שלב 12 — יצירת Conflict בכוונה

כל תלמיד משנה את אותה שורה בקובץ `tasks.txt`:

| תלמיד | שינוי |
| :---- | :---- |
| תלמיד 1 | `Create Login Page - HIGH` |
| תלמיד 2 | `Create Login Page - MEDIUM` |
| תלמיד 3 | `Create Login Page - LOW` |

כולם:

git add .

git commit \-m "update priority"

git push

---

## שלב 13 — PR ראשון

תלמיד 1 מבצע Merge — אין בעיה.

---

## שלב 14 — PR שני

תלמיד 2 מנסה Merge. GitHub מציג:

Conflict detected

**מה לומדים:** למה נוצרים Conflicts.

---

## שלב 15 — פתרון Conflict

תלמיד 2 מעדכן את `main` שלו:

git checkout main

git pull

חוזר ל-branch שלו ומבצע מיזוג:

git checkout feature-priority

git merge main

מופיע קונפליקט:

\<\<\<\<\<\<\< HEAD

HIGH

\=======

MEDIUM

\>\>\>\>\>\>\> main

התלמיד בוחר מה נשאר — למשל `HIGH` — ומוחק את הסימונים. לאחר מכן:

git add .

git commit \-m "resolve conflict"

git push

**מה לומדים:** פתרון Conflict אמיתי.

---

## שלב 16 — Stash

המנהל מבקש תיקון דחוף, אבל תלמיד 3 באמצע עבודה לא גמורה.

git stash          \# שומר את העבודה בצד

git switch main    \# עובר לביצוע התיקון

\# ... מבצע תיקון ...

git stash pop      \# מחזיר את העבודה

**מה לומדים:** שמירת עבודה זמנית.

---

## שלב 17 — Revert

מישהו הכניס שינוי לא נכון.

git log                  \# בודקים מה ה-Commit הבעייתי

git revert COMMIT\_ID     \# מבטלים אותו

**מה לומדים:** איך מבטלים שינוי בלי להרוס היסטוריה.

---

## סיכום — הזרימה המלאה

Clone

  ↓

Branch

  ↓

Develop

  ↓

Commit

  ↓

Push

  ↓

Pull Request

  ↓

Code Review

  ↓

Merge

  ↓

Pull

  ↓

Conflict

  ↓

Resolve

  ↓

Stash

  ↓

Revert

זו כבר סימולציה כמעט מלאה של יום עבודה אמיתי בצוות פיתוח — לא רק תרגול פקודות Git.  
