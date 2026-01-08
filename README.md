<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI引流数据看板 | Lordhair</title>
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/dist/echarts.min.js"></script>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif; }
        body { background: #f5f6f7; padding: 20px; }
        .container { max-width: 1200px; margin: 0 auto; }
        .header { text-align: center; margin-bottom: 30px; padding: 20px; background: white; border-radius: 10px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .chart-row { display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 20px; }
        .chart-box { flex: 1; min-width: 300px; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .chart-title { font-size: 16px; font-weight: bold; margin-bottom: 15px; color: #333; }
        .chart { width: 100%; height: 300px; }
        @media (max-width: 768px) { .chart-row { flex-direction: column; } }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📊 Lordhair AI引流数据可视化看板</h1>
            <p>数据周期：2023年3月-12月 | 平台：LH、NT、BN</p>
        </div>
        
        <div class="chart-row">
            <div class="chart-box">
                <div class="chart-title">📈 引流趋势总览</div>
                <div class="chart" id="chart1"></div>
            </div>
            <div class="chart-box">
                <div class="chart-title">🏆 平台对比</div>
                <div class="chart" id="chart2"></div>
            </div>
        </div>
        
        <div class="chart-row">
            <div class="chart-box">
                <div class="chart-title">🔄 转化率分析</div>
                <div class="chart" id="chart3"></div>
            </div>
            <div class="chart-box">
                <div class="chart-title">🎯 工具占比</div>
                <div class="chart" id="chart4"></div>
            </div>
        </div>
    </div>

    <script>
        // 初始化图表
        document.addEventListener('DOMContentLoaded', function() {
            const chart1 = echarts.init(document.getElementById('chart1'));
            const chart2 = echarts.init(document.getElementById('chart2'));
            
            // 图表1: 趋势图
            chart1.setOption({
                title: { text: '各平台ChatGPT引流趋势', left: 'center' },
                tooltip: { trigger: 'axis' },
                xAxis: { type: 'category', data: ['3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'] },
                yAxis: { type: 'value' },
                series: [
                    { name: 'LH', type: 'line', data: [286,606,1208,1524,2278,1164,1381,1489,1554,1248] },
                    { name: 'NT', type: 'line', data: [65,119,94,203,225,746,1453,1435,1102,729] },
                    { name: 'BN', type: 'line', data: [85,186,121,270,187,3466,7342,7909,6551,5676] }
                ]
            });
            
            // 图表2: 柱状图
            chart2.setOption({
                title: { text: '12月各工具引流对比', left: 'center' },
                tooltip: { trigger: 'axis' },
                xAxis: { type: 'category', data: ['ChatGPT', 'Perplexity', 'Gemmini'] },
                yAxis: { type: 'value' },
                series: [
                    { name: 'LH', type: 'bar', data: [1248, 47, 0] },
                    { name: 'NT', type: 'bar', data: [729, 94, 136] },
                    { name: 'BN', type: 'bar', data: [5676, 3810, 22] }
                ]
            });
        });
        
        // 响应式调整
        window.addEventListener('resize', function() {
            if (chart1) chart1.resize();
            if (chart2) chart2.resize();
        });
    </script>
</body>
</html>
