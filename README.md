<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>台中行程點餐單</title>
    <style>
        body { font-family: -apple-system, sans-serif; background: #f8f9fa; color: #212529; padding: 15px; max-width: 600px; margin: 0 auto; }
        h1, p.subtitle { text-align: center; }
        h1 { font-size: 19px; color: #343a40; }
        p.subtitle { color: #6c757d; font-size: 13px; margin-bottom: 20px; }
        .card { background: #fff; border-radius: 8px; padding: 15px; margin-bottom: 15px; box-shadow: 0 1px 3px rgba(0,0,0,0.05); }
        .card-title { font-size: 14px; font-weight: bold; margin-bottom: 10px; color: #343a40; border-left: 4px solid #007bff; padding-left: 8px; }
        .fixed-text { font-size: 13px; color: #495057; line-height: 1.5; background: #f1f3f5; padding: 10px; border-radius: 6px; margin-bottom: 10px; }
        .option-label { display: block; background: #fdfdfd; border: 1px solid #dee2e6; border-radius: 6px; padding: 10px; margin-bottom: 8px; cursor: pointer; }
        .option-input { margin-right: 8px; }
        .option-name { font-weight: 600; font-size: 13.5px; color: #212529; }
        .option-desc { font-size: 12.5px; color: #6c757d; display: block; margin-left: 22px; margin-top: 2px; }
        .other-input { width: 85%; margin-left: 22px; margin-top: 5px; padding: 6px; border: 1px solid #ced4da; border-radius: 4px; font-size: 13px; display: none; }
        .sub-question { margin-left: 15px; border-left: 2px dashed #ced4da; padding-left: 10px; margin-top: 10px; display: none; }
        button.submit-btn { display: block; width: 100%; background: #007bff; color: #fff; border: none; padding: 12px; font-size: 15px; font-weight: bold; border-radius: 6px; cursor: pointer; margin-top: 20px; }
        #result-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); justify-content: center; align-items: center; padding: 15px; z-index: 999; }
        .modal-content { background: #fff; padding: 20px; border-radius: 8px; max-width: 500px; width: 100%; max-height: 80vh; overflow-y: auto; }
        textarea { width: 100%; height: 250px; font-size: 13px; padding: 10px; box-sizing: border-box; border: 1px solid #ced4da; border-radius: 4px; resize: none; background: #f8f9fa; line-height: 1.4; }
        .modal-btns { display: flex; justify-content: flex-end; margin-top: 10px; }
        .modal-btn { padding: 6px 12px; border-radius: 4px; border: none; cursor: pointer; font-weight: 500; background: #e9ecef; color: #495057; }
    </style>
</head>
<body>
    <h1>台中冬日自駕四天三夜行程規劃</h1>
    <p class="subtitle">親愛的，請選出妳想體驗的住宿與美食選項</p>
    <form id="itinerary-form">
        <div class="card">
            <div class="card-title">🏨 住宿盲盒（三選一，連住三晚不挪窩）</div>
            <label class="option-label"><input type="radio" name="hotel" value="鳥人創意旅店" class="option-input" required><span class="option-name">鳥人創意旅店（西屯區）</span><span class="option-desc">主打地窖、沙漠、原始森林風格，拍照視覺衝擊力高。</span></label>
            <label class="option-label"><input type="radio" name="hotel" value="台中芭蕾城堡酒店" class="option-input" required><span class="option-name">台中芭蕾城堡酒店（南屯區）</span><span class="option-desc">主打歐洲城堡渡假感，部分房型有私人空中花園與雙人按摩浴缸。</span></label>
            <label class="option-label"><input type="radio" name="hotel" value="沐蘭精品旅館" class="option-input" required><span class="option-name">沐蘭精品旅館（西屯區）</span><span class="option-desc">森林系頂級 Villa 風格，融入落羽松與大量植物植栽，奢華療癒。</span></label>
        </div>
        <div class="card">
            <div class="card-title">📅 第一天 行程安排</div>
            <div class="fixed-text">【下午】機場接機（準備手搖飲微糖少冰）<br>【下午茶】宮原眼科第四信用合作社（雙球冰淇淋，兩人分食）<br>【傍晚】旅店辦理入住、放置行李、梳洗更衣</div>
            <div style="font-size:13px; font-weight:bold; margin-bottom:6px;">請選擇晚餐大餐：</div>
            <label class="option-label"><input type="radio" name="d1_dinner" value="這一鍋 皇室秘藏鍋物" class="option-input" required onclick="toggleOther('d1_dinner',false)"><span class="option-name">這一鍋 皇室秘藏鍋物（七期朝富店）</span><span class="option-desc">浮誇東方宮廷風火鍋。可以用墨魚汁在豆腐紙上寫字，牛肉自帶乾冰。</span></label>
            <label class="option-label"><input type="radio" name="d1_dinner" value="永心鳳茶" class="option-input" required onclick="toggleOther('d1_dinner',false)"><span class="option-name">永心鳳茶（勤美誠品店）</span><span class="option-desc">時髦老洋房復古茶沙龍。用紅酒杯喝台灣冷泡茶，吃精緻現代台菜。</span></label>
            <label class="option-label"><input type="radio" name="d1_dinner" value="other" class="option-input" required onclick="toggleOther('d1_dinner',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d1_dinner_other" class="other-input" placeholder="請輸入想吃的餐廳或小吃"></label>
            <div style="font-size:13px; font-weight:bold; margin:10px 0 6px 0; color:#007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
            <label><input type="radio" name="d1_alcohol" value="yes" required onclick="toggleSub('d1_alc_section',true)"> 是</label>
            <label style="margin-left:20px;"><input type="radio" name="d1_alcohol" value="no" required onclick="toggleSub('d1_alc_section',false)"> 否，今天想早點休息</label>
            <div id="d1_alc_section" class="sub-question"><div class="fixed-text">【晚上】前往七期秋紅谷都市夜景散步，隨後前往特色酒吧小酌。</div></div>
            <div class="fixed-text" style="margin-top:8px;">【宵夜】旅店房內 Uber Eats 外送（地瓜球與期間限定草莓芝芝）<br>【深夜】開箱超商統一布丁限定款（翻轉布丁「丁布」或無焦糖版「統一布布」）</div>
        </div>
        <div class="card">
            <div class="card-title">📅 第二天 行程安排</div>
            <div style="font-size:13px; font-weight:bold; margin-bottom:6px;">【早餐】請選擇早餐（兩人分食一份）：</div>
            <label class="option-label"><input type="radio" name="d2_breakfast" value="肉蛋吐司" class="option-input" required onclick="toggleOther('d2_breakfast',false)"><span class="option-name">肉蛋吐司（健行總店）</span><span class="option-desc">台灣神級排隊老店。炭烤吐司夾上爆汁軟嫩豬排，配冰豆漿。</span></label>
            <label class="option-label"><input type="radio" name="d2_breakfast" value="明賢行" class="option-input" required onclick="toggleOther('d2_breakfast',false)"><span class="option-name">明賢行</span><span class="option-desc">老宅改建的文青風台式早午餐。吃得到精跡乾淨的控肉飯、炒麵與點心。</span></label>
            <label class="option-label"><input type="radio" name="d2_breakfast" value="other" class="option-input" required onclick="toggleOther('d2_breakfast',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d2_breakfast_other" class="other-input" placeholder="請輸入想吃的早餐"></label>
            <div class="fixed-text">【中午至下午】西區全日慢活散步（車停草悟道大停車場，步行參觀審計新村、勤美誠品聖誕村、草悟廣場）</div>
            <div style="font-size:13px; font-weight:bold; margin:8px 0 6px 0;">【下午茶】馬卡龍（二選一，外帶車上吃）：</div>
            <label class="option-label"><input type="radio" name="d2_macaron" value="CJSJ 法式甜點店" class="option-input" required onclick="toggleOther('d2_macaron',false)"><span class="option-name">CJSJ 法式甜點店（西區）</span><span class="option-desc">米其林三星主廚創意法式甜點。馬卡龍精緻如藝術品，特別減糖調整。</span></label>
            <label class="option-label"><input type="radio" name="d2_macaron" value="繽色絲 貝殼馬卡龍" class="option-input" required onclick="toggleOther('d2_macaron',false)"><span class="option-name">繽色絲 Princess 貝殼馬卡龍（西屯區）</span><span class="option-desc">造型吸睛的肥卡龍與貝殼馬卡龍。外殼繽紛，內餡厚實飽滿口味創新。</span></label>
            <label class="option-label"><input type="radio" name="d2_macaron" value="other" class="option-input" required onclick="toggleOther('d2_macaron',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d2_macaron_other" class="other-input" placeholder="請輸入想吃的甜點"></label>
            <div style="font-size:13px; font-weight:bold; margin:8px 0 6px 0;">【晚餐】燒肉晚餐（二選一，單點精緻肉品不撐胃）：</div>
            <label class="option-label"><input type="radio" name="d2_dinner" value="茶六燒肉堂" class="option-input" required onclick="toggleOther('d2_dinner',false)"><span class="option-name">茶六燒肉堂（公益店）</span><span class="option-desc">台中燒肉天花板。裝潢大氣，肉質精緻，無限續喝的溫暖味噌魚湯。</span></label>
            <label class="option-label"><input type="radio" name="d2_dinner" value="屋馬燒肉" class="option-input" required onclick="toggleOther('d2_dinner',false)"><span class="option-name">屋馬燒肉（園邸店）</span><span class="option-desc">傳奇燒肉始祖。貼心桌邊服務、無限續喝黃金雞湯，可加購海鮮粥。</span></label>
            <label class="option-label"><input type="radio" name="d2_dinner" value="other" class="option-input" required onclick="toggleOther('d2_dinner',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d2_dinner_other" class="other-input" placeholder="請輸入想吃的餐廳"></label>
            <div style="font-size:13px; font-weight:bold; margin:10px 0 6px 0; color:#007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
            <label><input type="radio" name="d2_alcohol" value="yes" required onclick="toggleSub('d2_alc_section',true)"> 是</label>
            <label style="margin-left:20px;"><input type="radio" name="d2_alcohol" value="no" required onclick="toggleSub('d2_alc_section',false)"> 否，想直接回房間泡澡</label>
            <div id="d2_alc_section" class="sub-question">
                <div style="font-size:13px; font-weight:bold; margin-bottom:5px;">請選擇今晚想去的特色酒吧：</div>
                <label class="option-label"><input type="radio" name="d2_bar" value="Isman Bar 三十參酒館" class="option-input"><span class="option-name">Isman Bar 三十參酒館</span><span class="option-desc">英倫特務風 Speakeasy 密室酒吧。門口偽裝成西裝店，需輸入密碼進入。</span></label>
                <label class="option-label"><input type="radio" name="d2_bar" value="Vender Bar" class="option-input"><span class="option-name">Vender Bar</span><span class="option-desc">榮獲亞洲50大最佳酒吧。門口偽裝成自動販賣機，調酒視覺風味世界級。</span></label>
            </div>
        </div>
        <div class="card">
            <div class="card-title">📅 第三天 行程安排</div>
            <div style="font-size:13px; font-weight:bold; margin-bottom:6px;">【早午餐】請選擇早午餐（兩人分食一份）：</div>
            <label class="option-label"><input type="radio" name="d3_breakfast" value="模範貝果" class="option-input" required onclick="toggleOther('d3_breakfast',false)"><span class="option-name">模範貝果</span><span class="option-desc">手工貝果名店。多種台灣在地內餡（如剝皮辣椒、芋泥），口感紮實。</span></label>
            <label class="option-label"><input type="radio" name="d3_breakfast" value="一人一伴" class="option-input" required onclick="toggleOther('d3_breakfast',false)"><span class="option-name">一人一伴 ともだち</span><span class="option-desc">日式老宅三明治專賣。招牌厚切炸豬排三明治與千層蛋捲，空間療癒。</span></label>
            <label class="option-label"><input type="radio" name="d3_breakfast" value="other" class="option-input" required onclick="toggleOther('d3_breakfast',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d3_breakfast_other" class="other-input" placeholder="請輸入想吃的早午餐"></label>
            <div class="fixed-text">【中午】台中國家歌劇院（無直角曲牆建築參觀、頂樓空中花園）<br>【午餐】鼎王麻辣鍋公益店（麻辣與酸菜白肉鴛鴦雙拼，主攻老油條與鴨血豆腐）<br>【下午】高美濕地落日（前往海邊木棧道，觀賞風車與冬日晚霞，備有防風外套與暖暖包）</div>
            <div style="font-size:13px; font-weight:bold; margin:10px 0 6px 0; color:#007bff;">【微醺開關】今天晚上是否需要安排喝酒行程？</div>
            <label><input type="radio" name="d3_alcohol" value="yes" required onclick="toggleSub('d3_alc_section',true)"> 是</label>
            <label style="margin-left:20px;"><input type="radio" name="d3_alcohol" value="no" required onclick="toggleSub('d3_alc_section',false)"> 否，今天吹完海風想喝熱湯休息</label>
            <div id="d3_alc_section" class="sub-question">
                <div style="font-size:13px; font-weight:bold; margin-bottom:5px;">請選擇今晚旅店外送晚餐（搭配18天生啤酒）：</div>
                <label class="option-label"><input type="radio" name="d3_dinner" value="生猛海產熱炒店外送" class="option-input"><span class="option-name">生猛海產熱炒店外送</span><span class="option-desc">外送九層塔炒蛤蜊、金沙苦瓜、鳳梨蝦球。配上超限定台灣18天生啤酒。</span></label>
                <label class="option-label"><input type="radio" name="d3_dinner" value="傳統小吃外送大集合" class="option-input"><span class="option-name">指標性傳統小吃外送大集合（蚵仔煎與滷肉飯）</span><span class="option-desc">外送邊緣酥脆、醬汁靈魂的蚵仔煎，搭配滷到軟爛入味、充滿膠質的爌肉飯。</span></label>
                <label class="option-label"><input type="radio" name="d3_dinner" value="other" class="option-input" onclick="toggleOther('d3_dinner',true)"><span class="option-name">其他（自填外送備案）</span><input type="text" id="d3_dinner_other" class="other-input" placeholder="請輸入想叫外送的食物"></label>
            </div>
            <div class="fixed-text" style="margin-top:10px;">【深夜】深夜解饞：外送或得來速享用台灣限定麥當勞神級玉米湯，配旅店雙人按摩大浴缸</div>
        </div>
        <div class="card">
            <div class="card-title">📅 第四天 行程安排</div>
            <div style="font-size:13px; font-weight: bold; margin-bottom:6px;">【早午餐】在地老靈魂早午餐（二選一，兩人分食）：</div>
            <label class="option-label"><input type="radio" name="d4_breakfast" value="王家菜頭粿糯米腸" class="option-input" required onclick="toggleOther('d4_breakfast',false)"><span class="option-name">王家菜頭粿糯米腸</span><span class="option-desc">傳統第二市場傳奇。必點菜頭粿、糯米腸、荷包蛋三合一，配老賴紅茶。</span></label>
            <label class="option-label"><input type="radio" name="d4_breakfast" value="山河魯肉飯" class="option-input" required onclick="toggleOther('d4_breakfast',false)"><span class="option-name">山河魯肉飯</span><span class="option-desc">想大口吃肉的選擇。道地大塊爌肉滷肉飯，肉質軟爛入味，配上一碗蜆仔湯。</span></label>
            <label class="option-label"><input type="radio" name="d4_breakfast" value="other" class="option-input" required onclick="toggleOther('d4_breakfast',true)"><span class="option-name">其他（自填備案）</span><input type="text" id="d4_breakfast_other" class="other-input" placeholder="請輸入想吃的早午餐"></label>
            <div class="fixed-text" style="margin-top:8px;">【中午】伴手禮衝刺（前往如邑堂太陽餅或俊美鳳梨酥採買，直接放車後廂）<br>【下午】抵達機場辦理登機回香港</div>
        </div>
        <button type="submit" class="submit-btn">完成選擇，生成行程結果</button>
    </form>
    <div id="result-modal">
        <div class="modal-content">
            <div class="modal-title">📋 12月冬日台中．微醺通行證 (VVIP PASS)</div>
            <p style="font-size:12px; color:#dc3545; text-align:center; margin-bottom:10px;">親愛的，恭喜妳成功解鎖盲盒！請立刻截圖發給 Isaac 解鎖行程，啟動妳的專屬台中冬日自駕之旅。</p>
            <textarea id="result-text" readonly onclick="this.select()"></textarea>
            <div class="modal-btns"><button class="modal-btn" onclick="closeModal()">返回修改</button></div>
        </div>
    </div>
    <script src="https://jsdelivr.net"></script>
    <script>
        emailjs.init("VlUqNiaw_M1XN169M");
        function toggleOther(name,show){const input=document.getElementById(name+'_other');if(input)input.style.display=show?'block':'none';}
        function toggleSub(id,show){const section=document.getElementById(id);section.style.display=show?'block':'none';const inputs=section.querySelectorAll('input');inputs.forEach(i=>i.required=show);}
        function closeModal(){document.getElementById('result-modal').style.display='none';}
        document.getElementById('itinerary-form').addEventListener('submit',function(e){
            e.preventDefault();const formData=new FormData(this);
            let getVal=(name)=>{let val=formData.get(name);if(val==='other'){return"【自填】"+(document.getElementById(name+'_other').value||"未填寫");}return val||"未安排";};
            let res="台中四天三夜自駕行程選擇結果：\n\n";
            res+="🏨 連住三晚旅店：\n"+formData.get('hotel')+"\n\n";
            res+="📅 第一天行程：\n- 【下午】機場接機 ➔ 宮原眼科第四信用合作社\n- 【傍晚】旅店入住梳洗\n- 【晚餐】"+getVal('d1_dinner')+"\n";
            if(formData.get('d1_alcohol')==='yes'){res+="- 【晚上】秋紅谷夜景散步 ➔ 特色酒吧小酌\n";}
            res+="- 【宵夜】房內外送（地瓜球、草莓芝芝）\n- 【深夜】超商開箱統一布丁限定款\n\n";
            res+="📅 第二天行程：\n- 【早餐】"+getVal('d2_breakfast')+"\n- 【中午至下午】西區全日慢活散步\n- 【下午茶】馬卡龍："+getVal('d2_macaron')+"\n- 【晚餐】燒肉："+getVal('d2_dinner')+"\n";
            if(formData.get('d2_alcohol')==='yes'){res+="- 【晚上酒吧】"+formData.get('d2_bar')+"\n";}res+="\n";
            res+="📅 第三天行程：\n- 【早午餐】"+getVal('d3_breakfast')+"\n- 【中午】台中國家歌劇院\n- 【午餐】鼎王麻辣鍋公益店\n- 【下午】高美濕地看落日夕陽\n";
            if(formData.get('d3_alcohol')==='yes'){res+="- 【晚餐】旅店外送熱炒/小吃（配18天生啤酒）："+getVal('d3_dinner')+"\n";}
            res+="- 【深夜】台灣限定麥當勞玉米湯配按摩大浴缸\n\n";
            res+="📅 第四天行程：\n- 【早午餐】"+getVal('d4_breakfast') + "\n- 【中午】伴手禮採買（如邑堂或俊美）\n- 【下午】抵達機場登機\n\n我選好了！";
            document.getElementById('result-text').value=res;
            document.getElementById('result-modal').style.display='flex';
            emailjs.send("service_w1v9g3g","template_m2h0x4r",{to_email:"x11946049@hotmail.com",message:res});
        });
    </script>
</body>
</html>
