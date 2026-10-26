<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>台中冬日自駕盲盒行程</title>
    <style>
        body { font-family: -apple-system, sans-serif; background: #fafafd; color: #2d3436; padding: 15px; max-width: 600px; margin: 0 auto; }
        h1, p.subtitle { text-align: center; }
        h1 { font-size: 22px; color: #2d3436; font-weight: 800; margin-bottom: 5px; }
        p.subtitle { color: #a0aec0; font-size: 13px; margin-bottom: 25px; }
        .card { background: #fff; border-radius: 12px; padding: 18px; margin-bottom: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.02), 0 1px 3px rgba(0,0,0,0.02); border: 1px solid #edf2f7; }
        .card-title { font-size: 14.5px; font-weight: bold; margin-bottom: 12px; color: #1a202c; border-left: 4px solid #4a5568; padding-left: 10px; }
        .fixed-text { font-size: 13px; color: #4a5568; line-height: 1.6; background: #f7fafc; padding: 12px; border-radius: 8px; margin-bottom: 12px; border: 1px dashed #e2e8f0; }
        .img-preview { width: 100%; height: 160px; object-fit: cover; border-radius: 8px; margin-bottom: 8px; background: #e2e8f0; }
        .option-label { display: block; background: #fff; border: 1px solid #e2e8f0; border-radius: 8px; padding: 12px; margin-bottom: 10px; cursor: pointer; transition: all 0.2s ease; }
        .option-label:hover { border-color: #cbd5e0; background: #f7fafc; }
        .option-input { margin-right: 10px; transform: scale(1.1); }
        .option-name { font-weight: 700; font-size: 14px; color: #2d3436; }
        .option-desc { font-size: 12.5px; color: #718096; display: block; margin-left: 24px; margin-top: 4px; line-height: 1.4; }
        .other-input { width: 85%; margin-left: 24px; margin-top: 8px; padding: 8px; border: 1px solid #e2e8f0; border-radius: 6px; font-size: 13px; display: none; background: #f7fafc; }
        .alc-switch { background: #fff; border: 1px solid #e2e8f0; padding: 12px; border-radius: 8px; margin: 12px 0; }
        .sub-question { margin-left: 15px; border-left: 2px dashed #cbd5e0; padding-left: 12px; margin-top: 12px; display: none; }
        button.submit-btn { display: block; width: 100%; background: #2d3436; color: #fff; border: none; padding: 15px; font-size: 16px; font-weight: bold; border-radius: 8px; cursor: pointer; margin-top: 25px; transition: background 0.2s; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        button.submit-btn:hover { background: #1e252b; }
        #result-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); justify-content: center; align-items: center; padding: 15px; z-index: 999; box-sizing: border-box; }
        .vip-pass { background: linear-gradient(135deg, #1a202c 0%, #2d3748 100%); color: #fff; padding: 25px; border-radius: 16px; max-width: 500px; width: 100%; max-height: 85vh; overflow-y: auto; box-shadow: 0 20px 25px rgba(0,0,0,0.25); border: 2px solid #d69e2e; position: relative; }
        .vip-title { font-size: 18px; font-weight: 800; text-align: center; color: #ecc94b; letter-spacing: 2px; margin-bottom: 5px; }
        .vip-subtitle { font-size: 12px; text-align: center; color: #cbd5e0; margin-bottom: 20px; text-transform: uppercase; border-bottom: 1px solid #4a5568; padding-bottom: 10px; }
        .vip-field { margin-bottom: 15px; background: rgba(255,255,255,0.05); padding: 12px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.1); }
        .vip-label { font-size: 11px; color: #a0aec0; text-transform: uppercase; font-weight: bold; margin-bottom: 4px; display: block; }
        .vip-value { font-size: 14px; color: #fff; font-weight: 600; }
        .vip-stamp { font-size: 12px; color: #e53e3e; font-weight: 800; border: 2px solid #e53e3e; padding: 4px 8px; display: inline-block; border-radius: 4px; transform: rotate(-5deg); position: absolute; top: 20px; right: 20px; text-transform: uppercase; }
        .vip-tip { font-size: 12.5px; color: #fc8181; text-align: center; margin-top: 20px; font-weight: bold; line-height: 1.5; background: rgba(229,62,62,0.1); padding: 10px; border-radius: 6px; }
        textarea { width: 100%; height: 100px; font-size: 12px; padding: 8px; box-sizing: border-box; border: 1px solid #4a5568; border-radius: 6px; resize: none; background: rgba(0,0,0,0.2); color: #a0aec0; margin-top: 15px; line-height: 1.4; }
        .modal-btn { display: block; width: 100%; text-align: center; background: #ecc94b; color: #1a202c; padding: 10px; border-radius: 6px; border: none; cursor: pointer; font-weight: bold; margin-top: 15px; font-size: 14px; }
    </style>
</head>
<body>

    <h1>台中冬日自駕四天三夜行程規劃</h1>
    <p class="subtitle">親愛的，請選出妳想體驗的住宿與美食選項</p>

    <form id="itinerary-form">

        <!-- 住宿定錨 -->
        <div class="card">
            <div class="card-title">🏨 住宿盲盒（三選一，連住三晚不挪窩，自帶專屬獨立車庫）</div>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="住宿">
                <input type="radio" name="hotel" value="鳥人創意旅店（西屯區）" class="option-input" required>
                <span class="option-name">鳥人創意旅店（西屯區）</span>
                <span class="option-desc">主打地窖、沙漠、原始森林風格，設計感強烈神祕，拍照視覺衝擊力高。</span>
            </label>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="住宿">
                <input type="radio" name="hotel" value="台中芭蕾城堡酒店（南屯區）" class="option-input" required>
                <span class="option-name">台中芭蕾城堡酒店（南屯區）</span>
                <span class="option-desc">主打一房一庭園的歐洲城堡渡假感，房型寬敞自帶雙人大型氣泡按摩浴缸。</span>
            </label>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="住宿">
                <input type="radio" name="hotel" value="沐蘭精品旅館（西屯區）" class="option-input" required>
                <span class="option-name">沐蘭精品旅館（西屯區）</span>
                <span class="option-desc">森林系頂級 Villa 風格，房間內融入落羽松、大型水景與大片植栽，奢華且極度療癒。</span>
            </label>
        </div>
        <!-- 第一天 -->
        <div class="card">
            <div class="card-title">📅 第一天 行程安排</div>
            <div class="fixed-text">
                【下午】機場接機（準備手搖飲微糖少冰）<br>
                【下午茶】宮原眼科第四信用合作社（雙球冰淇淋，兩人分食）<br>
                【傍晚】旅店辦理入住、放置行李、梳洗更衣
            </div>
            <div style="font-size: 13px; font-weight: bold; margin-bottom: 8px;">請選擇晚餐大餐：</div>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="火鍋">
                <input type="radio" name="d1_dinner" value="這一鍋 皇室秘藏鍋物（七期朝富店）" class="option-input" required onclick="toggleOther('d1_dinner', false)">
                <span class="option-name">這一鍋 皇室秘藏鍋物（七期朝富店）</span>
                <span class="option-desc">浮誇東方宮廷風火鍋。可以用墨魚汁在豆腐紙上寫字下鍋煮，神仙牛肉上桌自帶乾冰瀑布。</span>
            </label>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="台菜">
                <input type="radio" name="d1_dinner" value="永心鳳茶（勤美誠品店）" class="option-input" required onclick="toggleOther('d1_dinner', false)">
                <span class="option-name">永心鳳茶（勤美誠品店）</span>
                <span class="option-desc">時髦老洋房復古茶沙龍。用紅酒杯喝台灣頂級冷泡茶，吃精緻時髦的現代台菜套餐。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d1_dinner" value="other" class="option-input" required onclick="toggleOther('d1_dinner', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d1_dinner_other" class="other-input" placeholder="請輸入想吃的餐廳或小吃">
            </label>

            <div class="alc-switch">
                <div style="font-size: 13px; font-weight: bold; margin-bottom: 8px; color: #007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
                <label><input type="radio" name="d1_alcohol" value="yes" required onclick="toggleSub('d1_alc_section', true)"> 是</label>
                <label style="margin-left: 20px;"><input type="radio" name="d1_alcohol" value="no" required onclick="toggleSub('d1_alc_section', false)"> 否，今天想早點休息</label>
            </div>

            <div id="d1_alc_section" class="sub-question">
                <div class="fixed-text">【晚上】前往七期秋紅谷都市夜景散步，隨後開車前往特色酒吧小酌。</div>
            </div>
            <div class="fixed-text" style="margin-top: 8px;">
                【宵夜】旅店房內 Uber Eats 外送（地瓜球與期間限定草莓芝芝）<br>
                【深夜】開箱超商統一布丁限定款（翻轉布丁「丁布」或無焦糖版「統一布布」）
            </div>
        </div>

        <!-- 第二天 -->
        <div class="card">
            <div class="card-title">📅 第二天 行程安排</div>
            <div style="font-size: 13px; font-weight: bold; margin-bottom: 6px;">【早餐】請選擇早餐（兩人分食一份）：</div>
            <label class="option-label">
                <input type="radio" name="d2_breakfast" value="肉蛋吐司（健行總店）" class="option-input" required onclick="toggleOther('d2_breakfast', false)">
                <span class="option-name">肉蛋吐司（健行總店）</span>
                <span class="option-desc">台灣神級排隊老店。炭烤香氣的吐司夾上爆汁軟嫩豬排，配冰豆漿。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d2_breakfast" value="明賢行" class="option-input" required onclick="toggleOther('d2_breakfast', false)">
                <span class="option-name">明賢行</span>
                <span class="option-desc">老宅改建的文青風台式早午餐。吃得到精緻乾淨的控肉飯、炒麵與古早味手作點心。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d2_breakfast" value="other" class="option-input" required onclick="toggleOther('d2_breakfast', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d2_breakfast_other" class="other-input" placeholder="請輸入想吃的早餐">
            </label>

            <div class="fixed-text">
                【中午至下午】西區全日慢活散步（車停草悟道大停車場，全程步行參觀審計新村文創市集、勤美誠品綠園道聖誕村、PARK2草悟廣場）
            </div>

            <div style="font-size: 13px; font-weight: bold; margin: 12px 0 6px 0;">【下午茶】馬卡龍盲盒（二選一，外帶車上吃）：</div>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="法式馬卡龍">
                <input type="radio" name="d2_macaron" value="CJSJ 法式甜點店" class="option-input" required onclick="toggleOther('d2_macaron', false)">
                <span class="option-name">CJSJ 法式甜點店（西區）</span>
                <span class="option-desc">米其林三星主廚創意法式甜點。馬卡龍做工精緻如藝術品，特別經過減糖調整。</span>
            </label>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="貝殼肥卡龍">
                <input type="radio" name="d2_macaron" value="繽色絲 貝殼馬卡龍" class="option-input" required onclick="toggleOther('d2_macaron', false)">
                <span class="option-name">繽色絲 Princess 貝殼馬卡龍（西屯區）</span>
                <span class="option-desc">造型吸睛的肥卡龍與貝殼馬卡龍。外殼繽紛，內餡厚實飽滿且口味創新，拍照發 IG 極好看。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d2_macaron" value="other" class="option-input" required onclick="toggleOther('d2_macaron', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d2_macaron_other" class="other-input" placeholder="請輸入想吃的甜點">
            </label>

            <div style="font-size: 13px; font-weight: bold; margin: 12px 0 6px 0;">【晚餐】燒肉晚餐盲盒（二選一，單點精緻肉品不撐胃）：</div>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="燒肉">
                <input type="radio" name="d2_dinner" value="茶六燒肉堂（公益店）" class="option-input" required onclick="toggleOther('d2_dinner', false)">
                <span class="option-name">茶六燒肉堂（公益店）</span>
                <span class="option-desc">台中燒肉天花板之一。裝潢大氣非凡，肉質精緻。入座先送無限續喝的味噌魚湯，最後的黑糖凍與草莓雪花冰好評度極高。</span>
            </label>
            <label class="option-label">
                <img src="https://unsplash.com" class="img-preview" alt="燒肉屋馬">
                <input type="radio" name="d2_dinner" value="屋馬燒肉（園邸店）" class="option-input" required onclick="toggleOther('d2_dinner', false)">
                <span class="option-name">屋馬燒肉（園邸店）</span>
                <span class="option-desc">台中傳奇燒肉始祖。主打極致貼心的桌邊服務、招牌無限續喝的黃金雞湯，最後可加購浮誇的海鮮粥。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d2_dinner" value="other" class="option-input" required onclick="toggleOther('d2_dinner', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d2_dinner_other" class="other-input" placeholder="請輸入想吃的餐廳">
            </label>

            <div class="alc-switch">
                <div style="font-size: 13px; font-weight: bold; margin-bottom: 8px; color: #007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
                <label><input type="radio" name="d2_alcohol" value="yes" required onclick="toggleSub('d2_alc_section', true)"> 是</label>
                <label style="margin-left: 20px;"><input type="radio" name="d2_alcohol" value="no" required onclick="toggleSub('d2_alc_section', false)"> 否，想直接回房間泡澡</label>
            </div>

            <div id="d2_alc_section" class="sub-question">
                <div style="font-size: 13px; font-weight: bold; margin-bottom: 5px;">請選擇今晚想去的特色酒吧：</div>
                <label class="option-label">
                    <img src="https://unsplash.com" class="img-preview" alt="酒吧">
                    <input type="radio" name="d2_bar" value="Isman Bar 三十參酒館" class="option-input">
                    <span class="option-name">Isman Bar 三十參酒館</span>
                    <span class="option-desc">英倫特務風 Speakeasy 密室酒吧。門口偽裝成高檔西裝店，需要輸入神祕密碼鎖才能開門進入，私密感極高。</span>
                </label>
                <label class="option-label">
                    <img src="https://unsplash.com" class="img-preview" alt="酒吧">
                    <input type="radio" name="d2_bar" value="Vender Bar" class="option-input">
                    <span class="option-name">Vender Bar</span>
                    <span class="option-desc">曾榮獲亞洲50大最佳酒吧。門口偽裝成一台自動販賣機，調酒以販賣機與生活為概念，視覺與風味皆為國際世界級。</span>
                </label>
            </div>
        </div>
        <!-- 第三天 -->
        <div class="card">
            <div class="card-title">📅 第三天 行程安排</div>
            <div style="font-size: 13px; font-weight: bold; margin-bottom: 6px;">【早午餐】早午餐盲盒（二選一，兩人分食一份）：</div>
            <label class="option-label">
                <input type="radio" name="d3_breakfast" value="模範貝果" class="option-input" required onclick="toggleOther('d3_breakfast', false)">
                <span class="option-name">模範貝果</span>
                <span class="option-desc">隱身老巷弄的手工貝果名店。多種特色台灣在地內餡（如剝皮辣椒、芋泥），口感紮實，配手沖咖啡非常舒服。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d3_breakfast" value="一人一伴 ともだち" class="option-input" required onclick="toggleOther('d3_breakfast', false)">
                <span class="option-name">一人一伴 ともだち</span>
                <span class="option-desc">日式老宅三明治專賣店。招牌是極厚切的炸豬排三明治與千層蛋捲，木質調空間非常療癒。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d3_breakfast" value="other" class="option-input" required onclick="toggleOther('d3_breakfast', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d3_breakfast_other" class="other-input" placeholder="請輸入想吃的早午餐">
            </label>

            <div class="fixed-text">
                【中午】台中國家歌劇院（無直角曲牆建築參觀、頂樓空中花園）<br>
                【午餐】鼎王麻辣鍋公益店（麻辣與酸菜白肉鴛鴦雙拼，主攻老油條與鴨血豆腐）<br>
                【下午】高美濕地落日（前往海邊木棧道，觀賞風車與冬日晚霞，備有保暖外套與暖暖包）
            </div>

            <div class="alc-switch">
                <div style="font-size: 13px; font-weight: bold; margin-bottom: 8px; color: #007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
                <label><input type="radio" name="d3_alcohol" value="yes" required onclick="toggleSub('d3_alc_section', true)"> 是</label>
                <label style="margin-left: 20px;"><input type="radio" name="d3_alcohol" value="no" required onclick="toggleSub('d3_alc_section', false)"> 否，今天吹完海風想喝熱湯休息</label>
            </div>

            <div id="d3_alc_section" class="sub-question">
                <div style="font-size: 13px; font-weight: bold; margin-bottom: 5px;">請選擇今晚旅店外送晚餐（搭配18天生啤酒）：</div>
                <label class="option-label">
                    <img src="https://unsplash.com" class="img-preview" alt="熱炒">
                    <input type="radio" name="d3_dinner" value="生猛海產熱炒店外送" class="option-input">
                    <span class="option-name">生猛海產熱炒店外送</span>
                    <span class="option-desc">外送九層塔炒蛤蜊、金沙苦瓜、鳳梨蝦球。配上超限定、保存期限只有18天的綠色玻璃瓶台灣生啤酒。</span>
                </label>
                <label class="option-label">
                    <img src="https://unsplash.com" class="img-preview" alt="傳統小吃">
                    <input type="radio" name="d3_dinner" value="傳統小吃外送大集合" class="option-input">
                    <span class="option-name">指標性傳統小吃外送大集合（蚵仔煎與滷肉飯）</span>
                    <span class="option-desc">外送邊緣酥脆、醬汁靈魂的蚵仔煎，搭配滷到軟爛入味、充滿膠質的大塊爌肉滷肉飯。</span>
                </label>
                <label class="option-label">
                    <input type="radio" name="d3_dinner" value="other" class="option-input" onclick="toggleOther('d3_dinner', true)">
                    <span class="option-name">其他（自填外送備案）</span>
                    <input type="text" id="d3_dinner_other" class="other-input" placeholder="請輸入想叫外送的食物">
                </label>
            </div>
            <div class="fixed-text" style="margin-top: 10px;">
                【深夜】深夜解饞：外送或得來速享用台灣限定麥當勞神級玉米湯，配旅店雙人按摩大浴缸
            </div>
        </div>

        <!-- 第四天 -->
        <div class="card">
            <div class="card-title">📅 第四天 行程安排</div>
            <div style="font-size: 13px; font-weight: bold; margin-bottom: 6px;">【早午餐】在地老靈魂早午餐（二選一，兩人分食）：</div>
            <label class="option-label">
                <input type="radio" name="d4_breakfast" value="王家菜頭粿糯米腸" class="option-input" required onclick="toggleOther('d4_breakfast', false)">
                <span class="option-name">王家菜頭粿糯米腸</span>
                <span class="option-desc">傳統第二市場傳奇。必點菜頭粿、糯米腸、荷包蛋三合一，淋上甜辣醬油膏，配隔壁的老賴紅茶。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d4_breakfast" value="山河魯肉飯" class="option-input" required onclick="toggleOther('d4_breakfast', false)">
                <span class="option-name">山河魯肉飯</span>
                <span class="option-desc">想大口吃肉的選擇。台灣道地的滷肉飯（大塊爌肉），肉質軟爛入味，配上一碗蜆仔湯，最接地氣。</span>
            </label>
            <label class="option-label">
                <input type="radio" name="d4_breakfast" value="other" class="option-input" required onclick="toggleOther('d4_breakfast', true)">
                <span class="option-name">其他（自填備案）</span>
                <input type="text" id="d4_breakfast_other" class="other-input" placeholder="請輸入想吃的早午餐">
            </label>
            <div class="fixed-text" style="margin-top: 8px;">
                【中午】伴手禮衝刺（前往如邑堂太陽餅或俊美鳳梨酥採買，免提行李直接放車後廂）<br>
                【下午】抵達機場辦理登機回香港
            </div>
        </div>

        <button type="submit" class="submit-btn">完成選擇，生成行程結果</button>
    </form>

    <!-- 方案B 高質感通行證 Modal -->
    <div id="result-modal">
        <div class="vip-pass">
            <div class="vip-stamp">APPROVED</div>
            <div class="vip-title">12月冬日台中．微醺通行證</div>
            <div class="vip-subtitle">VVIP PASS // DETAILED ITINERARY</div>
            
            <div class="vip-field">
                <span class="vip-label">🏨 奢華宿營旅店</span>
                <span id="v-hotel" class="vip-value">-</span>
            </div>
            <div class="vip-field">
                <span class="vip-label">🍽️ Day 1 啟航晚餐</span>
                <span id="v-d1-d" class="vip-value">-</span>
            </div>
            <div class="vip-field">
                <span class="vip-label">🥩 Day 2 燒肉盛宴</span>
                <span id="v-d2-d" class="vip-value">-</span>
            </div>
            <div class="vip-field">
                <span class="vip-label">🍹 Day 2 夜幕微醺</span>
                <span id="v-d2-b" class="vip-value">-</span>
            </div>
            <div class="vip-field">
                <span class="vip-label">🌅 Day 3 海線晚餐</span>
                <span id="v-d3-d" class="vip-value">-</span>
            </div>

            <div class="vip-tip">
                親愛的，恭喜妳成功解鎖盲盒！請立刻截圖發給 Isaac 解鎖行程，啟動妳的專屬台中冬日自駕之旅。
            </div>

            <textarea id="result-text" readonly onclick="this.select()"></textarea>
            <button class="modal-btn" onclick="closeModal()">返回修改選項</button>
        </div>
    </div>

    <script src="https://jsdelivr.net"></script>
    <script>
        emailjs.init("VlUqNiaw_M1XN169M");
        function toggleOther(name, show) {
            const input = document.getElementById(name + '_other');
            if(input) input.style.display = show ? 'block' : 'none';
        }
        function toggleSub(id, show) {
            const section = document.getElementById(id);
            section.style.display = show ? 'block' : 'none';
            const inputs = section.querySelectorAll('input');
            inputs.forEach(i => i.required = show);
        }
        function closeModal() { document.getElementById('result-modal').style.display = 'none'; }
        
        document.getElementById('itinerary-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const formData = new FormData(this);
            
            let getVal = (name) => {
                let val = formData.get(name);
                if(val === 'other') { return "【自填】" + (document.getElementById(name + '_other').value || "未填寫"); }
                return val || "未安排";
            };

            // 渲染方案B 圖卡資料
            document.getElementById('v-hotel').innerText = formData.get('hotel');
            document.getElementById('v-d1-d').innerText = getVal('d1_dinner');
            document.getElementById('v-d2-d').innerText = getVal('d2_dinner');
            document.getElementById('v-d2-b').innerText = formData.get('d2_alcohol') === 'yes' ? formData.get('d2_bar') : "回房享受雙人按摩大浴缸";
            document.getElementById('v-d3-d').innerText = formData.get('d3_alcohol') === 'yes' ? getVal('d3_dinner') : "回房享用神級玉米湯放鬆";

            let res = "台中四天三夜自駕行程選擇結果：\n\n";
            res += "🏨 連住三晚旅店：\n" + formData.get('hotel') + "\n\n";
            res += "📅 第一天行程：\n- 【下午】機場接機 ➔ 宮原眼科第四信用合作社\n- 【傍晚】旅店入住梳洗\n- 【晚餐】" + getVal('d1_dinner') + "\n";
            if(formData.get('d1_alcohol') === 'yes') { res += "- 【晚上】秋紅谷夜景散步 ➔ 特色酒吧小酌\n"; }
            res += "- 【宵夜】房內外送（地瓜球、草莓芝芝）\n- 【深夜】超商開箱統一布丁限定款\n\n";
            res += "📅 第二天行程：\n- 【早餐】" + getVal('d2_breakfast') + "\n- 【中午至下午】西區全日慢活散步（審計新村、勤美誠品、草悟廣場）\n- 【下午茶】馬卡龍：" + getVal('d2_macaron') + "\n- 【晚餐】燒肉：" + getVal('d2_dinner') + "\n";
            if(formData.get('d2_alcohol') === 'yes') { res += "- 【晚上酒吧】" + formData.get('d2_bar') + "\n"; }
            res += "\n";
            res += "📅 第三天行程：\n- 【早午餐】" + getVal('d3_breakfast') + "\n- 【中午】台中國家歌劇院\n- 【午餐】鼎王麻辣鍋公益店\n- 【下午】高美濕地看落日夕陽\n";
            if(formData.get('d3_alcohol') === 'yes') { res += "- 【晚餐】旅店外送熱炒/小吃（配18天生啤酒）：" + getVal('d3_dinner') + "\n"; }
            res += "- 【深夜】台灣限定麥當勞玉米湯配按摩大浴缸\n\n";
            res += "📅 第四天行程：\n- 【早午餐】" + getVal('d4_breakfast') + "\n- 【中午】伴手禮採買（如邑堂或俊美）\n- 【下午】抵達機場登機\n\n我選好了！";
            
            document.getElementById('result-text').value = res;
            document.getElementById('result-modal').style.display = 'flex';
            
            // 實時 Mail 發送至你的 Hotmail
            emailjs.send("service_w1v9g3g","template_m2h0x4r",{to_email:"x11946049@hotmail.com",message:res});
        });
    </script>
</body>
</html>
