<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Абайдың "Толық Адам" ілімі</title>
    <style>
        @import url('dd.png');
        
        body {
            margin: 0;
            padding: 0;
            font-family: 'Noto Serif', serif;
            background: linear-gradient(135deg, #0d0d4b 0%, #16213e 100%);
            color: #fff;
            overflow-x: hidden;
            perspective: 1000px;
        }
        
        .book {
            position: relative;
            width: 90%;
            max-width: 1000px;
            height: 700px;
            margin: 50px auto;
            box-shadow: 0 0 50px rgba(0, 195, 255, 0.5);
            background: url('2222.png') center/cover no-repeat fixed;
            border-radius: 10px;
            overflow: hidden;
            transform-style: preserve-3d;
            border: 2px solid rgba(0, 212, 255, 0.3);
        }
        
        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: rgba(15, 32, 39, 0.85);
            padding: 50px;
            box-sizing: border-box;
            box-shadow: inset 0 0 30px rgba(0, 212, 255, 0.2);
            display: none;
            transform-origin: left center;
            transition: transform 1s ease-in-out;
            border-left: 1px solid rgba(0, 212, 255, 0.2);
            border-right: 1px solid rgba(0, 212, 255, 0.2);
        }
        
        .page.active {
            display: block;
            z-index: 1;
            animation: fadeIn 0.5s ease-out;
        }
        
        .page.next {
            display: block;
            z-index: 0;
            transform: rotateY(180deg);
        }
        
        .page.prev {
            display: block;
            z-index: 0;
            transform: rotateY(-180deg);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .page-content {
            height: 100%;
            overflow-y: auto;
            padding-right: 20px;
            text-align: center; /* Барлық мәтіндерді ортаға туралау */
        }
        
        .slide-title {
            font-size: 36px;
            color: #00d4ff;
            margin-bottom: 30px;
            text-align: center;
            text-shadow: 0 0 10px rgba(0, 212, 255, 0.7);
            padding-bottom: 10px;
            border-bottom: 2px solid rgba(0, 212, 255, 0.5);
            position: relative;
        }
        
        .slide-title::after {
            content: "";
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, transparent, #00d4ff, transparent);
            box-shadow: 0 0 10px #00d4ff;
        }
        
        .slide-content {
            font-size: 20px;
            line-height: 1.8;
            color: #e6f7ff;
            text-align: center; /* Мәтіндерді ортаға туралау */
        }
        
        .highlight {
            color: #ffcc00;
            font-weight: bold;
            text-shadow: 0 0 5px rgba(255, 204, 0, 0.5);
        }
        
        .two-columns {
            display: flex;
            justify-content: space-between;
            margin: 20px auto; /* Ортаға туралау */
            max-width: 800px; /* Максималды ені */
        }
        
        .column {
            flex: 0 0 48%;
            padding: 15px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 212, 255, 0.2);
            text-align: center; /* Баған мәтіндерін ортаға туралау */
        }
        
        .table {
            width: 100%;
            max-width: 600px; /* Кестенің максималды ені */
            border-collapse: collapse;
            margin: 25px auto; /* Ортаға туралау */
            background-color: rgba(0, 0, 0, 0.3);
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
        }
        
        .table th, .table td {
            border: 1px solid rgba(0, 212, 255, 0.3);
            padding: 12px;
            text-align: center;
        }
        
        .table th {
            background: linear-gradient(135deg, #00b4db 0%, #0083b0 100%);
            color: white;
            text-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
        }
        
        .slide-image {
            width: 250px;
            height: 250px;
            border-radius: 50%;
            object-fit: cover;
            margin: 20px auto;
            display: block;
            border: 5px solid #00d4ff;
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.7);
            position: relative;
            z-index: 1;
        }
        
        .slide-image::before {
            content: "";
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(0,212,255,0.5) 0%, rgba(0,212,255,0) 70%);
            z-index: -1;
            animation: pulse 3s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(0.95); opacity: 0.7; }
            50% { transform: scale(1.05); opacity: 1; }
            100% { transform: scale(0.95); opacity: 0.7; }
        }
        
        .background-image {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            opacity: 0.1;
            z-index: -1;
            filter: blur(2px);
        }
        
        .navigation {
            position: fixed;
            bottom: 30px;
            width: 100%;
            display: flex;
            justify-content: center;
            z-index: 100;
        }
        
        .nav-btn {
            background: linear-gradient(135deg, #00b4db 0%, #0083b0 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            margin: 0 15px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 18px;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0, 180, 219, 0.4);
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        .nav-btn::before {
            content: "";
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                to bottom right,
                rgba(255, 255, 255, 0) 0%,
                rgba(255, 255, 255, 0) 45%,
                rgba(255, 255, 255, 0.2) 48%,
                rgba(255, 255, 255, 0.2) 52%,
                rgba(255, 255, 255, 0) 55%,
                rgba(255, 255, 255, 0) 100%
            );
            transform: rotate(30deg);
            animation: shine 3s infinite;
        }
        
        .nav-btn.home-btn {
            background: linear-gradient(135deg, #ff8a00 0%, #e52e71 100%);
            margin-left: 30px;
        }
        
        .nav-btn.home-btn::before {
            background: linear-gradient(
                to bottom right,
                rgba(255, 255, 255, 0) 0%,
                rgba(255, 255, 255, 0) 45%,
                rgba(255, 255, 255, 0.3) 48%,
                rgba(255, 255, 255, 0.3) 52%,
                rgba(255, 255, 255, 0) 55%,
                rgba(255, 255, 255, 0) 100%
            );
        }
        
        @keyframes shine {
            0% { transform: translateX(-100%) rotate(30deg); }
            100% { transform: translateX(100%) rotate(30deg); }
        }
        
        .nav-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 180, 219, 0.6);
        }
        
        .page-number {
            position: absolute;
            bottom: 20px;
            right: 30px;
            color: #00d4ff;
            font-size: 16px;
            font-style: italic;
            text-shadow: 0 0 5px rgba(0, 212, 255, 0.5);
        }
        
        .page::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('https://www.transparenttextures.com/patterns/old-paper.png');
            opacity: 0.1;
            pointer-events: none;
        }
        
        @keyframes glow {
            0% { box-shadow: 0 0 30px rgba(0, 212, 255, 0.5); }
            50% { box-shadow: 0 0 50px rgba(0, 212, 255, 0.8); }
            100% { box-shadow: 0 0 30px rgba(0, 212, 255, 0.5); }
        }
        
        .book {
            animation: glow 3s infinite;
        }
        
        .glow-effect {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: radial-gradient(circle at 20% 30%, rgba(0, 212, 255, 0.1) 0%, transparent 50%);
            pointer-events: none;
            z-index: -1;
        }
        
        .particles {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: -1;
        }
        
        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background-color: rgba(0, 212, 255, 0.7);
            border-radius: 50%;
            animation: float 10s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0) translateX(0); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100vh) translateX(100px); opacity: 0; }
        }
        
        #homeBtn {
            display: none;
        }
        
        #page17 #homeBtn {
            display: block;
        }
    </style>
