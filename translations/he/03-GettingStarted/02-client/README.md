<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a0acf3093691b1cfcc008a8c6648ea26",
  "translation_date": "2025-06-13T06:48:45+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "he"
}
-->
בקוד הקודם עשינו:

- ייבוא הספריות
- יצירת מופע של client וחיבורו באמצעות stdio כפרוטוקול תקשורת.
- רשימת prompts, משאבים וכלים והפעלתם כולם.

זהו, יש לנו client שיכול לתקשר עם שרת MCP.

בואו ניקח את הזמן בחלק התרגיל הבא ונפרק כל קטע קוד ונבין מה קורה.

## תרגיל: כתיבת client

כפי שנאמר לעיל, ניקח את הזמן להסביר את הקוד, ובכל מקרה אפשר לכתוב יחד אם רוצים.

### -1- ייבוא הספריות

נייבא את הספריות הדרושות, נצטרך הפניות ל-client ולפרוטוקול התקשורת שבחרנו, stdio. stdio הוא פרוטוקול לדברים שמיועדים לרוץ על המחשב המקומי שלך. SSE הוא פרוטוקול תקשורת נוסף שנראה בפרקים הבאים אך זו אפשרות נוספת שלך. לעת עתה, נמשיך עם stdio.

בואו נעבור ליצירת מופעים.

### -2- יצירת מופע של client ופרוטוקול התקשורת

נצטרך ליצור מופע של פרוטוקול התקשורת ושל ה-client שלנו:

### -3- רשימת הפיצ'רים של השרת

כעת יש לנו client שיכול להתחבר אם התוכנית תרוץ. עם זאת, הוא לא מציג את הפיצ'רים שלו בפועל, אז נעשה זאת עכשיו:

מצוין, עכשיו תפסנו את כל הפיצ'רים. השאלה היא מתי משתמשים בהם? ובכן, ה-client הזה פשוט למדי, פשוט במובן שנצטרך לקרוא במפורש לפיצ'רים כשנרצה אותם. בפרק הבא ניצור client מתקדם יותר שיש לו גישה למודל שפה גדול משלו, LLM. לעת עתה, בואו נראה איך ניתן להפעיל את הפיצ'רים בשרת:

### -4- הפעלת פיצ'רים

כדי להפעיל את הפיצ'רים, עלינו לוודא שאנו מציינים את הפרמטרים הנכונים ובמקרים מסוימים את שם מה שאנחנו מנסים להפעיל.

### -5- הרצת ה-client

כדי להריץ את ה-client, הקלד את הפקודה הבאה בטרמינל:

## משימה

במשימה זו, תשתמש במה שלמדת בכתיבת client אך תיצור client משלך.

הנה שרת שניתן להשתמש בו שעליך לקרוא אליו דרך קוד ה-client שלך, נסה להוסיף עוד פיצ'רים לשרת כדי להפוך אותו ליותר מעניין.

## פתרון

[Solution](./solution/README.md)

## נקודות מפתח

הנקודות החשובות בפרק זה לגבי clients הן:

- ניתן להשתמש בהם גם לגילוי וגם להפעלת פיצ'רים בשרת.
- יכולים להפעיל שרת בעת שהם מתחילים (כמו בפרק זה) אך clients יכולים להתחבר גם לשרתים שכבר רצים.
- זו דרך מצוינת לבדוק את יכולות השרת לצד חלופות כמו Inspector כפי שתואר בפרק הקודם.

## משאבים נוספים

- [בניית clients ב-MCP](https://modelcontextprotocol.io/quickstart/client)

## דוגמאות

- [מחשבון Java](../samples/java/calculator/README.md)
- [מחשבון .Net](../../../../03-GettingStarted/samples/csharp)
- [מחשבון JavaScript](../samples/javascript/README.md)
- [מחשבון TypeScript](../samples/typescript/README.md)
- [מחשבון Python](../../../../03-GettingStarted/samples/python)

## מה הלאה

- הבא: [יצירת client עם LLM](/03-GettingStarted/03-llm-client/README.md)

**כתב ויתור**:  
מסמך זה תורגם באמצעות שירות תרגום מבוסס בינה מלאכותית [Co-op Translator](https://github.com/Azure/co-op-translator). למרות שאנו שואפים לדיוק, יש לקחת בחשבון כי תרגומים אוטומטיים עלולים להכיל שגיאות או אי-דיוקים. המסמך המקורי בשפתו המקורית נחשב למקור הסמכותי. למידע קריטי מומלץ להשתמש בתרגום מקצועי אנושי. אנו לא נושאים באחריות לכל אי-הבנה או פרשנות שגויה הנובעת משימוש בתרגום זה.