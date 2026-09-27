# formasite 
<!doctype html>
<html lang="ru">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>forma. — персональный план ухода</title>
  <meta name="description" content="Персональный план ухода и стиля. Загрузите фото и получите рекомендации.">
  <style>
    :root {
      --bg: #f5f3ef;
      --surface: #fffefa;
      --text: #25261f;
      --muted: #77786f;
      --line: #e8e5dd;
      --green: #596b50;
      --green-dark: #42523a;
      --pale: #e9eee5;
      --radius: 20px;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font: 16px/1.5 Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    button, input { font: inherit; }

    .wrap {
      width: min(1080px, calc(100% - 36px));
      margin: 0 auto;
      padding: 26px 0 48px;
    }

    header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 58px;
    }

    .brand {
      font-size: 22px;
      font-weight: 800;
      letter-spacing: -1.2px;
    }

    .brand span { color: var(--green); }

    .header-note {
      color: var(--muted);
      font-size: 13px;
    }

    .hero { max-width: 700px; margin-bottom: 34px; }

    .eyebrow {
      color: var(--green);
      font-size: 12px;
      font-weight: 800;
      letter-spacing: 1.6px;
      text-transform: uppercase;
    }

    h1 {
      margin: 12px 0;
      font-size: clamp(40px, 7vw, 68px);
      line-height: 1;
      letter-spacing: -3.5px;
    }

    .hero p {
      max-width: 580px;
      margin: 16px 0 0;
      color: var(--muted);
      font-size: 17px;
    }

    .columns {
      display: grid;
      grid-template-columns: 1.1fr .9fr;
      gap: 18px;
      align-items: start;
    }

    .card {
      padding: 24px;
      border: 1px solid var(--line);
      border-radius: var(--radius);
      background: var(--surface);
      box-shadow: 0 12px 35px rgba(35, 35, 28, .035);
    }

    .card h2 {
      margin: 0 0 5px;
      font-size: 21px;
      letter-spacing: -.5px;
    }

    .muted {
      margin: 0 0 19px;
      color: var(--muted);
      font-size: 14px;
    }

    .dropzone {
      display: grid;
      min-height: 245px;
      place-items: center;
      padding: 20px;
      overflow: hidden;
      border: 1.5px dashed #c9c8be;
      border-radius: 16px;
      background: #faf9f5;
      text-align: center;
      cursor: pointer;
      transition: border-color .2s, background .2s;
    }

    .dropzone:hover {
      border-color: var(--green);
      background: #f7f8f3;
    }

    .upload-copy { pointer-events: none; }

    .upload-icon {
      display: grid;
      width: 48px;
      height: 48px;
      place-items: center;
      margin: 0 auto 12px;
      border-radius: 15px;
      background: var(--pale);
      color: var(--green-dark);
      font-size: 26px;
    }

    .upload-copy strong { display: block; margin-bottom: 4px; }
    .upload-copy small { color: var(--muted); }

    #photo { display: none; }

    #preview {
      display: none;
      width: 100%;
      max-height: 330px;
      object-fit: contain;
      border-radius: 12px;
    }

    .consent {
      display: flex;
      gap: 10px;
      align-items: flex-start;
      margin: 16px 0;
      color: var(--muted);
      font-size: 13px;
    }

    .consent input {
      flex: 0 0 auto;
      margin-top: 4px;
      accent-color: var(--green);
    }

    .button {
      width: 100%;
      padding: 14px 18px;
      border: 0;
      border-radius: 12px;
      background: var(--green);
      color: white;
      font-weight: 750;
      cursor: pointer;
      transition: background .2s, opacity .2s, transform .2s;
    }

    .button:hover:not(:disabled) {
      background: var(--green-dark);
      transform: translateY(-1px);
    }

    .button:disabled { opacity: .45; cursor: not-allowed; }

    .privacy-note, .footnote {
      color: var(--muted);
      font-size: 12px;
    }

    .privacy-note { margin: 12px 0 0; }

    .side-card { margin-bottom: 18px; }

    .feature {
      display: flex;
      gap: 12px;
      margin-top: 16px;
    }

    .feature-icon {
      display: grid;
      flex: 0 0 30px;
      width: 30px;
      height: 30px;
      place-items: center;
      border-radius: 10px;
      background: var(--pale);
      color: var(--green-dark);
      font-size: 13px;
      font-weight: 800;
    }

    .feature strong { display: block; font-size: 14px; }
    .feature span { color: var(--muted); font-size: 13px; }

    .results {
      display: none;
      margin-top: 22px;
      padding-top: 22px;
      border-top: 1px solid var(--line);
    }

    .results-intro {
      color: var(--muted);
      font-size: 13px;
    }

    .metrics {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
      margin: 16px 0 20px;
    }

    .metric {
      min-height: 83px;
      padding: 13px;
      border: 1px solid var(--line);
      border-radius: 13px;
      background: white;
    }

    .metric span {
      display: block;
      margin-bottom: 5px;
      color: var(--muted);
      font-size: 12px;
    }

    .metric strong { font-size: 15px; }

    .recommendations {
      padding-left: 19px;
      color: #45463f;
      font-size: 14px;
    }

    .recommendations li { margin: 8px 0; }

    .premium {
      margin-top: 20px;
      padding: 20px;
      border-radius: 16px;
      background: #272a22;
      color: white;
    }

    .premium p {
      margin: 7px 0 15px;
      color: #d1d2ca;
      font-size: 14px;
    }

    .premium .button {
      background: #e7ecdf;
      color: #293124;
    }

    .premium .button:hover:not(:disabled) { background: white; }

    .disclaimer {
      max-width: 760px;
      margin: 26px auto 0;
      color: var(--muted);
      font-size: 12px;
      text-align: center;
    }

    @media (max-width: 760px) {
      header { margin-bottom: 42px; }
      .columns { grid-template-columns: 1fr; }
      .card { padding: 19px; }
      h1 { letter-spacing: -2.2px; }
    }
  </style>
