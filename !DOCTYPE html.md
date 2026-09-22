<!DOCTYPE html>  
<html lang="zh-CN">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>全球法西斯与民族主义指数地图</title>  
    <!-- 引入 ECharts 地图库 -->  
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/dist/echarts.min.js"></script>  
    <script src="https://cdn.jsdelivr.net/npm/echarts@5.4.3/map/js/world.js"></script>  
    <style>  
        * {  
            box-sizing: border-box;  
            margin: 0;  
            padding: 0;  
        }  
        body {  
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;  
            background-color: #121212;  
            color: #e0e0e0;  
            display: flex;  
            flex-direction: column;  
            align-items: center;  
            min-height: 100vh;  
            padding: 20px;  
        }  
        header {  
            text-align: center;  
            margin-bottom: 20px;  
        }  
        h1 {  
            font-size: 2rem;  
            color: #ffffff;  
            margin-bottom: 8px;  
        }  
        p.subtitle {  
            font-size: 0.95rem;  
            color: #a0a0a0;  
            max-width: 700px;  
        }  
        #map-container {  
            width: 100%;  
            max-width: 1100px;  
            height: 600px;  
            background: #1e1e1e;  
            border-radius: 12px;  
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);  
            overflow: hidden;  
        }  
        @media (max-width: 768px) {  
            #map-container {  
                height: 450px;  
            }  
            h1 {  
                font-size: 1.5rem;  
            }  
        }  
    </style>  
</head>  
<body>  
  
    <header>  
        <h1>全球法西斯与极端民族主义指数</h1>  
        <p class="subtitle">Realistically presenting the fascism and ultranationalism index across regions of the world.</p>  
    </header>  
  
    <div id="map-container"></div>  
  
    <script>  
        const chartDom = document.getElementById('map-container');  
        const myChart = echarts.init(chartDom, 'dark');  
  
        // 示例数据（数值范围 0 - 100）  
        const mapData = [  
            { name: 'United States', value: 42 },  
            { name: 'Russia', value: 85 },  
            { name: 'China', value: 65 },  
            { name: 'Germany', value: 30 },  
            { name: 'France', value: 38 },  
            { name: 'United Kingdom', value: 35 },  
            { name: 'India', value: 72 },  
            { name: 'Brazil', value: 50 },  
            { name: 'Japan', value: 40 },  
            { name: 'Italy', value: 45 },  
            { name: 'Turkey', value: 78 },  
            { name: 'Hungary', value: 70 },  
            { name: 'Poland', value: 55 }  
        ];  
  
        const option = {  
            backgroundColor: '#1e1e1e',  
            title: {  
                text: '指数分布图 (0-100)',  
                left: '20',  
                top: '20',  
                textStyle: {  
                    color: '#ccc',  
                    fontSize: 14  
                }  
            },  
            tooltip: {  
                trigger: 'item',  
                formatter: function (params) {  
                    const value = params.value ? params.value : '暂无数据';  
                    return `<strong>${params.name}</strong><br/>法西斯/民族主义指数: <span style="color:#ff4d4f;font-weight:bold;">${value}</span>`;  
                }  
            },  
            visualMap: {  
                min: 0,  
                max: 100,  
                text: ['高', '低'],  
                realtime: false,  
                calculable: true,  
                inRange: {  
                    color: ['#313695', '#4575b4', '#74add1', '#fdae61', '#f46d43', '#d73027', '#a50026']  
                },  
                textStyle: {  
                    color: '#fff'  
                },  
                bottom: '30',  
                left: '30'  
            },  
            series: [  
                {  
                    name: '法西斯指数',  
                    type: 'map',  
                    map: 'world',  
                    roam: true,  
                    emphasis: {  
                        label: {  
                            show: true,  
                            color: '#fff'  
                        },  
                        itemStyle: {  
                            areaColor: '#ffd700'  
                        }  
                    },  
                    data: mapData  
                }  
            ]  
        };  
  
        myChart.setOption(option);  
  
        window.addEventListener('resize', function() {  
            myChart.resize();  
        });  
    </script>  
</body>  
</html>  