</head>
<body>
    <div class="book">
        <!-- 1-бет -->
        <div class="page active" id="page1">
            <img src="АБ1.png" class="background-image">
            <div class="page-content">
                <img src="dd.png" alt="Абай Құнанбаев" class="slide-image">
                <h1 class="slide-title">Абайдың «Толық адам» ілімі</h1>
                <div class="slide-content">
                    <p style="font-size: 20px;">Ұлттық білім беру негізі</p>
                </div>
                <div class="page-number">1</div>
            </div>
        </div>
        
        <!-- 2-бет -->
        <div class="page" id="page2">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">«Толық адам» ілімін тану </h1>
                <div class="slide-content">
                    <p>Біреуінің күні жоқ біреуінсіз,<br>
                    Ғылым сол үшеуінің <span class="highlight">жөнін</span> білмек.</p>
                    
                    <p>FAЛAM-AДAM тандемі: Ceзiну<br>
                    Maxa66атпен әрекет ету</p>
                    
                    <div class="two-columns">
                        <div class="column">
                            <p><span class="highlight">ЖҮРЕК</span><br>
                            AқИҚАТ: тану<br>
                            Көкірек көзін ашу</p>
                        </div>
                        <div class="column">
                            <p><span class="highlight">АҚЫЛ</span><br>
                            ҚАЙPAT<br>
                            KУАТТЫ жұмсау<br>
                            «Ұттым-Ұттымға» сүйену</p>
                        </div>
                    </div>
                </div>
                <div class="page-number">2</div>
            </div>
        </div>
        
        <!-- 3-бет -->
        <div class="page" id="page3">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">«Толық адам» ІЛІМІНІҢ кілті</h1>
                <div class="slide-content">
                    <p><span class="highlight">ғажайып</span> ақылды және ғажайыппен жасаған денеге кіргізіп, мұнша салихат иесі қылғаны хикметпенен сұлтан қылғандығы емес пе?</p>
                    
                    <p style="font-size: 24px;"><span class="highlight">(27-сөз)</span></p>
                    
                    <p>Біреуі ойын біреуіне ұқтырарлық тіліне сез беріп жаратпағы махаббат емес пе?</p>
                    
                    <p>Махаббаттың төлеуі - махаббат. Талап, ұғым махаббаттан шығады (38-сөз).</p>
                </div>
                <div class="page-number">3</div>
            </div>
        </div>
        
        <!-- 4-бет -->
        <div class="page" id="page4">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Адамдық деңгейлері</h1>
                <div class="slide-content">
                    <p><span class="highlight">НАДАН:</span><br>
                    Өзінде ой жоқ,<br>
                    Басында ми жоқ,<br>
                    Күлкішіп кердең наданның.<br>
                    Көп айтса көнді,<br>
                    Жұрт айтса болды -<br>
                    Әдеті надан адамның.</p>
                    
                    <p><span class="highlight">АДАМ:</span><br>
                    Қашан бір бала ғылым, білімді көксерлік болса, сонда ғана оның аты АДАМ болады</p>
                    
                    <p><span class="highlight">ТОЛЫҚ АДАМ:</span><br>
                    Құдай Тағала жолында жүруді өзіне кім шарт қылып қадам басса, сол ТОЛЫҚ АДАМ болады (38)</p>
                </div>
                <div class="page-number">4</div>
            </div>
        </div>
        
        <!-- 5-бет -->
        <div class="page" id="page5">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">АДАМДЫҚ ТАЛАБЫ</h1>
                <div class="slide-content">
                    <p>*Ғылым таппай мақтанба,<br>
                    *Орын таппай баптанба,<br>
                    *Құмарланып шаттанба,<br>
                    *Ойнап босқа күлуге...</p>
                    
                    <p>«Біз ғылымды жасап шығара алмаймыз, жаралып, жасалып қойған нөрселерді сезбекпіз, көзбен көріп, ақылмен біліп...»</p>
                </div>
                <div class="page-number">5</div>
            </div>
        </div>
        
        <!-- 6-бет -->
        <div class="page" id="page6">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Адам болудың баспалдағы</h1>
                <div class="slide-content">
                    <p>Адамзатқа не керек:</p>
                    <p>* Сүймек,<br>
                    * Сезбек,<br>
                    * Кейімек,<br>
                    * Харекет қылмақ,<br>
                    * Жүгірмек,<br>
                    * Ақылмен ойлап сөйлемек.</p>
                </div>
                <div class="page-number">6</div>
            </div>
        </div>
        
        <!-- 7-бет -->
        <div class="page" id="page7">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">«Толық адам» іліміне бастайтын сүрлеу</h1>
                <div class="slide-content">
                    <p><span class="highlight">Уайым</span><br>
                    қайғысыздығыңа  уайым-қайғы  қылдағы, сол уайым-қайғысыздықтан  құтыларлық орынды харекет  табу керек hәм қылу керек (4)</p>
                </div>
                <div class="page-number">7</div>
            </div>
        </div>
        
        <!-- 8-бет -->
        <div class="page" id="page8">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Адам болам десеңіз... (шарты)</h1>
                <div class="slide-content">
                    <p style="font-size: 22px; line-height: 2.5;">
                        <span class="highlight">РАҚЫМ</span><br>
                        <span class="highlight">ҚАНАҒАТ</span><br>
                        <span class="highlight">ТЕРЕҢ ОЙ</span><br>
                        <span class="highlight">ЕҢБЕК</span><br>
                        <span class="highlight">ТАЛАП</span>
                    </p>
                </div>
                <div class="page-number">8</div>
            </div>
        </div>
        
        <!-- 9-бет -->
        <div class="page" id="page9">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Пендеге тән куаныш пен жұбаныш</h1>
                <div class="slide-content">
                    <p>«... Оның қасында біз сәулелі кісінің бірі емеспіз бе? Оған қарағанда мен таза кісі емеспін бе?»</p>
                    
                    <p>«Жалғыз біз бе, елдің бөрі де сүйтіп-ақ жүр ғой, көппен керген үлы той, көппен бірге болсақ болады да...» (23-сөз)</p>
                </div>
                <div class="page-number">9</div>
            </div>
        </div>
        
        <!-- 10-бет -->
        <div class="page" id="page10">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">ЖАЛҚАУЛЫҚ - АДАМ ДҰШПАНЫ</h1>
                <div class="slide-content">
                    <p><span class="highlight">Әрбір жалқау кісі қорқақ, қайратсыз тартады;</span><br>
                    <span class="highlight">әрбір қайратсыз қорқақ, мақтаншақ келеді;</span><br>
                    <span class="highlight">әрбір мақтаншақ қорқақ, ақылсыз, надан келеді;</span><br>
                    <span class="highlight">әрбір ақылсыз надан, арсыз келеді;</span><br>
                    <span class="highlight">әрбір арсыз жалқаудан сұрамсақ, өзі тойымсыз, өнерсіз, ешкімге достығы жоқ жандар шығады (3- сөз).</span></p>
                    
                    <p><span class="highlight">Қулық саумақ, көз сүзіп, тіленіп, адам саумақ - өнерсіз иттің ісі (4-сөз)</span><br>
                    - Тоқ тіленші - адамның сайтаны</p>
                </div>
                <div class="page-number">10</div>
            </div>
        </div>
        
        <!-- 11-бет -->
        <div class="page" id="page11">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">ЖҮРЕК- ИМАН ҰЯСЫ</h1>
                <div class="slide-content">
                    <p>Tipi адамның жүректен аяулы жері бола ма? Тіл жүректің айтқанына көнсе, жалған шықпайды. Амалдың тілін алса, жүрек ұмыт қалады.</p>
                    
                    <p>Махаббатсыз дүние бос, Хайуанға оны қосындар</p>
                </div>
                <div class="page-number">11</div>
            </div>
        </div>
        
        <!-- 12-бет -->
        <div class="page" id="page12">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">ЫСТЫҚ ҚАЙРАТ - ҚУАТ КӨЗІ</h1>
                <div class="slide-content">
                    <p>Алла тағала саған еңбек қылып мал табарлық куат берді... Сол куатты жұмсарлық ғылым берді... Ол ғылымды ұғарлық ақыл берді... Ерінбей еңбек қыл...</p>
                    
                    <p>... көштің соңынан итше ере бермей, адасқан көптен атының басын бұрып алуға жараған, әділетті ақыл мойындаған нөрсете, қиын да болса, мойындау, әділетті ақыл мойындамаған нөрсете, юңай да болса, мойындамау - ерлік (14)</p>
                </div>
                <div class="page-number">12</div>
            </div>
        </div>
        
        <!-- 13-бет -->
        <div class="page" id="page13">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Толық Адам: Қабілеттің Қасиетке ұласуы</h1>
                <div class="slide-content">
                    <table class="table">
                        <tr>
                            <th></th>
                            <th>Қабілет</th>
                            <th>Қабілет</th>
                        </tr>
                        <tr>
                            <td><strong>Сөйлеу</strong></td>
                            <td>↓</td>
                            <td><strong>Ойлау</strong></td>
                        </tr>
                        <tr>
                            <td><strong>Қасиет:</strong></td>
                            <td></td>
                            <td><strong>Қасиет:</strong></td>
                        </tr>
                        <tr>
                            <td><strong>Шешендік</strong></td>
                            <td>↓</td>
                            <td><strong>Даналық</strong></td>
                        </tr>
                        <tr>
                            <td colspan="3" style="padding: 20px;">
                                <p>Адамның қабілеті мен қасиетінің үйлесімі - толық адам болудың негізі</p>
                            </td>
                        </tr>
                    </table>
                </div>
                <div class="page-number">13</div>
            </div>
        </div>
        
        <!-- 14-бет -->
        <div class="page" id="page14">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">Толық АДАМ табиғаты</h1>
                <div class="slide-content">
                    <p>3 тану: Алла ғағаланы танымақтық, өзін танымақтық, дүниені танымақтық (38)</p>
                    
                    <p>Мал, мақтан, ғиззат-құрмет адамды өзі іздеп тапса, адамдықты бұзбайды hәм көрік болады. Егерде адам өзі оларға табынып іздесе, тапса да, таппаса да адамдығы жоғалады (38)</p>
                    
                    <p>Биік мансап - биік жартас, ерінбей еңбектеп жылан да шығады, екпіндеп ұшып қыран да шығады (37)</p>
                </div>
                <div class="page-number">14</div>
            </div>
        </div>
        
        <!-- 15-бет -->
        <div class="page" id="page15">
            <img src="https://images.unsplash.com/photo-1531685250784-7569952593d2?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">ТОЛЫҚ АДАМ болмысы:</h1>
                <div class="slide-content">
                    <p>Ақиқатты тану (рациональны меже);<br>
                    ақиқаттың сырын сезіну (эмоциональны күй);<br>
                    жасампаздық (адами әлеует);<br>
                    көркем мінез (кісілік қалып) <span class="highlight">ҮЙЛЕСІМІ.</span></p>
                </div>
                <div class="page-number">15</div>
            </div>
        </div>
        
        <!-- 16-бет -->
        <div class="page" id="page16">
            <img src="АБ1.png" class="background-image">
            <div class="page-content">
                <h1 class="slide-title">ТОЛЬІҚ АДАМ бітімі</h1>
                <div class="slide-content">
                    <p><span class="highlight">Тән куаты:</span><br>
                    жибили (ішу, жеу, ұйықтау + 5 сезім мүшесі арқылы білуге ұмтылу);</p>
                    
                    <p><span class="highlight">Жан қуаты:</span><br>
                    кәсиби (жибилиден басталып, кейін сақтау арқылы зораятын дағдылар) + 3 артық қуат (түрткі, «тыншытпайтын» күш, жүректің сезімталдығы)</p>
                    
                    <div class="two-columns">
                        <div class="column">
                            <p><span class="highlight">Тән куатының нәтижесі:</span><br>
                            Дәулет, Еркіндік, Тәуелсіздік</p>
                            
                            <p><span class="highlight">Тән куатының сипаты:</span><br>
                            Сырттан тауып, сыртта сақталады</p>
                        </div>
                        <div class="column">
                            <p><span class="highlight">Жан куатының нәтижесі:</span><br>
                            Ақыл, Ғылым, Махаббат</p>
                            
                            <p><span class="highlight">Жан куатының сипаты:</span><br>
                            ІШКІ Рухани әлемді жетілдіреді</p>
                        </div>
                    </div>
                </div>
                <div class="page-number">16</div>
            </div>
        </div>
        
        <!-- 17-бет -->
        <div class="page" id="page17">
            <img src="124.png" class="background-image">
            <div class="page-content">
                <img src="124.png" alt="Абай Құнанбаев" class="slide-image">
                <h1 class="slide-title">Назарларыңызға рахмет</h1>
                <div class="slide-content" style="text-align: center;">
                    <p>Абай Құнанбаевтың "Толық Адам" ілімі бойынша презентация</p>
                </div>
                <div class="page-number">17</div>
            </div>
        </div>
    </div>
    
    <div class="navigation">
        <button class="nav-btn" id="prevBtn">← </button>
        <button class="nav-btn" id="nextBtn"> →</button>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const pages = document.querySelectorAll('.page');
            const prevBtn = document.getElementById('prevBtn');
            const nextBtn = document.getElementById('nextBtn');
            let currentPage = 0;
            
            // Бастапқы бетті көрсету
            showPage(currentPage);
            
            // Келесі бетке өту
            nextBtn.addEventListener('click', function() {
                if (currentPage < pages.length - 1) {
                    currentPage++;
                    showPage(currentPage);
                }
            });
            
            // Алдыңғы бетке өту
            prevBtn.addEventListener('click', function() {
                if (currentPage > 0) {
                    currentPage--;
                    showPage(currentPage);
                }
            });
            
            // Пернелер арқылы басқару
            document.addEventListener('keydown', function(e) {
                if (e.key === 'ArrowRight' || e.key === ' ') {
                    if (currentPage < pages.length - 1) {
                        currentPage++;
                        showPage(currentPage);
                    }
                } else if (e.key === 'ArrowLeft') {
                    if (currentPage > 0) {
                        currentPage--;
                        showPage(currentPage);
                    }
                }
            });
            
            // Бетті көрсету функциясы
            function showPage(index) {
                pages.forEach((page, i) => {
                    page.classList.remove('active', 'prev', 'next');
                    
                    if (i === index) {
                        page.classList.add('active');
                    } else if (i < index) {
                        page.classList.add('prev');
                    } else if (i > index) {
                        page.classList.add('next');
                    }
                });
                
                // Түймешіктерді жасыру/көрсету
                prevBtn.style.display = index === 0 ? 'none' : 'block';
                nextBtn.style.display = index === pages.length - 1 ? 'none' : 'block';
            }
        });
    </script>
</body>
</html>
