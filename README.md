<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>하모니실용음악학원 할인계산기</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.2em;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .header p {
            font-size: 1.3em;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .content {
            padding: 30px;
        }

        .section {
            margin-bottom: 30px;
        }

        .section h2 {
            font-size: 1.4em;
            margin-bottom: 15px;
            color: #333;
            font-weight: bold;
        }

        .discount-info {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
        }

        .discount-rules {
            font-size: 0.95em;
            line-height: 1.6;
        }

        .discount-rules div {
            margin-bottom: 8px;
            font-weight: 500;
        }

        .course-grid {
            display: grid;
            gap: 15px;
        }

        .course-item {
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 12px;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s ease;
        }

        .course-info h3 {
            font-size: 1.2em;
            font-weight: bold;
            margin-bottom: 5px;
            color: #333;
        }

        .course-price {
            font-size: 1.1em;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 5px;
        }

        .course-desc {
            font-size: 0.9em;
            color: #666;
        }

        .counter {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .counter-btn {
            width: 35px;
            height: 35px;
            border: 2px solid #667eea;
            background: white;
            color: #667eea;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2em;
            transition: all 0.2s ease;
        }

        .counter-btn:hover {
            background: #667eea;
            color: white;
        }

        .counter-value {
            font-size: 1.3em;
            font-weight: bold;
            min-width: 20px;
            text-align: center;
        }

        .discount-section {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
        }

        .discount-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
            border-bottom: 1px solid #e9ecef;
        }

        .discount-item:last-child {
            border-bottom: none;
        }

        .discount-info-text h4 {
            font-size: 1.1em;
            font-weight: bold;
            margin-bottom: 3px;
        }

        .discount-info-text p {
            font-size: 0.9em;
            color: #666;
        }

        .discount-counter {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .discount-counter-btn {
            width: 30px;
            height: 30px;
            border: 1px solid #667eea;
            background: white;
            color: #667eea;
            border-radius: 6px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1em;
            font-weight: bold;
        }

        .discount-counter-btn:hover {
            background: #667eea;
            color: white;
        }

        .discount-counter-value {
            font-size: 1.1em;
            font-weight: bold;
            min-width: 15px;
            text-align: center;
        }

        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .checkbox {
            width: 20px;
            height: 20px;
            border: 2px solid #667eea;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            background: white;
            transition: all 0.2s ease;
        }

        .checkbox.checked {
            background: #667eea;
            color: white;
        }

        .result-section {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            margin-top: 20px;
        }

        .result-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .result-item:last-child {
            margin-bottom: 0;
        }

        .final-amount {
            border-top: 2px solid rgba(255,255,255,0.3);
            padding-top: 15px;
            margin-top: 15px;
            font-size: 1.3em;
            font-weight: bold;
        }

        .breakdown {
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            padding: 15px;
            margin-top: 15px;
        }

        .breakdown h4 {
            margin-bottom: 10px;
            font-size: 1.1em;
        }

        .breakdown-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 0.95em;
        }

        .breakdown-total {
            border-top: 1px solid rgba(255,255,255,0.3);
            padding-top: 8px;
            margin-top: 8px;
            font-weight: bold;
        }

        @media (max-width: 600px) {
            .container {
                margin: 10px;
            }
            
            .content {
                padding: 20px;
            }
            
            .header h1 {
                font-size: 1.8em;
            }
            
            .header p {
                font-size: 1.1em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎵 하모니실용음악학원</h1>
            <p>할인 자동 계산기</p>
        </div>
        
        <div class="content">
            <div class="section">
                <h2>💡 간단한 할인 공식</h2>
                <div class="discount-info">
                    <div class="discount-rules">
                        <div>🎯 2과목 선택 = 15% 할인</div>
                        <div>🎯 3과목 선택 = 25% 할인</div>
                        <div>🎯 가족 수강 시 1인당 = 1만원 할인</div>
                        <div>🎯 지인 등록 시 1인당 = 3만원 할인 (첫달)</div>
                        <div>🎯 3개월 일괄결제 시 = 10% 추가 할인</div>
                    </div>
                </div>
            </div>

            <div class="section">
                <h2>📚 수업 선택</h2>
                <div class="course-grid">
                    <div class="course-item">
                        <div class="course-info">
                            <h3>입시반</h3>
                            <div class="course-price">390,000원</div>
                            <div class="course-desc">보컬, 악기, 화성학</div>
                        </div>
                        <div class="counter">
                            <div class="counter-btn" onclick="changeCourse('entrance', -1)">-</div>
                            <div class="counter-value" id="entrance-count">0</div>
                            <div class="counter-btn" onclick="changeCourse('entrance', 1)">+</div>
                        </div>
                    </div>
                    
                    <div class="course-item">
                        <div class="course-info">
                            <h3>개인반</h3>
                            <div class="course-price">180,000원</div>
                            <div class="course-desc">1:1 맞춤 개인 레슨</div>
                        </div>
                        <div class="counter">
                            <div class="counter-btn" onclick="changeCourse('private', -1)">-</div>
                            <div class="counter-value" id="private-count">0</div>
                            <div class="counter-btn" onclick="changeCourse('private', 1)">+</div>
                        </div>
                    </div>
                    
                    <div class="course-item">
                        <div class="course-info">
                            <h3>그룹반</h3>
                            <div class="course-price">130,000원</div>
                            <div class="course-desc">3명 이하 개별 수업</div>
                        </div>
                        <div class="counter">
                            <div class="counter-btn" onclick="changeCourse('group', -1)">-</div>
                            <div class="counter-value" id="group-count">0</div>
                            <div class="counter-btn" onclick="changeCourse('group', 1)">+</div>
                        </div>
                    </div>
                    
                    <div class="course-item">
                        <div class="course-info">
                            <h3>듀엣/밴드반</h3>
                            <div class="course-price">90,000원</div>
                            <div class="course-desc">3명 이상 팀 수업</div>
                        </div>
                        <div class="counter">
                            <div class="counter-btn" onclick="changeCourse('band', -1)">-</div>
                            <div class="counter-value" id="band-count">0</div>
                            <div class="counter-btn" onclick="changeCourse('band', 1)">+</div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="section">
                <h2>💰 추가 할인</h2>
                <div class="discount-section">
                    <div class="discount-item">
                        <div class="discount-info-text">
                            <h4>가족 할인</h4>
                            <p>1인당 10,000원 할인</p>
                        </div>
                        <div class="discount-counter">
                            <div class="discount-counter-btn" onclick="changeDiscount('family', -1)">-</div>
                            <div class="discount-counter-value" id="family-count">0</div>
                            <div class="discount-counter-btn" onclick="changeDiscount('family', 1)">+</div>
                        </div>
                    </div>
                    
                    <div class="discount-item">
                        <div class="discount-info-text">
                            <h4>지인 추천 할인</h4>
                            <p>1인당 30,000원 할인 (첫달)</p>
                        </div>
                        <div class="discount-counter">
                            <div class="discount-counter-btn" onclick="changeDiscount('referral', -1)">-</div>
                            <div class="discount-counter-value" id="referral-count">0</div>
                            <div class="discount-counter-btn" onclick="changeDiscount('referral', 1)">+</div>
                        </div>
                    </div>
                    
                    <div class="discount-item">
                        <div class="discount-info-text">
                            <h4>3개월 일괄결제 할인</h4>
                            <p>10% 추가 할인</p>
                        </div>
                        <div class="checkbox-item">
                            <div class="checkbox" id="bulk-checkbox" onclick="toggleBulkPayment()"></div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="result-section">
                <h2>💳 최종 결제 금액</h2>
                
                <div class="result-item">
                    <span>원래 금액</span>
                    <span id="original-amount">0원</span>
                </div>
                
                <div class="result-item">
                    <span>할인 금액</span>
                    <span id="discount-amount">0원</span>
                </div>
                
                <div class="result-item final-amount">
                    <span>최종 금액</span>
                    <span id="final-amount">0원</span>
                </div>

                <div class="breakdown" id="breakdown">
                    <h4>🔍 할인 내역</h4>
                    <div class="breakdown-item">
                        <span>적용된 할인이 없습니다</span>
                        <span>-</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const courses = {
            entrance: { price: 390000, count: 0 },
            private: { price: 180000, count: 0 },
            group: { price: 130000, count: 0 },
            band: { price: 90000, count: 0 }
        };

        const discounts = {
            family: 0,
            referral: 0,
            bulk: false
        };

        function changeCourse(type, delta) {
            courses[type].count = Math.max(0, courses[type].count + delta);
            document.getElementById(type + '-count').textContent = courses[type].count;
            calculateTotal();
        }

        function changeDiscount(type, delta) {
            discounts[type] = Math.max(0, discounts[type] + delta);
            document.getElementById(type + '-count').textContent = discounts[type];
            calculateTotal();
        }

        function toggleBulkPayment() {
            discounts.bulk = !discounts.bulk;
            const checkbox = document.getElementById('bulk-checkbox');
            if (discounts.bulk) {
                checkbox.classList.add('checked');
                checkbox.textContent = '✓';
            } else {
                checkbox.classList.remove('checked');
                checkbox.textContent = '';
            }
            calculateTotal();
        }

        function calculateTotal() {
            // 총 수업 금액 계산
            let originalAmount = 0;
            let totalCourses = 0;
            
            Object.keys(courses).forEach(key => {
                originalAmount += courses[key].price * courses[key].count;
                totalCourses += courses[key].count;
            });

            let totalDiscount = 0;
            let breakdownItems = [];

            // 다과목 할인
            if (totalCourses >= 2) {
                let courseDiscountPercent = 0;
                if (totalCourses === 2) {
                    courseDiscountPercent = 15;
                } else if (totalCourses >= 3) {
                    courseDiscountPercent = 25;
                }
                
                if (courseDiscountPercent > 0) {
                    const courseDiscount = originalAmount * (courseDiscountPercent / 100);
                    totalDiscount += courseDiscount;
                    breakdownItems.push({
                        text: `다과목 할인 (${totalCourses}과목 - ${courseDiscountPercent}%)`,
                        amount: courseDiscount
                    });
                }
            }

            // 가족 할인
            if (discounts.family > 0) {
                const familyDiscount = discounts.family * 10000;
                totalDiscount += familyDiscount;
                breakdownItems.push({
                    text: `가족 할인 (${discounts.family}인)`,
                    amount: familyDiscount
                });
            }

            // 지인 할인
            if (discounts.referral > 0) {
                const referralDiscount = discounts.referral * 30000;
                totalDiscount += referralDiscount;
                breakdownItems.push({
                    text: `지인 추천 할인 (${discounts.referral}인)`,
                    amount: referralDiscount
                });
            }

            let finalAmount = originalAmount - totalDiscount;

            // 3개월 일괄결제 할인 (최종 금액에서 10% 추가 할인)
            if (discounts.bulk) {
                const bulkDiscount = finalAmount * 0.1;
                totalDiscount += bulkDiscount;
                finalAmount -= bulkDiscount;
                breakdownItems.push({
                    text: '3개월 일괄결제 할인 (10%)',
                    amount: bulkDiscount
                });
            }

            // 화면 업데이트
            document.getElementById('original-amount').textContent = formatCurrency(originalAmount);
            document.getElementById('discount-amount').textContent = formatCurrency(totalDiscount);
            document.getElementById('final-amount').textContent = formatCurrency(finalAmount);

            // 할인 내역 업데이트
            updateBreakdown(breakdownItems, totalDiscount);
        }

        function updateBreakdown(items, total) {
            const breakdown = document.getElementById('breakdown');
            let html = '<h4>🔍 할인 내역</h4>';
            
            if (items.length === 0) {
                html += '<div class="breakdown-item"><span>적용된 할인이 없습니다</span><span>-</span></div>';
            } else {
                items.forEach(item => {
                    html += `<div class="breakdown-item"><span>${item.text}</span><span>-${formatCurrency(item.amount)}</span></div>`;
                });
                html += `<div class="breakdown-item breakdown-total"><span><strong>총 할인</strong></span><span><strong>-${formatCurrency(total)}</strong></span></div>`;
            }
            
            breakdown.innerHTML = html;
        }

        function formatCurrency(amount) {
            return new Intl.NumberFormat('ko-KR').format(Math.round(amount)) + '원';
        }

        // 초기 계산
        calculateTotal();
    </script>
</body>
</html>
