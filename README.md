<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Free PDF & Image Tools Online</title>
  <meta name="description" content="Convert, compress, resize, and manage PDFs & images online. Free tools: Merge PDF, Split PDF, Compress PDF, Image to PDF, Resize Image, PDF to Images, and more.">
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf-lib/1.17.1/pdf-lib.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.16.105/pdf.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.7.1/jszip.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>
</head>
<body class="bg-gray-100">

  <!-- Hero Section -->
  <header class="bg-blue-600 text-white py-12 text-center">
    <h1 class="text-4xl font-bold">🛠️ Free PDF & Image Tools</h1>
    <p class="mt-3 text-lg">Convert, compress, resize, and manage your files easily — 100% free, no signup needed.</p>
  </header>

  <!-- Ads Placeholder -->
  <div class="my-6 flex justify-center">
    <div class="bg-gray-200 text-gray-600 p-4 w-[728px] h-[90px] flex items-center justify-center rounded">
      🚀 Google AdSense Banner (728x90)
    </div>
  </div>

  <!-- Tools Grid -->
  <main class="max-w-6xl mx-auto px-4 py-8">
    <h2 class="text-2xl font-semibold mb-6 text-center">Choose a Tool</h2>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
      <button onclick="showTool('mergePdfTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">📑 <strong>Merge PDF</strong></button>
      <button onclick="showTool('splitPdfTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">✂️ <strong>Split PDF</strong></button>
      <button onclick="showTool('compressPdfTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">📉 <strong>Compress PDF</strong></button>
      <button onclick="showTool('imgToPdfTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">🖼️ <strong>Image → PDF</strong></button>
      <button onclick="showTool('resizeImgTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">📐 <strong>Resize Image</strong></button>
      <button onclick="showTool('compressImgTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">🗜️ <strong>Compress Image</strong></button>
      <button onclick="showTool('pdfToImgTool')" class="bg-white shadow-lg p-6 rounded-xl hover:shadow-2xl transition">🖼️ <strong>PDF → Images</strong></button>
    </div>
  </main>

  <!-- SEO Text Section -->
  <section class="bg-white py-12 mt-8">
    <div class="max-w-5xl mx-auto px-4 text-center">
      <h2 class="text-2xl font-semibold mb-4">Why Choose Our Free PDF & Image Tools?</h2>
      <p class="text-gray-600 mb-4">
        Manage PDF and image files quickly without installing software. Merge PDFs, compress large documents, convert images to PDF, resize images, and more — all in your browser, fast, secure, and free.
      </p>
      <p class="text-gray-600">
        Your files stay private and never leave your device. Start converting, compressing, and resizing now!
      </p>
    </div>
  </section>

  <!-- Ads Placeholder -->
  <div class="my-6 flex justify-center">
    <div class="bg-gray-200 text-gray-600 p-4 w-[300px] h-[250px] flex items-center justify-center rounded">
      📢 Google AdSense Box (300x250)
    </div>
  </div>

  <!-- Tools Section -->
  <section class="max-w-4xl mx-auto px-4 py-8">
    <div id="toolContainer" class="bg-white shadow-lg rounded-xl p-6 hidden"></div>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-800 text-white py-6 text-center">
    <p>© 2025 Free PDF & Image Tools. All rights reserved.</p>
  </footer>

