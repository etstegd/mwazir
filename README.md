<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Wazir Grades | Wazir Coding</title>

  <style>
    * {
      box-sizing: border-box;
      font-family: Tahoma, Arial, sans-serif;
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
      background: linear-gradient(135deg, #0f172a, #164e63);
      color: #f8fafc;
    }

    .container {
      width: 100%;
      max-width: 470px;
      padding: 28px;
      background: #ffffff;
      color: #172033;
      border-radius: 20px;
      box-shadow: 0 15px 45px #0004;
    }

    .brand {
      text-align: center;
      margin-bottom: 24px;
    }

    .brand h1 {
      margin: 0;
      color: #0f766e;
      font-size: 29px;
    }

    .brand p {
      color: #64748b;
      margin: 9px 0 0;
    }

    .location {
      display: inline-block;
      margin-top: 12px;
      padding: 7px 13px;
      background: #ccfbf1;
      color: #115e59;
      border-radius: 20px;
      font-size: 14px;
    }

    label {
      display: block;
      margin: 16px 0 8px;
      font-weight: bold;
    }

    input {
      width: 100%;
      padding: 13px;
      border: 1px solid #cbd5e1;
      border-radius: 10px;
      font-size: 15px;
      background: #f8fafc;
    }

    input:focus {
      outline: 2px solid #0d9488;
      border-color: transparent;
    }

    button {
      width: 100%;
      padding: 14px;
      margin-top: 22px;
      border: none;
      border-radius: 10px;
      background: #0d9488;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }

    button:hover {
      background: #0f766e;
    }

    .notice {
      margin-top: 16px;
      padding: 12px;
      background: #fef3c7;
      color: #92400e;
      border-radius: 10px;
      font-size: 13px;
      line-height: 1.8;
    }

    footer {
      margin-top: 24px;
      padding-top: 16px;
      border-top: 1px solid #e2e8f0;
      text-align: center;
      color: #64748b;
      font-size: 13px;
      line-height: 1.9;
    }

    footer a {
      color: #0f766e;
      text-decoration: none;
    }
  </style>
</head>

<body>
  <main class="container">
    <header class="brand">
      <h1>Wazir Grades</h1>
      <p>نظام استقبال ملفات درجات المدارس</p>
      <span class="location">📍 مركز ببا</span>
    </header>

    <form id="gradesForm">
      <label for="schoolName">اسم المدرسة</label>
      <input
        id="schoolName"
        type="text"
        placeholder="اكتب اسم المدرسة"
        required
      >

      <label for="schoolCode">كود المدرسة</label>
      <input
        id="schoolCode"
        type="text"
        placeholder="اكتب كود المدرسة"
        required
      >

      <label for="gradesFile">ملف الدرجات</label>
      <input
        id="gradesFile"
        type="file"
        accept=".xlsx,.xls,.xlsm,.csv"
        required
      >

      <button type="submit">
        إرسال بيانات الملف عبر واتساب
      </button>
    </form>

    <div class="notice">
      ⚠️ بعد فتح واتساب، أرفق ملف الدرجات يدويًا في المحادثة،
      ثم اضغط إرسال. لا تغلق الصفحة قبل التأكد من إرفاق الملف.
    </div>

    <footer>
      <strong>Wazir Coding</strong><br>
      مركز ببا<br>
      رقم الشركة:
      <a href="tel:01204261726">01204261726</a>
    </footer>
  </main>

  <script>
    const COMPANY_NAME = "Wazir Coding";
    const CENTER_NAME = "مركز ببا";
    const COMPANY_PHONE = "01204261726";

    // رقم واتساب المصري بصيغة دولية بدون علامة +
    const ADMIN_WHATSAPP = "201222995534";

    document
      .getElementById("gradesForm")
      .addEventListener("submit", function (event) {
        event.preventDefault();

        const schoolName =
          document.getElementById("schoolName").value.trim();

        const schoolCode =
          document.getElementById("schoolCode").value.trim();

        const fileInput =
          document.getElementById("gradesFile");

        const file = fileInput.files[0];

        if (!schoolName || !schoolCode || !file) {
          alert("من فضلك أكمل البيانات واختر ملف الدرجات.");
          return;
        }

        const allowedExtensions = [
          "xlsx", "xls", "xlsm", "csv"
        ];

        const extension = file.name
          .split(".")
          .pop()
          .toLowerCase();

        if (!allowedExtensions.includes(extension)) {
          alert("نوع الملف غير مدعوم.");
          return;
        }

        const message = [
          "طلب إرسال ملف درجات مدرسة",
          "الشركة: " + COMPANY_NAME,
          "الإدارة/المركز: " + CENTER_NAME,
          "اسم المدرسة: " + schoolName,
          "كود المدرسة: " + schoolCode,
          "اسم الملف المطلوب إرفاقه: " + file.name
        ].join("\n");

        const whatsappURL =
          "https://wa.me/" +
          ADMIN_WHATSAPP +
          "?text=" +
          encodeURIComponent(message);

        window.open(whatsappURL, "_blank");
      });
  </script>
</body>
</html>