</head>
<body>
  <main class="wrap">
    <header>
      <div class="brand">forma<span>.</span></div>
      <div class="header-note">Уход за собой — без сложностей</div>
    </header>

    <section class="hero">
      <div class="eyebrow">Персональный разбор</div>
      <h1>Подчеркни свою естественную внешность</h1>
      <p>Получи понятные идеи по уходу, стилю и ежедневным привычкам — в одном месте.</p>
    </section>

    <div class="columns">
      <section class="card">
        <h2>Начни с фото</h2>
        <p class="muted">Для снимка выбери ровный свет, нейтральное выражение лица и ракурс анфас.</p>

        <label class="dropzone" for="photo">
          <div class="upload-copy" id="uploadCopy">
            <div class="upload-icon">＋</div>
            <strong>Нажми, чтобы выбрать фото</strong>
            <small>JPG, PNG или WebP</small>
          </div>
          <img id="preview" alt="Предпросмотр выбранного фото">
        </label>
        <input id="photo" type="file" accept="image/jpeg,image/png,image/webp">

        <label class="consent">
          <input id="consent" type="checkbox">
          <span>Мне исполнилось 18 лет. Я понимаю, что в этой версии сайта показывается демонстрационный пример, а не настоящий анализ лица.</span>
        </label>

        <button class="button" id="showResults" disabled>Посмотреть пример результата</button>
        <p class="privacy-note">Фото остаётся в браузере: сайт не загружает его на сервер.</p>

        <section class="results" id="results" aria-live="polite">
          <h2>Твой план на каждый день</h2>
          <p class="results-intro">Демонстрационный экран — показатели ниже не рассчитаны по фотографии.</p>

          <div class="metrics">
            <div class="metric"><span>Фокус</span><strong>Базовый уход</strong></div>
            <div class="metric"><span>Стиль</span><strong>Подчеркнуть свои черты</strong></div>
            <div class="metric"><span>Фото</span><strong>Мягкий естественный свет</strong></div>
            <div class="metric"><span>Ритм</span><strong>Регулярные привычки</strong></div>
          </div>

          <strong>Попробуй сегодня</strong>
          <ul class="recommendations">
            <li>Утром используй мягкое очищение и увлажняющий крем.</li>
            <li>Подбирай причёску и аксессуары под свой вкус и образ жизни.</li>
            <li>Для фото поставь камеру на уровень глаз и встань лицом к окну.</li>
            <li>Поддерживай регулярный сон и привычный режим ухода.</li>
          </ul>

          <div class="premium">
            <strong>Расширенный план — 2 €</strong>
            <p>Дополнительные идеи по уходу и стилю, подборки и трекер ежедневных привычек.</p>
            <button class="button" id="premiumButton">Открыть премиум</button>
          </div>
        </section>
      </section>

      <aside>
        <section class="card side-card">
          <h2>Что будет на сайте</h2>
          <div class="feature">
            <div class="feature-icon">1</div>
            <div><strong>Понятный разбор</strong><span>Без сравнений с другими людьми и оценок «идеальности».</span></div>
          </div>
          <div class="feature">
            <div class="feature-icon">2</div>
            <div><strong>Практичные рекомендации</strong><span>Простые идеи, которые легко добавить в повседневную жизнь.</span></div>
          </div>
          <div class="feature">
            <div class="feature-icon">3</div>
            <div><strong>Премиум-функции</strong><span>Расширенный план можно будет открыть за 2 € после подключения оплаты.</span></div>
          </div>
        </section>

        <section class="card">
          <h2>Ограничения анализа</h2>
          <p class="muted" style="margin: 8px 0 0">
            Фотография не позволяет достоверно определить здоровье или предсказать, как изменится внешность. Эта версия сайта не анализирует костную структуру и симметрию.
          </p>
        </section>
      </aside>
    </div>

    <p class="disclaimer">
      Демонстрационный прототип. Не медицинская оценка и не настоящий анализ внешности. Оплата в этой версии не подключена.
    </p>
  </main>

  <script>
    const photoInput = document.querySelector("#photo");
    const consentInput = document.querySelector("#consent");
    const showResultsButton = document.querySelector("#showResults");
    const preview = document.querySelector("#preview");
    const uploadCopy = document.querySelector("#uploadCopy");
    const results = document.querySelector("#results");

    let currentPreviewUrl = null;

    function updateButton() {
      showResultsButton.disabled = !(photoInput.files.length && consentInput.checked);
    }

    photoInput.addEventListener("change", () => {
      results.style.display = "none";

      const file = photoInput.files[0];
      if (!file) {
        preview.style.display = "none";
        uploadCopy.style.display = "block";
        updateButton();
        return;
      }

      const allowedTypes = ["image/jpeg", "image/png", "image/webp"];
      if (!allowedTypes.includes(file.type)) {
        alert("Выбери изображение в формате JPG, PNG или WebP.");
        photoInput.value = "";
        updateButton();
        return;
      }

      if (currentPreviewUrl) URL.revokeObjectURL(currentPreviewUrl);
      currentPreviewUrl = URL.createObjectURL(file);

      preview.src = currentPreviewUrl;
      preview.style.display = "block";
      uploadCopy.style.display = "none";
      updateButton();
    });

    consentInput.addEventListener("change", updateButton);

    showResultsButton.addEventListener("click", () => {
      results.style.display = "block";
      results.scrollIntoView({ behavior: "smooth", block: "start" });
    });

    document.querySelector("#premiumButton").addEventListener("click", () => {
      alert("Премиум-раздел пока демонстрационный. Чтобы принимать оплату, нужно подключить платёжный сервис.");
    });

    window.addEventListener("beforeunload", () => {
      if (currentPreviewUrl) URL.revokeObjectURL(currentPreviewUrl);
    });
  </script>
</body>
</html>
