<img width="822" height="422" alt="image" src="https://github.com/user-attachments/assets/6efdef09-542e-488a-9d26-8a91419c3e25" /># A4-paper-setup-

<!doctype html>
<html lang="bn">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Print A4 page/title>
<style>
:root {
  --paper-width: 210mm;
  --paper-height: 297mm;
  --header-height: 30mm;
  --footer-height: 30mm;
}

/* সাধারণ স্টাইল */
body {
  background: #f2f2f2;
  margin: 0;
  padding: 20px;
  font-family: 'Noto Sans Bengali', Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* পৃষ্ঠা */
.sheet {
  width: var(--paper-width);
  height: 270mm;
  background: #fff;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  border: 1px solid #ccc;
}


.sheet:hover .delete-btn {
  display: block;
}

/* Header */
header {
  height: var(--header-height);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10mm 15mm;
  background: #e6f2ff;
  border-bottom: 1px solid #007bff;
}
header img {
  width: 60mm;
  max-height: 25mm;
  object-fit: contain;
}

/* Main Content */
main {
  flex: 1;
  padding: 6mm 11mm;
  box-sizing: border-box;
  overflow: hidden;
}
main h1 {
  color: #007bff;
  margin-top: 0;
}
main p {
  color: #333;
  line-height: 1.6;
}
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}
table, th, td {
  border: 1px solid #007bff;
}
th, td {
  padding: 8px;
  text-align: left;
}
th {
  background: #cce5ff;
}

/* Footer */
footer {
  height: var(--footer-height);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 6mm 15mm;
  border-top: 1px solid #007bff;
  background: #e6f2ff;
  margin-top: auto;
}
footer img {
  width: 40mm;
  max-height: 20mm;
  object-fit: contain;
}

/* Buttons */
.print-btn, .mail-btn {
  position: fixed;
  top: 15px;
  right: 20px;
  color: #fff;
  border: none;
  padding: 8px 14px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 14px;
  box-shadow: 0 3px 8px rgba(0, 0, 0, 0.2);
  z-index: 999;
  transition: all 0.2s ease-in-out;
}
.mail-btn { right: 100px; background: #28a745; }
.print-btn { background: #007bff; }
.print-btn:hover, .mail-btn:hover { transform: scale(1.05); }

/* প্রিন্টের জন্য */
@media print {
  body { background: none; }
  .print-btn, .mail-btn, .delete-btn { display: none !important; }
  .sheet {
    width: 210mm;
    height: 270mm;
    margin: 0 auto;
    box-shadow: none;
    border: none;
    page-break-after: auto; /* blank page এড়াতে */
    overflow: hidden;
  }
  header, footer {
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
  @page {
    size: A4;
    margin: 10mm;
  }
}
</style>
</head>
<body>

<button class="mail-btn" id="mailBtn">Mail</button>
<button class="print-btn" id="printBtn">Print</button>

<div id="pages">
  <section class="sheet">
    <button class="delete-btn">🗑️</button>

    <header>
      <img src="{{ asset('assets/header.jpeg') }}" alt="Header Logo">
      <div contenteditable="true">তারিখ / ঠিকানা</div>
    </header>

    <main contenteditable="true">
      <h1>প্রথম পৃষ্ঠা</h1>
      <p>এটি একটি প্রিন্টেবল পৃষ্ঠা। এখানে তুমি নিজের লেখা যোগ করতে পারো।</p>
      <table>
        <tr><th>আইটেম</th><th>পরিমাণ</th><th>মূল্য</th></tr>
        <tr><td>আইটেম ১</td><td>২</td><td>৳100</td></tr>
        <tr><td>আইটেম ২</td><td>৫</td><td>৳250</td></tr>
      </table>
    </main>

    <footer>
      <img src="{{ asset('assets/footer.jpeg') }}" alt="Footer Logo">
      <div contenteditable="true">Grameen CyberNet Ltd. | যোগাযোগ: +8801XXXXXXXXX</div>
    </footer>
  </section>
</div>

<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script>
$(document).ready(function(){
  $('#printBtn').on('click', function(){ window.print(); });
  $('#mailBtn').on('click', function(){ alert('Mail বাটন কাজের জন্য প্রস্তুত!'); });
  $(document).on('click', '.delete-btn', function(){
    if(confirm('তুমি কি এই পৃষ্ঠা মুছে ফেলতে চাও?')){
      $(this).closest('.sheet').remove();
    }
  });
});
</script>

</body>
</html>
