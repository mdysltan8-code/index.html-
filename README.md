# index.html-
Simple web game project
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>رضاهم غايتي 💚</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;800;900&family=Amiri:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #1a6b3a;
    --gold: #c9a84c;
    --light-green: #2d9b5a;
    --cream: #fdf8ef;
    --dark: #0f2419;
    --soft: #e8f5ee;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Tajawal', sans-serif;
    background: var(--cream);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* HEADER */
  .header {
    background: linear-gradient(135deg, var(--dark) 0%, var(--green) 60%, var(--light-green) 100%);
    padding: 30px 20px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute;
    inset: 0;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .header-badge {
    display: inline-block;
    background: rgba(201,168,76,0.2);
    border: 1px solid var(--gold);
    color: var(--gold);
    padding: 6px 18px;
    border-radius: 20px;
    font-size: 13px;
    margin-bottom: 15px;
    letter-spacing: 1px;
  }
  .header h1 {
    font-family: 'Amiri', serif;
    font-size: clamp(28px, 6vw, 52px);
    color: #fff;
    font-weight: 700;
    text-shadow: 0 2px 20px rgba(0,0,0,0.3);
    margin-bottom: 8px;
  }
  .header .subtitle {
    color: rgba(255,255,255,0.75);
    font-size: 15px;
    margin-bottom: 20px;
  }
  .credits {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
    margin-top: 15px;
  }
  .credit-item {
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.2);
    border-radius: 12px;
    padding: 8px 16px;
    color: rgba(255,255,255,0.9);
    font-size: 13px;
    text-align: center;
  }
  .credit-item span {
    display: block;
    color: var(--gold);
    font-size: 11px;
    margin-bottom: 2px;
  }

  /* MAIN */
  .main {
    max-width: 900px;
    margin: 0 auto;
    padding: 30px 15px 60px;
  }

  /* SCREEN SYSTEM */
  .screen { display: none; }
  .screen.active { display: block; }

  /* WELCOME SCREEN */
  .welcome-card {
    background: white;
    border-radius: 24px;
    padding: 40px 30px;
    text-align: center;
    box-shadow: 0 8px 40px rgba(26,107,58,0.1);
    border: 1px solid rgba(26,107,58,0.1);
  }
  .welcome-icon {
    font-size: 80px;
    margin-bottom: 20px;
    display: block;
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.05)} }
  .welcome-card h2 {
    font-family: 'Amiri', serif;
    font-size: 28px;
    color: var(--dark);
    margin-bottom: 12px;
  }
  .welcome-card p {
    color: #555;
    font-size: 16px;
    line-height: 1.8;
    margin-bottom: 30px;
  }
  .menu-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 15px;
    margin-top: 20px;
  }
  .menu-btn {
    background: linear-gradient(135deg, var(--soft), white);
    border: 2px solid var(--green);
    border-radius: 16px;
    padding: 20px 15px;
    cursor: pointer;
    transition: all 0.3s;
    text-align: center;
    font-family: 'Tajawal', sans-serif;
  }
  .menu-btn:hover {
    background: var(--green);
    color: white;
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(26,107,58,0.3);
  }
  .menu-btn .btn-icon { font-size: 32px; display: block; margin-bottom: 8px; }
  .menu-btn .btn-title { font-weight: 700; font-size: 15px; color: var(--dark); }
  .menu-btn:hover .btn-title { color: white; }
  .menu-btn .btn-desc { font-size: 12px; color: #888; margin-top: 4px; }
  .menu-btn:hover .btn-desc { color: rgba(255,255,255,0.8); }

  /* CONTENT CARDS */
  .content-card {
    background: white;
    border-radius: 24px;
    padding: 35px 25px;
    box-shadow: 0 8px 40px rgba(26,107,58,0.1);
    border: 1px solid rgba(26,107,58,0.1);
    animation: fadeIn 0.4s ease;
  }
  @keyframes fadeIn { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
  .card-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 25px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--soft);
  }
  .card-icon { font-size: 40px; }
  .card-header h2 {
    font-family: 'Amiri', serif;
    font-size: 24px;
    color: var(--dark);
  }

  /* VERSE BOX */
  .verse-box {
    background: linear-gradient(135deg, var(--dark), var(--green));
    border-radius: 16px;
    padding: 25px;
    margin-bottom: 20px;
    color: white;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .verse-box::before {
    content: '❝';
    position: absolute;
    top: -10px;
    right: 15px;
    font-size: 80px;
    opacity: 0.1;
    font-family: serif;
  }
  .verse-box .arabic-text {
    font-family: 'Amiri', serif;
    font-size: 20px;
    line-height: 2;
    margin-bottom: 12px;
  }
  .verse-box .source {
    color: var(--gold);
    font-size: 13px;
    font-weight: 700;
  }
  .hadith-box {
    background: linear-gradient(135deg, #2c4a1e, #1a6b3a);
    border-right: 4px solid var(--gold);
    border-radius: 12px;
    padding: 20px;
    color: white;
    margin-bottom: 15px;
  }
  .hadith-box .arabic-text {
    font-family: 'Amiri', serif;
    font-size: 18px;
    line-height: 2;
    margin-bottom: 8px;
  }
  .hadith-box .source { color: var(--gold); font-size: 13px; }

  /* DAILY TIPS */
  .tips-grid {
    display: grid;
    gap: 12px;
  }
  .tip-item {
    background: var(--soft);
    border-radius: 12px;
    padding: 15px 18px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
    border-right: 3px solid var(--green);
    transition: all 0.3s;
    cursor: pointer;
  }
  .tip-item:hover {
    background: var(--green);
    color: white;
    transform: translateX(-4px);
  }
  .tip-item .tip-num {
    background: var(--green);
    color: white;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    font-size: 14px;
    flex-shrink: 0;
  }
  .tip-item:hover .tip-num { background: white; color: var(--green); }
  .tip-item .tip-text { font-size: 15px; line-height: 1.7; padding-top: 4px; }

  /* DUA */
  .dua-box {
    background: linear-gradient(160deg, #f8f4e8, #fff8e1);
    border: 2px solid var(--gold);
    border-radius: 20px;
    padding: 30px;
    text-align: center;
    margin-bottom: 20px;
  }
  .dua-box .dua-arabic {
    font-family: 'Amiri', serif;
    font-size: 22px;
    color: var(--dark);
    line-height: 2.2;
    margin-bottom: 15px;
  }
  .dua-box .dua-meaning {
    color: #666;
    font-size: 14px;
    line-height: 1.8;
    border-top: 1px solid rgba(201,168,76,0.3);
    padding-top: 12px;
    margin-top: 5px;
  }

  /* STORIES */
  .story-card {
    background: var(--soft);
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 15px;
    border-right: 4px solid var(--light-green);
    transition: all 0.3s;
  }
  .story-card:hover { box-shadow: 0 4px 20px rgba(26,107,58,0.15); }
  .story-title {
    font-weight: 800;
    color: var(--dark);
    font-size: 17px;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .story-text { color: #444; font-size: 14px; line-height: 1.9; }
  .story-moral {
    background: var(--green);
    color: white;
    padding: 10px 15px;
    border-radius: 8px;
    font-size: 13px;
    margin-top: 12px;
    font-weight: 600;
  }

  /* REPENTANCE */
  .repent-steps {
    display: grid;
    gap: 15px;
  }
  .repent-step {
    display: flex;
    gap: 15px;
    align-items: flex-start;
    background: white;
    border-radius: 14px;
    padding: 18px;
    box-shadow: 0 2px 12px rgba(0,0,0,0.06);
    border: 1px solid var(--soft);
  }
  .step-icon {
    font-size: 30px;
    width: 50px;
    height: 50px;
    background: var(--soft);
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  .step-content h3 { color: var(--dark); font-size: 16px; margin-bottom: 6px; }
  .step-content p { color: #555; font-size: 14px; line-height: 1.7; }

  /* QUIZ */
  .quiz-container { }
  .question-box {
    background: linear-gradient(135deg, var(--dark), var(--green));
    border-radius: 16px;
    padding: 25px;
    color: white;
    text-align: center;
    margin-bottom: 20px;
  }
  .question-num { color: var(--gold); font-size: 13px; margin-bottom: 10px; }
  .question-text { font-family: 'Amiri', serif; font-size: 20px; line-height: 1.8; }
  .options-grid { display: grid; gap: 12px; }
  .option-btn {
    background: white;
    border: 2px solid var(--soft);
    border-radius: 12px;
    padding: 15px 20px;
    cursor: pointer;
    font-family: 'Tajawal', sans-serif;
    font-size: 15px;
    text-align: right;
    transition: all 0.3s;
    color: var(--dark);
  }
  .option-btn:hover { border-color: var(--green); background: var(--soft); }
  .option-btn.correct { background: #d4edda; border-color: #28a745; color: #155724; }
  .option-btn.wrong { background: #f8d7da; border-color: #dc3545; color: #721c24; }
  .feedback-box {
    display: none;
    padding: 15px 20px;
    border-radius: 12px;
    margin-top: 15px;
    font-size: 15px;
    font-weight: 600;
    text-align: center;
    animation: fadeIn 0.3s;
  }
  .feedback-box.show { display: block; }
  .feedback-box.correct { background: #d4edda; color: #155724; }
  .feedback-box.wrong { background: #f8d7da; color: #721c24; }
  .score-display {
    text-align: center;
    padding: 30px;
    background: white;
    border-radius: 20px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  }
  .score-num { font-size: 60px; font-weight: 900; color: var(--green); }
  .score-msg { font-size: 18px; color: var(--dark); margin: 10px 0; }

  /* BUTTONS */
  .btn-primary {
    background: linear-gradient(135deg, var(--green), var(--light-green));
    color: white;
    border: none;
    border-radius: 12px;
    padding: 14px 30px;
    font-family: 'Tajawal', sans-serif;
    font-size: 16px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s;
    width: 100%;
    margin-top: 15px;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(26,107,58,0.35); }
  .btn-back {
    background: var(--soft);
    color: var(--dark);
    border: 2px solid var(--green);
    border-radius: 12px;
    padding: 10px 22px;
    font-family: 'Tajawal', sans-serif;
    font-size: 15px;
    cursor: pointer;
    margin-bottom: 20px;
    transition: all 0.3s;
  }
  .btn-back:hover { background: var(--green); color: white; }

  /* PROGRESS BAR */
  .progress-bar {
    background: var(--soft);
    border-radius: 10px;
    height: 8px;
    margin-bottom: 20px;
    overflow: hidden;
  }
  .progress-fill {
    background: linear-gradient(90deg, var(--green), var(--light-green));
    height: 100%;
    border-radius: 10px;
    transition: width 0.4s ease;
  }

  /* DECORATION */
  .section-divider {
    text-align: center;
    color: var(--gold);
    font-size: 24px;
    margin: 20px 0;
    letter-spacing: 8px;
  }

  .badge { 
    display: inline-block;
    background: var(--soft);
    color: var(--green);
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: 700;
    border: 1px solid var(--green);
    margin-bottom: 15px;
  }

  @media (max-width: 600px) {
    .menu-grid { grid-template-columns: 1fr 1fr; }
    .credits { gap: 10px; }
  }
</style>
</head>
<body>

<div class="header">
  <div class="header-badge">🌿 لعبة تعليمية إسلامية</div>
  <h1>رضاهم غايتي 💚</h1>
  <p class="subtitle">رحلة تعليمية في فضل بر الوالدين</p>
  <div class="credits">
    <div class="credit-item"><span>إعداد الطالبة</span>مدى سلطان الجهمي</div>
    <div class="credit-item"><span>إشراف المعلمة</span>نمشه الجهمي</div>
    <div class="credit-item"><span>مديرة المدرسة</span>سميرة السعدي</div>
    <div class="credit-item"><span>📚</span>مدرسة المتوسطة والثانوية المدراء</div>
  </div>
</div>

<div class="main">

  <!-- WELCOME SCREEN -->
  <div class="screen active" id="screen-home">
    <div class="welcome-card">
      <span class="welcome-icon">🤲</span>
      <h2>أهلاً بك في رحلة البر والإحسان</h2>
      <p>اكتشف فضل بر الوالدين من خلال الآيات الكريمة والأحاديث الشريفة والقصص المؤثرة، وتعلم كيف تكون برّاً بوالديك كل يوم.</p>
      <div class="section-divider">✦ ✦ ✦</div>
      <div class="menu-grid">
        <button class="menu-btn" onclick="showScreen('screen-verses')">
          <span class="btn-icon">📖</span>
          <div class="btn-title">آية وحديث</div>
          <div class="btn-desc">من القرآن والسنة</div>
        </button>
        <button class="menu-btn" onclick="showScreen('screen-daily')">
          <span class="btn-icon">🌟</span>
          <div class="btn-title">كيف أبرّ والديّ؟</div>
          <div class="btn-desc">نصائح يومية</div>
        </button>
        <button class="menu-btn" onclick="showScreen('screen-dua')">
          <span class="btn-icon">🤲</span>
          <div class="btn-title">دعاء للوالدين</div>
          <div class="btn-desc">أجمل الأدعية</div>
        </button>
        <button class="menu-btn" onclick="showScreen('screen-stories')">
          <span class="btn-icon">📚</span>
          <div class="btn-title">قصص مؤثرة</div>
          <div class="btn-desc">عبر ودروس</div>
        </button>
        <button class="menu-btn" onclick="showScreen('screen-repent')">
          <span class="btn-icon">💫</span>
          <div class="btn-title">ماذا أفعل إذا قصّرت؟</div>
          <div class="btn-desc">طريق التوبة</div>
        </button>
        <button class="menu-btn" onclick="showScreen('screen-quiz')">
          <span class="btn-icon">🎯</span>
          <div class="btn-title">اختبر معلوماتك</div>
          <div class="btn-desc">مسابقة ممتعة</div>
        </button>
      </div>
    </div>
  </div>

  <!-- VERSES SCREEN -->
  <div class="screen" id="screen-verses">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card">
      <div class="card-header">
        <span class="card-icon">📖</span>
        <h2>آيات وأحاديث في بر الوالدين</h2>
      </div>

      <div class="badge">من القرآن الكريم</div>

      <div class="verse-box">
        <div class="arabic-text">
          ﴿وَقَضَىٰ رَبُّكَ أَلَّا تَعْبُدُوا إِلَّا إِيَّاهُ وَبِالْوَالِدَيْنِ إِحْسَانًا ۚ إِمَّا يَبْلُغَنَّ عِندَكَ الْكِبَرَ أَحَدُهُمَا أَوْ كِلَاهُمَا فَلَا تَقُل لَّهُمَا أُفٍّ وَلَا تَنْهَرْهُمَا وَقُل لَّهُمَا قَوْلًا كَرِيمًا﴾
        </div>
        <div class="source">سورة الإسراء - الآية 23</div>
      </div>

      <div class="verse-box" style="background: linear-gradient(135deg, #1a3a6b, #2d5aa0); margin-bottom: 20px;">
        <div class="arabic-text">
          ﴿وَوَصَّيْنَا الْإِنسَانَ بِوَالِدَيْهِ حَمَلَتْهُ أُمُّهُ وَهْنًا عَلَىٰ وَهْنٍ وَفِصَالُهُ فِي عَامَيْنِ أَنِ اشْكُرْ لِي وَلِوَالِدَيْكَ إِلَيَّ الْمَصِيرُ﴾
        </div>
        <div class="source">سورة لقمان - الآية 14</div>
      </div>

      <div class="badge">من السنة النبوية الشريفة</div>

      <div class="hadith-box">
        <div class="arabic-text">
          ❝ رِضَا اللهِ فِي رِضَا الْوَالِدَيْنِ، وَسَخَطُ اللهِ فِي سَخَطِ الْوَالِدَيْنِ ❞
        </div>
        <div class="source">رواه الترمذي وصححه الألباني</div>
      </div>

      <div class="hadith-box">
        <div class="arabic-text">
          ❝ جَاءَ رَجُلٌ إِلَى النَّبِيِّ ﷺ فَقَالَ: مَن أَحَقُّ النَّاسِ بِحُسْنِ صَحَابَتِي؟ قَالَ: أُمُّكَ. قَالَ: ثُمَّ مَن؟ قَالَ: أُمُّكَ. قَالَ: ثُمَّ مَن؟ قَالَ: أُمُّكَ. قَالَ: ثُمَّ مَن؟ قَالَ: أَبُوكَ ❞
        </div>
        <div class="source">متفق عليه</div>
      </div>

      <div class="hadith-box">
        <div class="arabic-text">
          ❝ أَلَا أُنَبِّئُكُمْ بِأَكْبَرِ الْكَبَائِرِ؟ قُلْنَا: بَلَى يَا رَسُولَ اللهِ، قَالَ: الإِشْرَاكُ بِاللهِ، وَعُقُوقُ الْوَالِدَيْنِ ❞
        </div>
        <div class="source">متفق عليه</div>
      </div>
    </div>
  </div>

  <!-- DAILY TIPS -->
  <div class="screen" id="screen-daily">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card">
      <div class="card-header">
        <span class="card-icon">🌟</span>
        <h2>كيف أبرّ والديّ يومياً؟</h2>
      </div>
      <p style="color:#666; margin-bottom:20px;">إليكِ أجمل الطرق العملية لبر الوالدين في حياتك اليومية:</p>

      <div class="tips-grid">
        <div class="tip-item">
          <div class="tip-num">1</div>
          <div class="tip-text">ابدأ يومك بإلقاء السلام عليهما بحرارة وابتسامة صادقة — فالسلام سنة وبر.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">2</div>
          <div class="tip-text">أطع أوامرهما في غير معصية الله، حتى وإن لم تفهم الحكمة في البداية.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">3</div>
          <div class="tip-text">تكلم معهما بنبرة هادئة ومحبة، لا ترفع صوتك ولا تقاطعهما أثناء الكلام.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">4</div>
          <div class="tip-text">بادر لمساعدة أمك في أعمال المنزل دون انتظار الطلب — هذا من أعظم البر.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">5</div>
          <div class="tip-text">أخبرهما بأخبارك وأحداث يومك، يسعدان حين تشاركهما تفاصيل حياتك.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">6</div>
          <div class="tip-text">قبّل رأس والدك ويد والدتك كل يوم — هذا الفعل البسيط يريح قلبيهما كثيراً.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">7</div>
          <div class="tip-text">ادعُ لهما في صلواتك سراً وعلناً، خاصة في السجود وأوقات الإجابة.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">8</div>
          <div class="tip-text">لا تعقد مقارنات مؤلمة أمامهما أو تُشعرهما بالتقصير، قدّر جهدهما مهما كان.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">9</div>
          <div class="tip-text">إذا سافرا أو غابا تواصل معهما، واسألهما عن أحوالهما باهتمام حقيقي.</div>
        </div>
        <div class="tip-item">
          <div class="tip-num">10</div>
          <div class="tip-text">احرص على التفوق في دراستك وعبادتك — نجاحك يسعدهما أكثر من أي هدية مادية.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- DUA SCREEN -->
  <div class="screen" id="screen-dua">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card">
      <div class="card-header">
        <span class="card-icon">🤲</span>
        <h2>أدعية للوالدين الكريمين</h2>
      </div>

      <div class="dua-box">
        <div class="dua-arabic">
          رَّبِّ ارْحَمْهُمَا كَمَا رَبَّيَانِي صَغِيرًا
        </div>
        <div class="dua-meaning">اللهم ارحم والديّ واغمرهما بلطفك ورحمتك كما ربّياني وأحسنا تنشئتي منذ الصغر</div>
      </div>

      <div class="dua-box">
        <div class="dua-arabic">
          رَبِّ اغْفِرْ لِي وَلِوَالِدَيَّ وَلِلْمُؤْمِنِينَ يَوْمَ يَقُومُ الْحِسَابُ
        </div>
        <div class="dua-meaning">دعاء نبي الله إبراهيم عليه السلام — سورة إبراهيم</div>
      </div>

      <div class="dua-box">
        <div class="dua-arabic">
          اللهم اغفر لأبي وأمي واجزهما عني خير الجزاء، وارزقهما الصحة والعافية، وأسعدهما في الدنيا والآخرة
        </div>
        <div class="dua-meaning">دعاء يومي جامع ومؤثر للوالدين</div>
      </div>

      <div class="dua-box" style="border-color: var(--light-green);">
        <div class="dua-arabic">
          اللهم إن كان أبي أو أمي قد توفيا فاغفر لهما وارحمهما، وأكرم نزلهما، ووسع مدخلهما
        </div>
        <div class="dua-meaning">دعاء لمن توفي والداه أو أحدهما</div>
      </div>

      <div style="background: var(--soft); border-radius: 12px; padding: 15px; margin-top: 5px; text-align: center;">
        <p style="color: var(--dark); font-size: 14px; line-height: 1.8;">
          💡 أفضل أوقات الدعاء للوالدين: <strong>السجود في الصلاة</strong> - <strong>آخر الليل</strong> - <strong>بين الأذان والإقامة</strong> - <strong>يوم الجمعة</strong>
        </p>
      </div>
    </div>
  </div>

  <!-- STORIES SCREEN -->
  <div class="screen" id="screen-stories">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card">
      <div class="card-header">
        <span class="card-icon">📚</span>
        <h2>قصص مؤثرة في بر الوالدين</h2>
      </div>

      <div class="story-card">
        <div class="story-title">🌟 أويس القرني — البار الذي فاق الصحابة شرفاً</div>
        <div class="story-text">
          كان أويس القرني يريد أن يلقى النبي ﷺ بشوق عظيم، لكن والدته كانت مريضة لا تستطيع أن تسافر، فآثر البقاء لخدمتها على الهجرة. وقد أخبر النبي ﷺ أصحابه بفضله وقال: "إن استطعتم أن تسألوه أن يستغفر لكم فافعلوا" — وهو شرف لم ينله إلا القليل.
        </div>
        <div class="story-moral">✨ الدرس: بر الوالدين يرفع الدرجات ويفتح الأبواب التي لا يفتحها غيره</div>
      </div>

      <div class="story-card">
        <div class="story-title">🌊 الرجل الذي حمل أمه على ظهره</div>
        <div class="story-text">
          سأل رجل عبدالله بن عمر رضي الله عنهما: حملت أمي على ظهري وطفت بها سبعاً وأطعمتها من فمي، فهل وفّيتها حقها؟ فقال ابن عمر: لا، ولا بزفرة واحدة من زفراتها حين ولادتك — ولكن قد أحسنت، والله يثيبك على القليل الكثير.
        </div>
        <div class="story-moral">✨ الدرس: فضل الأم عظيم جداً لا يُعوَّض، فلا تقصّر في برها أبداً</div>
      </div>

      <div class="story-card">
        <div class="story-title">💫 سعد بن أبي وقاص وأمه الصابرة</div>
        <div class="story-text">
          لما أسلم سعد بن أبي وقاص رضي الله عنه، قالت أمه: والله لا آكل ولا أشرب حتى ترتد عن دينك أو أموت. فنزل قوله تعالى: ﴿وَإِن جَاهَدَاكَ عَلَىٰ أَن تُشْرِكَ بِي مَا لَيْسَ لَكَ بِهِ عِلْمٌ فَلَا تُطِعْهُمَا ۖ وَصَاحِبْهُمَا فِي الدُّنْيَا مَعْرُوفًا﴾ وأثنى الله على سعد بالصبر والحكمة.
        </div>
        <div class="story-moral">✨ الدرس: نطيع الوالدين في كل شيء ما لم يكن في معصية الله، ونحسن صحبتهما دائماً</div>
      </div>

      <div class="story-card">
        <div class="story-title">🌹 جريج العابد والدعاء الذي غيّر حياته</div>
        <div class="story-text">
          كان جريج عابداً في صومعته، فجاءت أمه تناديه وهو في صلاته، فقال: أجيب أمي أم ربي؟ فاستمر في صلاته ولم يجبها. فدعت عليه: اللهم لا تمته حتى يرى وجوه المومسات. فابتُلي بما ابتُليَ حتى ثبت براءته بمعجزة. فسألوه عن أمه فدعا لها وقال: اللهم ارض عن أمي.
        </div>
        <div class="story-moral">✨ الدرس: إجابة الوالدين تقدّم على كثير من النوافل، فلا تتهاون بندائهما</div>
      </div>
    </div>
  </div>

  <!-- REPENTANCE SCREEN -->
  <div class="screen" id="screen-repent">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card">
      <div class="card-header">
        <span class="card-icon">💫</span>
        <h2>ماذا أفعل إذا قصّرت في بر والديّ؟</h2>
      </div>
      <p style="color:#555; margin-bottom: 20px; font-size:15px; line-height:1.8;">
        لا تيأس... رحمة الله واسعة، وباب التوبة مفتوح دائماً. إليكِ خطوات عملية للعودة:
      </p>

      <div class="repent-steps">
        <div class="repent-step">
          <div class="step-icon">💔</div>
          <div class="step-content">
            <h3>أولاً: اعترف بالتقصير في نفسك</h3>
            <p>الخطوة الأولى هي الصدق مع النفس والاعتراف بأنك قصّرت، دون تبرير أو لوم للآخرين. هذا الإحساس بالذنب علامة صحة في القلب.</p>
          </div>
        </div>
        <div class="repent-step">
          <div class="step-icon">🤲</div>
          <div class="step-content">
            <h3>ثانياً: استغفر الله وتب إليه</h3>
            <p>قل: "اللهم إني أستغفرك من تقصيري في حق والديّ، وأتوب إليك" — التوبة الصادقة تمحو الذنوب وتبدلها حسنات.</p>
          </div>
        </div>
        <div class="repent-step">
          <div class="step-icon">🌹</div>
          <div class="step-content">
            <h3>ثالثاً: اعتذر لهما بصدق</h3>
            <p>قل لهما بكل تواضع: "أنا آسف، أعلم أني قصّرت معك، وأعدك بأن أتغير." — هذه الكلمات البسيطة تشفي جروحاً كثيرة.</p>
          </div>
        </div>
        <div class="repent-step">
          <div class="step-icon">🌱</div>
          <div class="step-content">
            <h3>رابعاً: ابدأ من الآن بالتغيير</h3>
            <p>ابدأ بخطوة صغيرة واحدة اليوم: قبّلة على رأس الأم، كلمة محبة للأب، مساعدة في العمل المنزلي — المهم أن تبدأ.</p>
          </div>
        </div>
        <div class="repent-step">
          <div class="step-icon">📿</div>
          <div class="step-content">
            <h3>خامساً: أكثر من الدعاء لهما</h3>
            <p>ادعُ لهما في كل صلاة، وخاصة في السجود. الدعاء للوالدين من أعظم البر، حتى بعد وفاتهما.</p>
          </div>
        </div>
        <div class="repent-step">
          <div class="step-icon">⭐</div>
          <div class="step-content">
            <h3>سادساً: استمر ولا تيأس من العودة</h3>
            <p>لو عدت للتقصير مرة أخرى فلا تستسلم — كلنا نخطئ، والمهم أن نعود دائماً. الله يحب التوابين ويحب المتطهرين.</p>
          </div>
        </div>
      </div>

      <div style="background: linear-gradient(135deg, var(--dark), var(--green)); border-radius: 16px; padding: 20px; margin-top: 20px; text-align: center; color: white;">
        <div style="font-family: 'Amiri', serif; font-size: 18px; margin-bottom: 8px;">
          ﴿إِنَّ اللَّهَ يُحِبُّ التَّوَّابِينَ وَيُحِبُّ الْمُتَطَهِّرِينَ﴾
        </div>
        <div style="color: var(--gold); font-size: 13px;">سورة البقرة - الآية 222</div>
      </div>
    </div>
  </div>

  <!-- QUIZ SCREEN -->
  <div class="screen" id="screen-quiz">
    <button class="btn-back" onclick="showScreen('screen-home')">↩ العودة للقائمة</button>
    <div class="content-card" id="quiz-content">
      <div class="card-header">
        <span class="card-icon">🎯</span>
        <h2>اختبري معلوماتك!</h2>
      </div>
      <div class="progress-bar"><div class="progress-fill" id="quiz-progress" style="width:0%"></div></div>
      <div class="quiz-container" id="quiz-area"></div>
    </div>
  </div>

</div>

<script>
const questions = [
  {
    q: "في أي سورة وردت الآية: ﴿وَقَضَىٰ رَبُّكَ أَلَّا تَعْبُدُوا إِلَّا إِيَّاهُ وَبِالْوَالِدَيْنِ إِحْسَانًا﴾؟",
    opts: ["سورة لقمان", "سورة الإسراء", "سورة البقرة", "سورة النساء"],
    ans: 1,
    exp: "وردت هذه الآية في سورة الإسراء الآية 23، وهي تقرن حق الوالدين بالعبادة مباشرة."
  },
  {
    q: "كم مرة ذكر النبي ﷺ الأمَّ حين سُئل عن أحق الناس بالصحبة؟",
    opts: ["مرة واحدة", "مرتين", "ثلاث مرات", "أربع مرات"],
    ans: 2,
    exp: "قال ﷺ: 'أمك' ثلاث مرات ثم في الرابعة قال 'أبوك' — مما يدل على مكانة الأم العظيمة."
  },
  {
    q: "من الصحابي الجليل الذي قال عنه النبي ﷺ: 'من سرّه أن ينظر إلى رجل من أهل الجنة فلينظر إلى هذا'؟",
    opts: ["أبو هريرة", "أويس القرني", "سعد بن أبي وقاص", "عبدالله بن مسعود"],
    ans: 1,
    exp: "أويس القرني رضي الله عنه كان بارّاً بوالدته بشكل استثنائي حتى أثنى عليه النبي ﷺ رغم أنه لم يلقه."
  },
  {
    q: "ما أفضل ما يمكن للمسلم أن يهديه لوالديه بعد وفاتهما؟",
    opts: ["الصدقة الجارية عنهما", "الدعاء لهما", "الصيام عنهما", "كل ما سبق صحيح"],
    ans: 3,
    exp: "كل هذه الأعمال تصل للوالدين المتوفين، والدعاء والصدقة والحج عنهما من أعظم البر بعد الوفاة."
  },
  {
    q: "ما الذي قرنه الله تعالى بعبادته في سورة الإسراء؟",
    opts: ["صلة الأرحام", "بر الوالدين", "الصدق في القول", "حسن الجوار"],
    ans: 1,
    exp: "قال الله تعالى: ﴿وقضى ربك ألا تعبدوا إلا إياه وبالوالدين إحساناً﴾ فقرن الإحسان للوالدين بعبادته مباشرة."
  },
  {
    q: "ما كبيرة الكبائر التي ذكرها النبي ﷺ بعد الإشراك بالله؟",
    opts: ["الكذب", "قطع الرحم", "عقوق الوالدين", "شهادة الزور"],
    ans: 2,
    exp: "قال ﷺ: 'ألا أنبئكم بأكبر الكبائر؟ الإشراك بالله وعقوق الوالدين' — فعقوق الوالدين من أشد الكبائر."
  },
  {
    q: "ما الدعاء القرآني المأثور الذي يدعو به المسلم لوالديه؟",
    opts: ["رب اجعلني صادقاً", "رب ارحمهما كما ربياني صغيراً", "رب زدني علماً", "رب اغفر لي"],
    ans: 1,
    exp: "﴿رَّبِّ ارْحَمْهُمَا كَمَا رَبَّيَانِي صَغِيرًا﴾ — سورة الإسراء، وهو دعاء جامع لوالدين الحي والميت."
  }
];

let currentQ = 0;
let score = 0;
let answered = false;

function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  if (id === 'screen-quiz') {
    currentQ = 0; score = 0;
    renderQuestion();
  }
  window.scrollTo(0, 0);
}

function renderQuestion() {
  answered = false;
  const area = document.getElementById('quiz-area');
  if (currentQ >= questions.length) {
    const pct = Math.round(score/questions.length*100);
    let msg = '';
    if(pct === 100) msg = '🏆 ممتاز جداً! أنت نجمة البر والإحسان!';
    else if(pct >= 70) msg = '🌟 أحسنت! لديكِ معرفة جيدة بفضل بر الوالدين';
    else if(pct >= 50) msg = '💪 جيد! راجعي المحتوى مرة أخرى لتزيدي معلوماتك';
    else msg = '📚 تحتاجين للمزيد من الدراسة، راجعي الأقسام الأخرى أولاً';
    
    area.innerHTML = `
      <div class="score-display">
        <div style="font-size:60px; margin-bottom: 15px;">${pct >= 70 ? '🏆' : pct >= 50 ? '📚' : '💪'}</div>
        <div class="score-num">${score}/${questions.length}</div>
        <div class="score-msg">${msg}</div>
        <div style="color:#888; font-size: 14px; margin: 10px 0">نسبة الإجابات الصحيحة: ${pct}%</div>
      </div>
      <button class="btn-primary" onclick="showScreen('screen-home')">العودة للقائمة الرئيسية 🏠</button>
      <button class="btn-primary" style="margin-top:10px; background: linear-gradient(135deg, #c9a84c, #d4b96a);" onclick="currentQ=0;score=0;renderQuestion()">إعادة الاختبار 🔄</button>
    `;
    return;
  }

  document.getElementById('quiz-progress').style.width = (currentQ/questions.length*100)+'%';
  const q = questions[currentQ];
  area.innerHTML = `
    <div class="question-box">
      <div class="question-num">سؤال ${currentQ+1} من ${questions.length}</div>
      <div class="question-text">${q.q}</div>
    </div>
    <div class="options-grid">
      ${q.opts.map((o,i)=>`<button class="option-btn" onclick="answer(${i})">${o}</button>`).join('')}
    </div>
    <div class="feedback-box" id="feedback"></div>
  `;
}

function answer(idx) {
  if (answered) return;
  answered = true;
  const q = questions[currentQ];
  const btns = document.querySelectorAll('.option-btn');
  const fb = document.getElementById('feedback');
  
  btns[q.ans].classList.add('correct');
  if (idx === q.ans) {
    score++;
    fb.textContent = '✅ أحسنتِ! إجابة صحيحة. ' + q.exp;
    fb.className = 'feedback-box show correct';
  } else {
    btns[idx].classList.add('wrong');
    fb.textContent = '❌ الإجابة الصحيحة: ' + q.opts[q.ans] + '. ' + q.exp;
    fb.className = 'feedback-box show wrong';
  }
  
  // Add next button
  const nextBtn = document.createElement('button');
  nextBtn.className = 'btn-primary';
  nextBtn.textContent = currentQ+1 < questions.length ? 'السؤال التالي ←' : 'عرض النتيجة 🏆';
  nextBtn.onclick = () => { currentQ++; renderQuestion(); };
  document.getElementById('quiz-area').appendChild(nextBtn);
}
</script>
</body>
</html>
