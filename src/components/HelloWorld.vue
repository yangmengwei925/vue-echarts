<template>
	<div class="echart">
		 <!-- <div ref="orgOptionsline" :style="{width:'800px',height:'200px'}"></div>  -->
		<div ref="oroptionmapjsonr" :style="{width:'400px',height:'400px'}"></div>
		 <!-- <div ref="orgOptionsbar" :style="{width:'800px',height:'380px'}"></div> -->
	</div>
</template>

<script>
	var ltopdata = [{
			name: '北京',
			value: 2
		},
		{
			name: '天津',
			value: 1
		},
		{
			name: '上海',
			value: 2
		},
		{
			name: '重庆',
			value: 1
		},
		{
			name: '河北',
			value: 1
		},
		{
			name: '河南',
			value: 1
		},
		{
			name: '云南',
			value: 1
		},
		{
			name: '辽宁',
			value: 1
		},
		{
			name: '黑龙江',
			value: 1
		},
		{
			name: '湖南',
			value: 1
		},
	]
	import chinaJson from 'echarts/map/json/china.json'
	console.log(chinaJson)
	export default {
		name: 'HelloWorld',
		data() {
			return {
				orgOptionsline: {
					textStyle: {
						color: "#9cbfde"
					},
					color: ['#2da8ff', '#ffce55', '#ec87bf'], //手动设置每个图例的颜色
					grid: {
						left: '30px',
						right: '0px',
						top: '10px',
						bottom: "30px"
					},
					xAxis: {
						type: 'category',
						boundaryGap: true,
						axisLine: {
							show: false,
							lineStyle: {
								color: "#e7e7e7"
							}
						},
						axisTick: {
							show: false
						},
						data: ['a', 'b', 'c', 'd', 'e']
					},
					yAxis: {
						type: 'value',
						boundaryGap: true,
						// 网格线
						splitLine: {
							lineStyle: {
								color: '#e7e7e7'
							}
						},
						// 坐标轴轴线样式
						axisLine: {
							show: false,
						},
						// 坐标轴刻度
						axisTick: {
							show: false
						},
					},
					series: [{
						name: 'a',
						type: 'line',
						symbol: 'circle', //拐点样式
						symbolSize: 4,
						stack: '总量1',
						lineStyle: {
							width: 1
						},
						data: [10, 40, 20, 50, 50]
					}, ]
				},

				oroptionmapjsonr: {
					textStyle: {
						color: "#9cbfde",
						fontSize: 10.67,
					},
					color: ['#fff'], //手动设置每个图例的颜色
					tooltip: {
						// trigger: 'item',
						formatter: function(params) {
							var percent = 0;
							var total = 0;
							for (var i = 0; i < ltopdata.length; i++) {
								if (params.name == ltopdata[i].name) {
									if (params.name !== '') {
										return params.name + '\n' + ltopdata[i].value;
									} else {
										return '';
									}
								}

							}

						},
					},
					legend: {
						show: false
					},
					toolbox: {
						show: true,
						orient: 'vertical',
						x: 'right',
						y: 'center',
					},
					roamController: {
						show: true,
						x: 'right',
						mapTypeControl: {
							'china': true
						}
					},
					series: [{
						name: 'iphoneX',
						type: 'map',
						mapType: 'china',
						roam: false,
						left: '25%',
						top: '25%',
						// zoom: 1,
						center: [115.97, 29.71],
						// aspectScale:1,
						itemStyle: {
							normal: {
								label: {
									show: false
								},
								areaColor: '#fff',
								borderColor: '#41c7db ',
								borderWidth: 1,
							},
							emphasis: {
								areaColor: '#41c7db '
							},

						},
						data: ltopdata
					}]
				},
				orgOptionsbar: {


					color: ['#3398DB'],
					grid: {
						left: '3%',
						right: '4%',
						bottom: '5%',
						containLabel: true
					},
					xAxis: [{
						type: 'category',
						data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
						axisTick: {
							show: false
						},
						axisLabel: {
							show: true
						},
						// 坐标轴轴线样式
						axisLine: {
							show: false
						},
					}],
					yAxis: [{
						type: 'value', // 网格线
						splitLine: {
							lineStyle: {
								color: '#e7e7e7'
							}
						},
						axisTick: {
							show: false
						},
						// 坐标轴轴线样式
						axisLine: {
							show: false,
						},
					}],
					series: [{
						name: '直接访问',
						type: 'bar',
						barWidth: '60%',
						data: [10, 52, 200, 334, 390, 330, 220]
					}]
				},
			}
		},
		mounted() {
			this.echarts()
		},
		methods: {
			// 图表
			echarts() {
				//  var orgOptionsline_charts = this.$echarts.init(this.$refs.orgOptionsline);
				//  orgOptionsline_charts.setOption(this.orgOptionsline)
				// this.$echarts.registerMap('china', chinaJson);
				 var oroptionmapjsonr_charts = this.$echarts.init(this.$refs.oroptionmapjsonr);
				 oroptionmapjsonr_charts.setOption(this.oroptionmapjsonr)
				// var orgOptionsbar_charts = this.$echarts.init(this.$refs.orgOptionsbar);
				// orgOptionsbar_charts.setOption(this.orgOptionsbar)
			},
		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
