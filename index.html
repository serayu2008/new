<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2025 기온 및 전력수요량 분석 시스템</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --text-color: #212529;
            --primary: #4dadf7;
            --secondary: #ff8787;
            --border-color: #dee2e6;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        h1 {
            color: #343a40;
            margin-bottom: 10px;
        }

        .status-container {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-bottom: 20px;
        }

        .status-badge {
            padding: 8px 16px;
            border-radius: 20px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            font-size: 0.9rem;
            font-weight: bold;
        }

        .status-badge.loaded {
            background-color: #e3fafc;
            color: #0b7285;
            border-color: #99e9f2;
        }

        /* 컨트롤러 디자인 */
        .controls {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            margin-bottom: 25px;
            align-items: center;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        label {
            font-size: 0.85rem;
            font-weight: 600;
            color: #495057;
        }

        select, input {
            padding: 8px 12px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 0.95rem;
            outline: none;
        }

        select:focus, input:focus {
            border-color: #339af0;
        }

        button {
            padding: 10px 20px;
            background-color: #339af0;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            align-self: flex-end;
            margin-top: auto;
            transition: background-color 0.2s;
        }

        button:hover {
            background-color: #228be6;
        }

        /* 차트 영역 */
        .chart-card {
            background-color: var(--card-bg);
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            margin-bottom: 25px;
            position: relative;
            height: 500px;
        }

        /* 요약 통계 영역 */
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .summary-card {
            background-color: var(--card-bg);
            padding: 15px;
            border-radius: 8px;
            border-left: 5px solid #339af0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.02);
        }

        .summary-card:nth-child(2) { border-left-color: #ff922b; }
        .summary-card:nth-child(3) { border-left-color: #fab005; }
        .summary-card:nth-child(4) { border-left-color: #fa5252; }

        .summary-card h3 {
            margin: 0 0 8px 0;
            font-size: 0.85rem;
            color: #868e96;
            text-transform: uppercase;
        }

        .summary-card p {
            margin: 0;
            font-size: 1.4rem;
            font-weight: bold;
            color: #343a40;
        }

        .loading-overlay {
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(255,255,255,0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            font-size: 1.2rem;
            z-index: 10;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>2025 기온 vs 전력수요 분석 시스템</h1>
        <p>전력거래소 시간별 전국 전력수요량 및 기상청 서울 기온 데이터 융합 시각화</p>
        
        <div class="status-container">
            <div id="status-temp" class="status-badge">기온 데이터 로딩 중...</div>
            <div id="status-power" class="status-badge">전력 데이터 로딩 중...</div>
        </div>
    </header>

    <div class="controls">
        <div class="control-group">
            <label for="view-mode">분석 모드</label>
            <select id="view-mode">
                <option value="daily-trend">특정 날짜의 24시간 추이 분석</option>
                <option value="monthly-scatter">월별 기온-전력수요 상관관계 (산점도)</option>
            </select>
        </div>

        <div class="control-group" id="date-group">
            <label for="target-date">조회 날짜</label>
            <input type="date" id="target-date" min="2025-01-01" max="2025-12-31" value="2025-01-01">
        </div>

        <div class="control-group" id="month-group" style="display: none;">
            <label for="target-month">조회 월</label>
            <select id="target-month">
                <option value="all">2025년 전체</option>
                <option value="01">1월 (한겨울)</option>
                <option value="02">2월</option>
                <option value="03">3월</option>
                <option value="04">4월</option>
                <option value="05">5월</option>
                <option value="06">6월</option>
                <option value="07">7월 (한여름)</option>
                <option value="08">8월 (한여름)</option>
                <option value="09">9월</option>
                <option value="10">10월</option>
                <option value="11">11월</option>
                <option value="12">12월</option>
            </select>
        </div>

        <button id="btn-update">분석하기</button>
    </div>

    <div class="chart-card">
        <div id="loading" class="loading-overlay">데이터를 불러오는 중입니다...</div>
        <canvas id="mainChart"></canvas>
    </div>

    <div class="summary-grid" id="summary-section">
        <div class="summary-card">
            <h3 id="lbl-meta-1">선택일 평균 기온</h3>
            <p id="val-meta-1">-</p>
        </div>
        <div class="summary-card">
            <h3 id="lbl-meta-2">최저 / 최고 기온</h3>
            <p id="val-meta-2">-</p>
        </div>
        <div class="summary-card">
            <h3 id="lbl-meta-3">하루 총 전력수요량</h3>
            <p id="val-meta-3">-</p>
        </div>
        <div class="summary-card">
            <h3 id="lbl-meta-4">최대 전력수요 (시간)</h3>
            <p id="val-meta-4">-</p>
        </div>
    </div>
</div>

<script>
    // 파일명 정의 (HTML 파일과 같은 경로)
    const FILE_TEMP = "2025 기온.csv";
    const FILE_POWER = "한국전력거래소_시간별 전국 전력수요량_20251231.csv";

    // 글로벌 데이터 저장소
    let tempRawData = [];
    let powerRawData = [];
    let tempMap = {};  // 날짜별 기온 매핑 {"2025-01-01": {avg, min, max}}
    let powerMap = {}; // 날짜별 전력수요 매핑 {"2025-01-01": [1시, 2시, ... 24시]}

    let chartInstance = null;

    // 페이지 로드 시 파일 자동 가져오기
    window.addEventListener('DOMContentLoaded', () => {
        loadDataFiles();
        setupEventListeners();
    });

    function setupEventListeners() {
        const viewMode = document.getElementById('view-mode');
        const dateGroup = document.getElementById('date-group');
        const monthGroup = document.getElementById('month-group');
        const btnUpdate = document.getElementById('btn-update');

        viewMode.addEventListener('change', (e) => {
            if (e.target.value === 'daily-trend') {
                dateGroup.style.display = 'flex';
                monthGroup.style.display = 'none';
            } else {
                dateGroup.style.display = 'none';
                monthGroup.style.display = 'flex';
            }
        });

        btnUpdate.addEventListener('click', updateVisualization);
    }

    // CSV 파일 로드 및 파싱 (PapaParse)
    function loadDataFiles() {
        let tempLoaded = false;
        let powerLoaded = false;

        // 1. 기온 파일 로드 (상단 7라인에 텍스트가 있으므로 skipFirstLines 혹은 파싱 후 전처리 적용)
        Papa.parse(FILE_TEMP, {
            download: true,
            header: true,
            skipEmptyLines: true,
            complete: function(results) {
                // 상단 메타데이터 필터링하고 실제 헤더가 있는 데이터만 추출
                const data = results.data.filter(row => row['날짜'] && row['지점']);
                processTempData(data);
                tempLoaded = true;
                document.getElementById('status-temp').innerText = "기온 데이터 완료";
                document.getElementById('status-temp').classList.add('loaded');
                checkAllLoaded(tempLoaded, powerLoaded);
            },
            error: function(err) {
                document.getElementById('status-temp').innerText = "기온 파일 오류";
                console.error(err);
            }
        });

        // 2. 전력수요 파일 로드
        Papa.parse(FILE_POWER, {
            download: true,
            header: true,
            skipEmptyLines: true,
            complete: function(results) {
                processPowerData(results.data);
                powerLoaded = true;
                document.getElementById('status-power').innerText = "전력 데이터 완료";
                document.getElementById('status-power').classList.add('loaded');
                checkAllLoaded(tempLoaded, powerLoaded);
            },
            error: function(err) {
                document.getElementById('status-power').innerText = "전력 파일 오류";
                console.error(err);
            }
        });
    }

    function checkAllLoaded(t, p) {
        if (t && p) {
            document.getElementById('loading').style.display = 'none';
            updateVisualization(); // 초기 로드 시 한 번 실행
        }
    }

    // 기온 데이터 구조화
    function processTempData(data) {
        data.forEach(row => {
            // 정규식을 사용해 공백이나 탭 문자 제거하여 날짜 포맷 정리 (\t2025-01-01 -> 2025-01-01)
            let dateKey = row['날짜'].trim();
            tempMap[dateKey] = {
                avg: parseFloat(row['평균기온(℃)']),
                min: parseFloat(row['최저기온(℃)']),
                max: parseFloat(row['최고기온(℃)'])
            };
        });
    }

    // 전력 데이터 구조화
    function processPowerData(data) {
        data.forEach(row => {
            let dateKey = row['날짜'].trim();
            let dayPower = [];
            // 1시부터 24시까지 데이터 배열화
            for (let i = 1; i <= 24; i++) {
                let val = row[`${i}시`] ? parseInt(row[`${i}시`].replace(/,/g, '')) : 0;
                dayPower.push(val);
            }
            powerMap[dateKey] = dayPower;
        });
    }

    // 메인 시각화 업데이트 스위치
    function updateVisualization() {
        const mode = document.getElementById('view-mode').value;
        if (mode === 'daily-trend') {
            renderDailyTrend();
        } else {
            renderScatterPlot();
        }
    }

    // 1. 특정 날짜 24시간 분석 (이중 축 선 그래프)
    function renderDailyTrend() {
        const targetDate = document.getElementById('target-date').value;
        const hours = Array.from({length: 24}, (_, i) => `${i + 1}시`);
        
        const powerData = powerMap[targetDate];
        const tempData = tempMap[targetDate];

        if (!powerData || !tempData) {
            alert("선택한 날짜의 데이터를 찾을 수 없습니다.");
            return;
        }

        // 요약정보 대시보드 업데이트
        document.getElementById('lbl-meta-1').innerText = `${targetDate} 평균 기온`;
        document.getElementById('val-meta-1').innerText = `${tempData.avg} ℃`;
        document.getElementById('lbl-meta-2').innerText = "최저 / 최고 기온";
        document.getElementById('val-meta-2').innerText = `${tempData.min}℃ / ${tempData.max}℃`;

        const totalPower = powerData.reduce((a, b) => a + b, 0);
        const maxPower = Math.max(...powerData);
        const maxHour = powerData.indexOf(maxPower) + 1;

        document.getElementById('lbl-meta-3').innerText = "하루 총 전력수요량";
        document.getElementById('val-meta-3').innerText = `${totalPower.toLocaleString()} MW`;
        document.getElementById('lbl-meta-4').innerText = "최대 전력 (시간대)";
        document.getElementById('val-meta-4').innerText = `${maxPower.toLocaleString()} MW (${maxHour}시)`;

        // 기존 차트 파괴
        if (chartInstance) chartInstance.destroy();

        // 24시간 가상의 온도 변화 분포 곡선 생성 (데이터 세분화 대안: 최고/최저치 활용 매칭)
        // 여기서는 시간 변화에 따라 최저기온(새벽5시)~최고기온(오후2시) 흐름을 간단히 추정하여 데모 시각화 구현
        let simulatedHourlyTemp = hours.map((_, index) => {
            let ratio = Math.sin((index - 6) / 24 * 2 * Math.PI) * 0.5 + 0.5; // 가상의 사인 곡선 기온 변화
            return Math.round((tempData.min + (tempData.max - tempData.min) * ratio) * 10) / 10;
        });

        const ctx = document.getElementById('mainChart').getContext('2d');
        chartInstance = new Chart(ctx, {
            type: 'line',
            data: {
                labels: hours,
                datasets: [
                    {
                        label: '전력수요량 (MW)',
                        data: powerData,
                        borderColor: '#228be6',
                        backgroundColor: 'rgba(34, 139, 230, 0.1)',
                        yAxisID: 'y-power',
                        tension: 0.3,
                        fill: true
                    },
                    {
                        label: '추정 시간별 기온 (℃)',
                        data: simulatedHourlyTemp,
                        borderColor: '#fa5252',
                        backgroundColor: '#fa5252',
                        yAxisID: 'y-temp',
                        tension: 0.4,
                        borderDash: [5, 5],
                        pointRadius: 3
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                interaction: { mode: 'index', intersect: false },
                plugins: {
                    title: { display: true, text: `${targetDate} 전력수요량 및 기온 추이 (시간별)` }
                },
                scales: {
                    'y-power': {
                        type: 'linear',
                        position: 'left',
                        title: { display: true, text: '전력수요량 (MW)' }
                    },
                    'y-temp': {
                        type: 'linear',
                        position: 'right',
                        title: { display: true, text: '기온 (℃)' },
                        grid: { drawOnChartArea: false }
                    }
                }
            }
        });
    }

    // 2. 기온과 전력수요 분산도 (산점도 분석)
    function renderScatterPlot() {
        const targetMonth = document.getElementById('target-month').value;
        let scatterData = [];

        let totalDays = 0;
        let sumTemp = 0;
        let sumPowerMax = 0;

        // 모든 날짜 순회하며 데이터 결합
        Object.keys(tempMap).forEach(date => {
            // 월 필터링
            if (targetMonth !== 'all' && date.split('-')[1] !== targetMonth) return;

            const powerData = powerMap[date];
            if (powerData) {
                const maxPowerOfDay = Math.max(...powerData); // 당일 피크 수요
                const avgTempOfDay = tempMap[date].avg;

                scatterData.push({ x: avgTempOfDay, y: maxPowerOfDay, date: date });

                sumTemp += avgTempOfDay;
                sumPowerMax += maxPowerOfDay;
                totalDays++;
            }
        });

        if(scatterData.length === 0) {
            alert("조건에 부합하는 데이터가 부족합니다.");
            return;
        }

        // 요약보드 통계 업데이트
        document.getElementById('lbl-meta-1').innerText = "분석 기간 평균 기온";
        document.getElementById('val-meta-1').innerText = `${(sumTemp / totalDays).toFixed(1)} ℃`;
        document.getElementById('lbl-meta-2').innerText = "분석 대상 일수";
        document.getElementById('val-meta-2').innerText = `${totalDays} 일`;
        document.getElementById('lbl-meta-3').innerText = "평균 일일 최대 전력";
        document.getElementById('val-meta-3').innerText = `${Math.round(sumPowerMax / totalDays).toLocaleString()} MW`;
        document.getElementById('lbl-meta-4').innerText = "특이사항";
        document.getElementById('val-meta-4').innerText = "냉·난방 임계점 확인";

        if (chartInstance) chartInstance.destroy();

        const ctx = document.getElementById('mainChart').getContext('2d');
        chartInstance = new Chart(ctx, {
            type: 'scatter',
            data: {
                datasets: [{
                    label: '일일 최고전력 vs 평균기온',
                    data: scatterData,
                    backgroundColor: 'rgba(77, 173, 247, 0.7)',
                    borderColor: '#1c7ed6',
                    pointRadius: 5
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
