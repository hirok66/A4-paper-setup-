<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>A4 Multi Page Print</title>

<style>
:root {
  --paper-width: 210mm;
  --paper-height: 270mm;
  --header-height: 25mm;
  --footer-height: 25mm;
}

/* বডি */
body {
  background: #eaeaea;
  margin: 0;
  padding: 20px;
  font-family: 'Noto Sans Bengali', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* পৃষ্ঠা ডিজাইন */
.sheet {
  width: var(--paper-width);
  height: var(--paper-height);
  background: #fff;
  border: 1px solid #ccc;
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-sizing: border-box;
  overflow: hidden;
  position: relative;
}

/* Header */
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: var(--header-height);

  padding: 10mm 15mm;
}

/* Body */
main {
  flex: 1;
  padding: 10mm 15mm;
  overflow: hidden;
  box-sizing: border-box;
}

/* Footer */
footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: var(--footer-height);

  padding: 8mm 15mm;
}

/* প্রিন্ট বাটন */
#printBtn {
  position: fixed;
  top: 15px;
  right: 20px;
  background: #1976d2;
  color: #fff;
  border: none;
  padding: 10px 18px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}
#printBtn:hover {
  background: #0d47a1;
}

/* প্রিন্ট মোড */
@media print {
  body {
    background: none;
  }
  #printBtn {
    display: none;
  }
  .sheet {
    width: 210mm;
    height: 270mm;
    border: none;
    margin: 0 auto;
    box-shadow: none;
    /* page-break-after: always; ← এটা বাদ দাও */
  }
  .sheet:not(:last-child) {
    page-break-after: always;
  }
  header, footer {
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
  @page {
    size: A4;
    margin: 0;
  }
}

</style>
</head>
<body>

<button id="printBtn">🖨️ Print All Pages</button>

<div id="pageContainer">

  <!-- ✅ পৃষ্ঠা ১ -->
  <section class="sheet">
    <header>
      <img src="" alt="Header Logo">
      <div contenteditable="true">প্রথম পেজের হেডার</div>
    </header>

    <main contenteditable="true">
      <h1>প্রথম পেজের শিরোনাম</h1>
      <p>এটি প্রথম পেজের কনটেন্ট। তুমি এখানে নিজের ডিজাইন বসাতে পারো।</p>
    </main>

    <footer>
      <img src="" alt="Footer Logo">
      <div contenteditable="true">প্রথম পেজের ফুটার ঠিকানা</div>
    </footer>
  </section>

  <!-- ✅ পৃষ্ঠা ২ -->
  {{-- <section class="sheet">
    <header>
      <img src="" alt="Header Logo">
      <div contenteditable="true">দ্বিতীয় পেজের হেডার</div>
    </header>

    <main contenteditable="true">
      <h1>দ্বিতীয় পেজের শিরোনাম</h1>
      <p>এটি দ্বিতীয় পেজের কনটেন্ট।</p>
    </main>

    <footer>
      <img src="" alt="Footer Logo">
      <div contenteditable="true">দ্বিতীয় পেজের ফুটার ঠিকানা</div>
    </footer>
  </section> --}}

  <!-- ✅ পৃষ্ঠা ৩ (তুমি যত ইচ্ছা এইভাবে যোগ করতে পারো) -->
  <section class="sheet">
    <header>
      <img src="" alt="Header Logo">
      <div contenteditable="true">তৃতীয় পেজের হেডার</div>
    </header>

    <main contenteditable="true">
      <h1>তৃতীয় পেজের শিরোনাম</h1>
      <p>এটি তৃতীয় পেজের কনটেন্ট। Footer সবসময় নিচে থাকবে।</p>
    </main>

    <footer>
      <img src="" alt="Footer Logo">
      <div contenteditable="true">তৃতীয় পেজের ফুটার ঠিকানা</div>
    </footer>
  </section>

</div>

<script>
document.getElementById('printBtn').addEventListener('click', () => {
  window.print();
});
</script>

</body>
</html>
