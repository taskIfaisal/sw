<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Batch Remove Background (Output .PNG) — Full Code</title>
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background: #121212;
      color: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    h2 {
      margin: 0 0 16px 0;
      font-size: 20px;
    }
    .config-box {
      background: #1c1c1c;
      border: 1px solid #2e2e2e;
      border-radius: 8px;
      padding: 14px;
      margin-bottom: 16px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 12px;
    }
    .config-field label {
      display: block;
      font-size: 12px;
      color: #aaa;
      margin-bottom: 4px;
    }
    .config-field input {
      width: 100%;
      padding: 8px 10px;
      border-radius: 6px;
      border: 1px solid #3a3a3a;
      background: #121212;
      color: #fff;
      font-size: 13px;
    }
    .controls {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 10px;
      margin-bottom: 16px;
    }
    .btn, button {
      background: #4CAF50;
      color: #fff;
      border: none;
      padding: 10px 16px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 14px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: background 0.2s ease, opacity 0.2s ease;
    }
    .btn:hover:not(:disabled), button:hover:not(:disabled) {
      background: #43a047;
    }
    .btn-blue {
      background: #2196F3;
    }
    .btn-blue:hover:not(:disabled) {
      background: #1976D2;
    }
    .btn-gray {
      background: #424242;
    }
    .btn-gray:hover:not(:disabled) {
      background: #525252;
    }
    button:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }
    .summary {
      font-size: 13px;
      color: #ccc;
      margin-left: auto;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 14px;
    }
    .card {
      background: #1e1e1e;
      border: 1px solid #303030;
      border-radius: 8px;
      padding: 10px;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .card img {
      width: 100%;
      height: 160px;
      object-fit: contain;
      background: repeating-conic-gradient(#2a2a2a 0% 25%, #383838 0% 50%) 50% / 16px 16px;
      border-radius: 4px;
    }
    .filename {
      font-size: 13px;
      font-weight: 600;
      word-break: break-all;
    }
    .subname {
      font-size: 11px;
      color: #9e9e9e;
      word-break: break-all;
    }
    .status {
      font-size: 12px;
      color: #bbb;
    }
    .status.ok {
      color: #4CAF50;
    }
    .status.err {
      color: #ef5350;
    }
    .card-actions {
      display: flex;
      gap: 6px;
      margin-top: auto;
    }
    .card-actions button {
      flex: 1;
      padding: 7px 10px;
      font-size: 12px;
      justify-content: center;
    }
    .hint {
      font-size: 12px;
      color: #888;
      margin-top: 14px;
    }
  </style>
</head>
<body>
  <h2>Batch Remove Background (Output .PNG + Unduh Sekaligus + Memory Clean)</h2>

  <div class="config-box">
    <div class="config-field">
      <label for="endpoint-input">Endpoint URL API</label>
      <input
        type="text"
        id="endpoint-input"
        value="https://api.remove.bg/v1.0/removebg"
        placeholder="https://api.remove.bg/v1.0/removebg atau endpoint Anda"
      />
    </div>
    <div class="config-field">
      <label for="api-key-input">API Key (opsional jika sudah di-handle server)</label>
      <input
        type="password"
        id="api-key-input"
        placeholder="Masukkan X-Api-Key jika panggil langsung"
      />
    </div>
  </div>

  <div class="controls">
    <label class="btn">
      Pilih Banyak Gambar
      <input type="file" id="batch-input" accept="image/*" multiple hidden />
    </label>

    <button id="process-btn" disabled>Proses Semua</button>
    <button id="download-all-btn" class="btn-blue" disabled>Unduh Semua (.PNG)</button>
    <button id="clear-btn" class="btn-gray" disabled>Bersihkan &amp; Bebaskan Memori</button>

    <span id="summary" class="summary">Belum ada gambar dipilih</span>
  </div>

  <div id="result-grid" class="grid"></div>

  <p class="hint">
    Semua nama file hasil otomatis menjadi <code>.png</code> (contoh: <code>foto1.jpg</code> → <code>foto1.png</code>) dan memori Object URL/Blob dibersihkan saat reset, hapus item, atau tutup halaman.
  </p>

  <script>
    const endpointInput = document.getElementById('endpoint-input');
    const apiKeyInput = document.getElementById('api-key-input');
    const batchInput = document.getElementById('batch-input');
    const processBtn = document.getElementById('process-btn');
    const downloadAllBtn = document.getElementById('download-all-btn');
    const clearBtn = document.getElementById('clear-btn');
    const resultGrid = document.getElementById('result-grid');
    const summaryEl = document.getElementById('summary');

    const CONCURRENCY = 2; // Proses 2 gambar bersamaan agar aman dari rate limit
    let items = [];
    let isProcessing = false;

    function formatMB(bytes) {
      return `${(bytes / (1024 * 1024)).toFixed(2)} MB`;
    }

    // Ubah ekstensi nama file asli menjadi .png (contoh: foto1.jpg -> foto1.png)
    function toPngFilename(originalName) {
      const baseName = originalName.replace(/\.[^/.]+$/, '');
      return `${baseName || 'image'}.png`;
    }

    // Bebaskan Object URL dan referensi berat pada satu item
    function releaseItemMemory(item) {
      if (item.previewUrl) {
        URL.revokeObjectURL(item.previewUrl);
        item.previewUrl = null;
      }
      if (item.resultUrl) {
        URL.revokeObjectURL(item.resultUrl);
        item.resultUrl = null;
      }
      item.file = null;
      item.resultBlob = null;
      if (item.imgEl) {
        item.imgEl.src = '';
        item.imgEl.remove();
        item.imgEl = null;
      }
    }

    // Bersihkan seluruh state & memori DOM/Blob
    function clearAllMemory() {
      for (const item of items) {
        releaseItemMemory(item);
      }
      items = [];
      resultGrid.replaceChildren();
      batchInput.value = '';
      processBtn.disabled = true;
      downloadAllBtn.disabled = true;
      clearBtn.disabled = true;
      summaryEl.textContent = 'Memori dibersihkan — belum ada gambar dipilih';
    }

    function updateControlsState() {
      const hasItems = items.length > 0;
      const doneCount = items.filter((it) => it.status === 'done' && it.resultBlob).length;

      processBtn.disabled = !hasItems || isProcessing;
      downloadAllBtn.disabled = doneCount === 0 || isProcessing;
      clearBtn.disabled = !hasItems || isProcessing;
      batchInput.disabled = isProcessing;
    }

    function updateSummary() {
      if (!items.length) {
        summaryEl.textContent = 'Belum ada gambar dipilih';
        return;
      }
      const doneCount = items.filter((it) => it.status === 'done').length;
      const errCount = items.filter((it) => it.status === 'error').length;
      summaryEl.textContent = `Total: ${items.length} | Selesai: ${doneCount} | Gagal: ${errCount}`;
    }

    // Render daftar kartu saat memilih banyak gambar sekaligus
    batchInput.addEventListener('change', (e) => {
      const selectedFiles = Array.from(e.target.files || []);
      if (!selectedFiles.length) return;

      for (const oldItem of items) {
        releaseItemMemory(oldItem);
      }
      items = [];
      resultGrid.replaceChildren();

      const fragment = document.createDocumentFragment();

      selectedFiles.forEach((file, index) => {
        const previewUrl = URL.createObjectURL(file);
        const outputName = toPngFilename(file.name);

        const card = document.createElement('div');
        card.className = 'card';

        const img = document.createElement('img');
        img.src = previewUrl;
        img.alt = outputName;

        const nameDiv = document.createElement('div');
        nameDiv.className = 'filename';
        nameDiv.textContent = outputName;

        const subDiv = document.createElement('div');
        subDiv.className = 'subname';
        subDiv.textContent = `Asli: ${file.name}`;

        const statusDiv = document.createElement('div');
        statusDiv.className = 'status';
        statusDiv.textContent = `Siap (${formatMB(file.size)})`;

        const actionsDiv = document.createElement('div');
        actionsDiv.className = 'card-actions';

        const singleDlBtn = document.createElement('button');
        singleDlBtn.className = 'btn-blue';
        singleDlBtn.textContent = 'Unduh .PNG';
        singleDlBtn.disabled = true;

        const removeSingleBtn = document.createElement('button');
        removeSingleBtn.className = 'btn-gray';
        removeSingleBtn.textContent = 'Hapus';

        const itemObj = {
          id: index,
          file,
          originalName: file.name,
          outputName,
          previewUrl,
          resultBlob: null,
          resultUrl: null,
          status: 'pending',
          cardEl: card,
          imgEl: img,
          statusEl: statusDiv,
          singleDlBtn
        };

        singleDlBtn.addEventListener('click', () => {
          triggerSingleDownload(itemObj);
        });

        removeSingleBtn.addEventListener('click', () => {
          if (isProcessing) return;
          releaseItemMemory(itemObj);
          card.remove();
          items = items.filter((it) => it !== itemObj);
          updateSummary();
          updateControlsState();
        });

        actionsDiv.append(singleDlBtn, removeSingleBtn);
        card.append(img, nameDiv, subDiv, statusDiv, actionsDiv);
        fragment.appendChild(card);

        items.push(itemObj);
      });

      resultGrid.appendChild(fragment);
      updateSummary();
      updateControlsState();
    });

    async function processSingleItem(item) {
      if (!item.file || item.status === 'done') return;

      item.status = 'processing';
      item.statusEl.className = 'status';
      item.statusEl.textContent = 'Memproses (kualitas asli)...';

      const endpoint = endpointInput.value.trim();
      const apiKey = apiKeyInput.value.trim();

      if (!endpoint) {
        item.status = 'error';
        item.statusEl.className = 'status err';
        item.statusEl.textContent = 'Gagal: Endpoint URL kosong';
        return;
      }

      try {
        // Kirim File asli tanpa resize/kompresi agar resolusi & ketajaman terjaga
        const formData = new FormData();
        formData.append('image_file', item.file, item.originalName);
        formData.append('size', 'auto');

        const headers = {};
        if (apiKey) {
          headers['X-Api-Key'] = apiKey;
        }

        const response = await fetch(endpoint, {
          method: 'POST',
          headers,
          body: formData
        });

        if (!response.ok) {
          const errText = await response.text().catch(() => '');
          throw new Error(`HTTP ${response.status}${errText ? ` - ${errText.slice(0, 80)}` : ''}`);
        }

        const rawBlob = await response.blob();
        if (!rawBlob || rawBlob.size === 0) {
          throw new Error('Respons gambar kosong');
        }

        // Pastikan tipe MIME Blob bernilai image/png tanpa mengubah bit/kualitas gambar
        const pngBlob = rawBlob.type === 'image/png'
          ? rawBlob
          : new Blob([rawBlob], { type: 'image/png' });

        if (item.previewUrl) {
          URL.revokeObjectURL(item.previewUrl);
          item.previewUrl = null;
        }

        item.resultBlob = pngBlob;
        item.resultUrl = URL.createObjectURL(pngBlob);
        item.imgEl.src = item.resultUrl;
        item.status = 'done';
        item.statusEl.className = 'status ok';
        item.statusEl.textContent = `Selesai (${formatMB(pngBlob.size)})`;
        item.singleDlBtn.disabled = false;

        // Lepaskan referensi File mentah setelah selesai diproses
        item.file = null;
      } catch (err) {
        item.status = 'error';
        item.statusEl.className = 'status err';
        item.statusEl.textContent = `Gagal: ${err.message}`;
      } finally {
        updateSummary();
      }
    }

    async function runBatchProcess() {
      if (isProcessing || !items.length) return;
      isProcessing = true;
      updateControlsState();

      let cursor = 0;

      async function worker() {
        while (cursor < items.length) {
          const currentItem = items[cursor++];
          await processSingleItem(currentItem);
        }
      }

      const workers = Array.from(
        { length: Math.min(CONCURRENCY, items.length) },
        worker
      );
      await Promise.all(workers);

      isProcessing = false;
      updateSummary();
      updateControlsState();
    }

    // Unduh satu file dengan nama .png (contoh: foto1.jpg -> foto1.png)
    function triggerSingleDownload(item) {
      if (!item.resultBlob) return;

      const tempUrl = URL.createObjectURL(item.resultBlob);
      const link = document.createElement('a');
      link.href = tempUrl;
      link.download = item.outputName;
      document.body.appendChild(link);
      link.click();
      link.remove();

      setTimeout(() => URL.revokeObjectURL(tempUrl), 1500);
    }

    // Unduh semua hasil .png sekaligus dengan jeda singkat antar file
    async function downloadAllFiles() {
      const completedItems = items.filter((it) => it.status === 'done' && it.resultBlob);
      if (!completedItems.length) return;

      downloadAllBtn.disabled = true;

      for (let i = 0; i < completedItems.length; i++) {
        triggerSingleDownload(completedItems[i]);
        summaryEl.textContent = `Mengunduh ${i + 1} dari ${completedItems.length}...`;
        await new Promise((resolve) => setTimeout(resolve, 250));
      }

      updateSummary();
      updateControlsState();
    }

    processBtn.addEventListener('click', runBatchProcess);
    downloadAllBtn.addEventListener('click', downloadAllFiles);
    clearBtn.addEventListener('click', clearAllMemory);

    window.addEventListener('pagehide', clearAllMemory);
  </script>
</body>
</html>