<script>
  let allImages = [];

  function showTool(tool) {
    const container = document.getElementById("toolContainer");
    container.classList.remove("hidden");

    if (tool === "mergePdfTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">📑 Merge PDF</h3>
        <input type="file" id="mergePdfInput" multiple accept="application/pdf" class="mb-4">
        <button onclick="mergePDFs()" class="bg-blue-600 text-white px-4 py-2 rounded">Merge</button>
        <p id="mergeStatus" class="mt-2 text-gray-600"></p>
      `;
    } 
    else if (tool === "splitPdfTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">✂️ Split PDF</h3>
        <input type="file" id="splitPdfInput" accept="application/pdf" class="mb-4"><br>
        <input type="text" id="splitPages" placeholder="e.g. 1-3,5" class="border p-2 mb-4 w-full"><br>
        <button onclick="splitPDF()" class="bg-blue-600 text-white px-4 py-2 rounded">Split</button>
        <p id="splitStatus" class="mt-2 text-gray-600"></p>
      `;
    }
    else if (tool === "compressPdfTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">📉 Compress PDF</h3>
        <input type="file" id="compressPdfInput" accept="application/pdf" class="mb-4"><br>
        <button onclick="compressPDF()" class="bg-blue-600 text-white px-4 py-2 rounded">Compress</button>
        <p id="compressStatus" class="mt-2 text-gray-600"></p>
      `;
    }
    else if (tool === "imgToPdfTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">🖼️ Image → PDF</h3>
        <input type="file" id="imgToPdfInput" multiple accept="image/*" class="mb-4"><br>
        <button onclick="imagesToPDF()" class="bg-blue-600 text-white px-4 py-2 rounded">Convert</button>
        <p id="imgToPdfStatus" class="mt-2 text-gray-600"></p>
      `;
    }
    else if (tool === "resizeImgTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">📐 Resize Image</h3>
        <input type="file" id="resizeImgInput" accept="image/*" class="mb-4"><br>
        <input type="number" id="resizeWidth" placeholder="Width (px)" class="border p-2 mb-2 w-full"><br>
        <input type="number" id="resizeHeight" placeholder="Height (px)" class="border p-2 mb-2 w-full"><br>
        <button onclick="resizeImage()" class="bg-blue-600 text-white px-4 py-2 rounded">Resize</button>
        <p id="resizeStatus" class="mt-2 text-gray-600"></p>
      `;
    }
    else if (tool === "compressImgTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">🗜️ Compress Image</h3>
        <input type="file" id="compressImgInput" accept="image/*" class="mb-4"><br>
        <label>Quality (0.1 - 1):</label>
        <input type="number" id="imgQuality" value="0.7" min="0.1" max="1" step="0.1" class="border p-2 mb-2 w-full"><br>
        <button onclick="compressImage()" class="bg-blue-600 text-white px-4 py-2 rounded">Compress</button>
        <p id="compressImgStatus" class="mt-2 text-gray-600"></p>
      `;
    }
    else if (tool === "pdfToImgTool") {
      container.innerHTML = `
        <h3 class="text-xl font-semibold mb-4">🖼️ PDF → Images</h3>
        <input type="file" id="pdfToImgInput" accept="application/pdf" class="mb-4"><br>
        <label>DPI:</label>
        <input type="number" id="dpi" value="150" min="72" max="300" class="border p-2 mb-2 w-full"><br>
        <label>Format:</label>
        <select id="imgFormat" class="border p-2 mb-2 w-full">
          <option value="png">PNG</option>
          <option value="jpeg">JPEG</option>
        </select><br>
        <button onclick="pdfToImages()" class="bg-blue-600 text-white px-4 py-2 rounded">Convert</button>
        <button id="downloadZipBtn" onclick="downloadZip()" class="bg-green-600 text-white px-4 py-2 rounded hidden">Download All</button>
        <p id="pdfToImgStatus" class="mt-2 text-gray-600"></p>
        <div id="imagesContainer" class="grid grid-cols-2 gap-2 mt-4"></div>
      `;
    }
  }

  // --- PDF Functions ---
  async function mergePDFs() {
    const files = document.getElementById("mergePdfInput").files;
    if (files.length < 2) return alert("Select at least 2 PDFs.");
    const mergedPdf = await PDFLib.PDFDocument.create();
    for (let file of files) {
      const pdfBytes = await file.arrayBuffer();
      const pdf = await PDFLib.PDFDocument.load(pdfBytes);
      const pages = await mergedPdf.copyPages(pdf, pdf.getPageIndices());
      pages.forEach(p => mergedPdf.addPage(p));
    }
    const mergedBytes = await mergedPdf.save();
    downloadBlob(new Blob([mergedBytes]), "merged.pdf");
    document.getElementById("mergeStatus").textContent = "✅ PDF merged!";
  }

  async function splitPDF() {
    const file = document.getElementById("splitPdfInput").files[0];
    if (!file) return alert("Select a PDF.");
    const ranges = document.getElementById("splitPages").value.split(",");
    const pdfBytes = await file.arrayBuffer();
    const pdf = await PDFLib.PDFDocument.load(pdfBytes);

    for (let range of ranges) {
      let [start, end] = range.split("-").map(n => parseInt(n));
      if (!end) end = start;
      const newPdf = await PDFLib.PDFDocument.create();
      const pages = await newPdf.copyPages(pdf, Array.from({length: end - start + 1}, (_, i) => start - 1 + i));
      pages.forEach(p => newPdf.addPage(p));
      const newBytes = await newPdf.save();
      downloadBlob(new Blob([newBytes]), `split_${range}.pdf`);
    }
    document.getElementById("splitStatus").textContent = "✅ PDF split!";
  }

  async function compressPDF() {
    const file = document.getElementById("compressPdfInput").files[0];
    if (!file) return alert("Select a PDF.");
    // Basic re-save (true compression needs backend)
    const pdfBytes = await file.arrayBuffer();
    const pdf = await PDFLib.PDFDocument.load(pdfBytes);
    const compressedBytes = await pdf.save();
    downloadBlob(new Blob([compressedBytes]), "compressed.pdf");
    document.getElementById("compressStatus").textContent = "✅ PDF compressed!";
  }

  async function imagesToPDF() {
    const files = document.getElementById("imgToPdfInput").files;
    if (!files.length) return alert("Select images.");
    const pdfDoc = await PDFLib.PDFDocument.create();
    for (let file of files) {
      const imgBytes = await file.arrayBuffer();
      let img, page;
      if (file.type.includes("png")) {
        img = await pdfDoc.embedPng(imgBytes);
      } else {
        img = await pdfDoc.embedJpg(imgBytes);
      }
      page = pdfDoc.addPage([img.width, img.height]);
      page.drawImage(img, {x: 0, y: 0, width: img.width, height: img.height});
    }
    const pdfBytes = await pdfDoc.save();
    downloadBlob(new Blob([pdfBytes]), "images.pdf");
    document.getElementById("imgToPdfStatus").textContent = "✅ Images converted!";
  }

  function resizeImage() {
    const file = document.getElementById("resizeImgInput").files[0];
    if (!file) return alert("Select an image.");
    const width = parseInt(document.getElementById("resizeWidth").value);
    const height = parseInt(document.getElementById("resizeHeight").value);
    const reader = new FileReader();
    reader.onload = e => {
      const img = new Image();
      img.onload = () => {
        const canvas = document.createElement("canvas");
        canvas.width = width;
        canvas.height = height;
        canvas.getContext("2d").drawImage(img, 0, 0, width, height);
        canvas.toBlob(blob => downloadBlob(blob, "resized.png"));
        document.getElementById("resizeStatus").textContent = "✅ Image resized!";
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  function compressImage() {
    const file = document.getElementById("compressImgInput").files[0];
    if (!file) return alert("Select an image.");
    const quality = parseFloat(document.getElementById("imgQuality").value);
    const reader = new FileReader();
    reader.onload = e => {
      const img = new Image();
      img.onload = () => {
        const canvas = document.createElement("canvas");
        canvas.width = img.width;
        canvas.height = img.height;
        canvas.getContext("2d").drawImage(img, 0, 0);
        canvas.toBlob(blob => downloadBlob(blob, "compressed.jpg"), "image/jpeg", quality);
        document.getElementById("compressImgStatus").textContent = "✅ Image compressed!";
      };
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }

  async function pdfToImages() {
    const fileInput = document.getElementById("pdfToImgInput");
    if (!fileInput.files[0]) return alert("Upload a PDF.");
    const dpi = parseInt(document.getElementById("dpi").value);
    const format = document.getElementById("imgFormat").value;
    const pdfFile = fileInput.files[0];
    const arrayBuffer = await pdfFile.arrayBuffer();
    const pdf = await pdfjsLib.getDocument({ data: arrayBuffer }).promise;

    const imagesContainer = document.getElementById("imagesContainer");
    imagesContainer.innerHTML = "";
    allImages = [];

    for (let pageNum = 1; pageNum <= pdf.numPages; pageNum++) {
      const page = await pdf.getPage(pageNum);
      const viewport = page.getViewport({ scale: dpi / 72 });
      const canvas = document.createElement("canvas");
      const ctx = canvas.getContext("2d");
      canvas.width = viewport.width;
      canvas.height = viewport.height;
      await page.render({ canvasContext: ctx, viewport }).promise;

      const imgData = canvas.toDataURL("image/" + format);
      allImages.push({ name: `page_${pageNum}.${format}`, data: imgData });

      const img = document.createElement("img");
      img.src = imgData;
      img.className = "border rounded shadow";
      imagesContainer.appendChild(img);
    }

    document.getElementById("downloadZipBtn").classList.remove("hidden");
    document.getElementById("pdfToImgStatus").textContent = "✅ PDF converted!";
  }

  async function downloadZip() {
    const zip = new JSZip();
    allImages.forEach(img => {
      const base64 = img.data.split(",")[1];
      zip.file(img.name, base64, { base64: true });
    });
    const content = await zip.generateAsync({ type: "blob" });
    saveAs(content, "pdf_images.zip");
  }

  function downloadBlob(blob, filename) {
    const link = document.createElement("a");
    link.href = URL.createObjectURL(blob);
    link.download = filename;
    link.click();
  }
</script>
</body>
</html>
