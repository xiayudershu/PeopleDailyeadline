<template>
	<div class="wordmain" style="overflow:hidden">
		     <el-container style="overflow:hidden">
		        <el-main class="wordcloudmain" style="overflow:hidden">
					<div class="words">
						<words @word-clicked="handleWordClicked" :msg="words2" :clickyear="8"></words>

					</div>
				</el-main>
				
				<el-aside class="wordcloudside" style="overflow:hidden">

				<div class="chart">
					
					<charts :chartData="chartData"></charts>
					
				</div>
				</el-aside>
		      </el-container>
	</div>
</template>

<script>
import words from "../wordcloud/words.vue"
import charts from "../wordcloud/chart.vue"
export default {
  components: {
    words,charts
  },
  data() {
    return {
      chartData: {
		   description:  ['蓬勃发展的津巴布韦教育事业', '中牟县发展乡镇企业珍惜耕地', '叙利亚重视发展农业'],
		   frequency:  [1260, 228, 3616, 8240, 9422, 1598, 4514, 9872, 22528, 25846, 18006],
		   word:'发展',
		   index:7
	   },
      clickedWord: '',
	words2 :[
		{'text': '发展', 'size': 7229},{'text': '改革', 'size': 5688},{'text': '企业', 'size': 2814},{'text': '国际', 'size': 2493},{'text': '合作', 'size': 2460},{'text': '人民', 'size': 2378},{'text': '谈判', 'size': 1516},{'text': '研制', 'size': 1252},{'text': '技术', 'size': 1214},{'text': '吴学谦', 'size': 1214},{'text': '人才', 'size': 1130},{'text': '出口', 'size': 998},{'text': '粮食', 'size': 998},{'text': '承包', 'size': 997},{'text': '开放', 'size': 970},{'text': '整党', 'size': 948},{'text': '金牌', 'size': 914},{'text': '中国队', 'size': 787},{'text': '贸易', 'size': 744},{'text': '学术', 'size': 740},{'text': '邓小平', 'size': 382},{'text': '蓬勃发展', 'size': 126},{'text': '外资', 'size': 124},{'text': '振兴中华', 'size': 120},{'text': '外向型经济', 'size': 120},{'text': '引进技术', 'size': 116},{'text': '整治', 'size': 110},{'text': '典型', 'size': 110},{'text': '机构改革', 'size': 109},{'text': '深入基层', 'size': 108},{'text': '走向世界', 'size': 108},{'text': '出口创汇', 'size': 106},{'text': '复苏', 'size': 104},{'text': '集体企业', 'size': 102},{'text': '先进技术', 'size': 102},{'text': '不结盟运动', 'size': 98},{'text': '艰苦奋斗', 'size': 92},{'text': '对外开放政策', 'size': 92},{'text': '新技术革命', 'size': 92},{'text': '参加奥运会', 'size': 90},{'text': '坚持四项基本原则', 'size': 88},{'text': '政治体制改革', 'size': 88},{'text': '治理整顿', 'size': 84},{'text': '党的建设', 'size': 82},{'text': '巴勒斯坦问题', 'size': 81}
		],
      wordData: [
		 {'word': '发展', 'descriptions': ['蓬勃发展的津巴布韦教育事业', '中牟县发展乡镇企业珍惜耕地', '叙利亚重视发展农业'], 'frequency': [1260, 228, 3616, 8240, 9422, 1598, 4514, 9872, 22528, 25846, 18006]},
		 {'word': '改革', 'descriptions': ['保共中央政治局部署改革工作', '中捷改革经验可相互借鉴', '十三届三中全会确定今后改革步骤'], 'frequency': [628, 58, 1168, 1372, 486, 40, 578, 8260, 9298, 5802, 5097]},
		 {'word': '企业', 'descriptions': ['南京事业单位实行企业化管理', '表示欢迎更多欧洲企业家到中国投资', '一些重点企业违反国家规定  大量截留动用统配钢材水泥'], 'frequency': [414, 64, 1810, 1940, 1116, 290, 1692, 6692, 15248, 8468, 4722]},
		 {'word': '国际', 'descriptions': ['青岛国际钓鱼赛收竿', '“中国面对未来”国际研讨会在京开幕', '趵突泉啤酒跻身国际市场'], 'frequency': [590, 196, 4196, 5082, 3004, 660, 2356, 6990, 17496, 8906, 5053]},
		 {'word': '合作', 'descriptions': ['中共四川省委组织部经过调查追认在中美合作所遇难的六十位先烈为烈士', '中法两国关于发展经济关系和合作的长期协定等签订', '中新、中澳友好合作关系走向新阶段'], 'frequency': [1000, 96, 5568, 4140, 2536, 708, 1564, 4238, 9836, 9010, 6576]},
		 {'word': '人民', 'descriptions': ['加强人民代表大会制度 恢复设立国家主席副主席', '人民日报社长秦川在旧金山举行招待会', '亳县人民政府为群众办实事'], 'frequency': [7268, 2052, 34316, 44764, 40404, 2770, 3698, 5688, 9080, 8688, 6245]},
		 {'word': '谈判', 'descriptions': ['泰老准备谈判解决边界问题', '巴阿间接谈判结束苏撤军问题仍无进展', '西提要求越与民柬谈判被阮基石拒绝'], 'frequency': [154, 4, 2146, 1772, 352, 218, 680, 1848, 2680, 950, 380]},
		 {'word': '研制', 'descriptions': ['大型强磁选机研制成功', '广州研制成烟花爆竹安全火药', '保加利亚研制出一种戒烟“烟”'], 'frequency': [0, 0, 0, 4, 48, 40, 300, 1264, 2502, 398, 126]},
		 {'word': '技术', 'descriptions': ['我国沸腾燃烧技术已进入世界先进行列', '亚洲开发银行向我国提供技术援助', '普及科学技术知识的好形式'], 'frequency': [470, 44, 2702, 6464, 2538, 672, 1720, 5354, 7724, 2828, 1694]},
		 {'word': '吴学谦', 'descriptions': ['吴学谦宴请西哈努克亲王和夫人', '吴学谦离京赴朝鲜访问', '吴学谦同莫兰举行会谈'], 'frequency': [0, 0, 0, 2, 2, 4, 0, 1226, 392, 4, 2]},
		 {'word': '人才', 'descriptions': ['《人才信息》杂志创刊', '致富要人才人才等不来靖江新桥乡农民集资请高校代培', '吸引专业人才到牧区工作'], 'frequency': [4, 4, 68, 110, 12, 74, 464, 1758, 2738, 2946, 1554]},
		 {'word': '出口', 'descriptions': ['山东陶瓷公司产品独具特色不断扩大出口', '潮汕平原努力增加水产品出口', '努力生产  扩大出口  多创外汇'], 'frequency': [174, 46, 310, 332, 398, 70, 654, 1552, 3764, 1874, 631]},
		 {'word': '粮食', 'descriptions': ['河南一季完成全年粮食征购任务', '文安县粮食系统带头“消化”粮食', '世界屋脊上的粮食专业户洛桑旺堆'], 'frequency': [302, 86, 2424, 1932, 1046, 168, 484, 1270, 1834, 1176, 573]},
		 {'word': '承包', 'descriptions': ['稳定和完善联产承包责任制', '山东省冶金工业总公司坚持承包制  以政策稳定促进企业生产持续发展', '吉林省推行承包经营后来居上'], 'frequency': [2, 0, 14, 6, 2, 0, 152, 1698, 662, 192, 43]},
		 {'word': '开放', 'descriptions': ['井冈山革命博物馆“八一”前夕开放', '福建沿海航标灯遮蔽孤将开放', '荣成县供销社  经营设施向社会开放'], 'frequency': [56, 8, 170, 172, 34, 50, 294, 1976, 3690, 2436, 2469]},
		 {'word': '整党', 'descriptions': ['四川省级机关在整党中抓紧落实知识分子政策', '整党给中原油田带来新气象', '段君毅在北京市委全会上谈整党'], 'frequency': [286, 0, 54, 10, 52, 6, 8, 972, 0, 0, 1]},
		 {'word': '金牌', 'descriptions': ['解放军北京小将获青运会头两块金牌', '亚运会第四天决出二十枚金牌', '世界短跑道速滑比赛 加拿大获全部金牌'], 'frequency': [0, 0, 6, 2, 0, 0, 100, 974, 2004, 746, 168]},
		 {'word': '中国队', 'descriptions': ['世界艺术体操锦标赛中国队又获一枚银牌', '中国队有攻势无建树被香港队逼和', '中国队首战负于瑞典队'], 'frequency': [0, 0, 16, 50, 38, 16, 104, 802, 2714, 1868, 628]},
		 {'word': '贸易', 'descriptions': ['新加坡对外贸易的特点', '关于日中贸易不平衡问题', '美国应采取措施消除障碍扩大中美经济贸易关系'], 'frequency': [700, 68, 2754, 2894, 3308, 520, 874, 2156, 3364, 1676, 1164]},
		 {'word': '学术', 'descriptions': ['国际工程教育学术讨论会在捷举行', '台港大陆学生合办学术研讨会', '“国际技术转移学术讨论会”在京举行'], 'frequency': [22, 2, 176, 608, 48, 110, 346, 1006, 1346, 836, 378]},
		 {'word': '邓小平', 'descriptions': ['叶剑英邓小平李先念陈云同志题词', '介绍邓小平同志关心科学、教育工作', '邓小平会见胡萨克'], 'frequency': [0, 4, 44, 672, 1282, 392, 442, 476, 1654, 466, 37]},
		 {'word': '蓬勃发展', 'descriptions': ['十年来教育事业在改革中蓬勃发展', '海峡两岸转口贸易蓬勃发展', '蓬勃发展的匈牙利食品工业'], 'frequency': [12, 0, 42, 158, 560, 30, 34, 126, 274, 62, 48]},
		 {'word': '外资', 'descriptions': ['利用外资引进技术  开创新的局面', '中国外资企业服务部在北京成立', '农业银行两年引进外资三亿多美元'], 'frequency': [2, 0, 8, 22, 62, 2, 50, 328, 1360, 648, 339]},
		 {'word': '振兴中华', 'descriptions': ['树人树木  振兴中华', '为了振兴中华', '北京举行“‘振兴中华’读书竞赛”知识测验发奖大会'], 'frequency': [0, 0, 0, 0, 0, 0, 64, 126, 100, 20, 5]},
		 {'word': '外向型经济', 'descriptions': ['辽河三角洲将建成外向型经济示范区', '南化公司发展外向型经济路子宽', '江苏电子行业朝外向型经济迈步'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 122, 134, 2, 3]},
		 {'word': '引进技术', 'descriptions': ['大连起重机厂多方引进技术', '冶金系统对引进技术重视消化吸收', '关卡重重引进技术何其难工程师疾呼克服官僚主义'], 'frequency': [0, 0, 0, 0, 0, 12, 10, 116, 22, 4, 0]},
		 {'word': '整治', 'descriptions': ['在整治和廉政建设中领导干部要作表率', '开发建设必须与国土整治水土保持同步', '在整治和廉政建设中领导干部要作表率'], 'frequency': [0, 0, 4, 32, 6, 2, 18, 132, 884, 918, 724]},
		 {'word': '典型', 'descriptions': ['查处典型案件  加强党性教育', '老典型的新面貌', '河北抓住典型事例反腐蚀'], 'frequency': [72, 6, 142, 138, 506, 48, 72, 134, 254, 430, 328]},
		 {'word': '机构改革', 'descriptions': ['四川七厅局支持渡口市机构改革', '十亿人民关注机构改革', '达县市委查处诬告他人干扰机构改革事件'], 'frequency': [2, 0, 0, 0, 0, 0, 24, 118, 254, 116, 84]},
		 {'word': '深入基层', 'descriptions': ['宁阳县各级领导深入基层解决问题', '河池市商业局领导深入基层召开咨询谈心会', '福建主要领导与会少深入基层多'], 'frequency': [0, 0, 24, 202, 350, 32, 54, 108, 168, 48, 25]},
		 {'word': '走向世界', 'descriptions': ['我电子产品开始走向世界', '走向世界的宁夏人', '法国舆论评我国成功发射试验卫星中国航天技术正在走向世界    马特拉公司赞扬中国快速认真履行合同'], 'frequency': [0, 0, 4, 8, 0, 0, 12, 126, 346, 140, 90]},
		 {'word': '出口创汇', 'descriptions': ['实施沿海经济发展战略关键必须抓好出口创汇', '山西轻工产品大批出口创汇', '山东半岛八个县各显神通去年出口创汇县县超亿元'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 108, 140, 8, 1]},
		 {'word': '复苏', 'descriptions': ['秃岭吐绿  土地复苏  沁水政府荒山建村落  且看开发热', '自动翻译技术在法国复苏', '英国经济复苏势头减弱'], 'frequency': [14, 0, 20, 40, 2, 4, 8, 144, 350, 416, 443]},
		 {'word': '集体企业', 'descriptions': ['发展同农民经济联合真正按集体企业对待', '沈阳市二轻集体企业越办越好', '泉州一集体企业创汇二百多万美元'], 'frequency': [0, 0, 0, 0, 0, 0, 102, 114, 62, 0, 0]},
		 {'word': '先进技术', 'descriptions': ['北京华丽衬衫厂重管理  积极消化吸收先进技术', '上海先进技术向各地辐射', '“六五”期间引进先进技术开始发挥作用'], 'frequency': [0, 4, 36, 68, 18, 26, 28, 102, 42, 16, 6]},
		 {'word': '不结盟运动', 'descriptions': ['不结盟运动和国际经济新秩序', '纪念不结盟运动诞生二十五周年', '要求不结盟运动开除越南'], 'frequency': [0, 0, 0, 0, 56, 84, 108, 102, 88, 24, 6]},
		 {'word': '艰苦奋斗', 'descriptions': ['赵紫阳强调发扬艰苦奋斗精神', '总参第一测绘大队艰苦奋斗堪称楷模', '青海省唐曲农场党委成员  发扬艰苦奋斗的优良传统'], 'frequency': [26, 2, 20, 198, 990, 22, 82, 106, 252, 102, 38]},
		 {'word': '对外开放政策', 'descriptions': ['中国实行对外开放政策坚定不移', '中国对外开放政策没有变', '对中国实行对外开放政策深表敬意'], 'frequency': [0, 0, 0, 0, 0, 0, 20, 92, 8, 2, 0]},
		 {'word': '新技术革命', 'descriptions': ['新技术革命和现代化', '让激光在新技术革命中起飞', '中央机关干部新技术革命知识讲座第二阶段将于七月下旬开讲'], 'frequency': [0, 0, 0, 2, 4, 0, 0, 92, 6, 0, 2]},
		 {'word': '参加奥运会', 'descriptions': ['举重“神童”被允许参加奥运会', '摩西将代表参加奥运会的运动员宣誓', '国际奥委会主席呼吁非洲国家参加奥运会'], 'frequency': [0, 0, 4, 10, 4, 0, 16, 90, 50, 20, 2]},
		 {'word': '坚持四项基本原则', 'descriptions': ['常德开展坚持四项基本原则宣传教育三万名党员中有六千余人被评为优秀', '搞好坚持四项基本原则的正面教育', '坚持四项基本原则坚持又红又专'], 'frequency': [0, 0, 0, 0, 0, 0, 16, 92, 18, 4, 0]},
		 {'word': '政治体制改革', 'descriptions': ['政治体制改革是我国生产力发展的客观要求', '把政治体制改革提到日程上来', '北京青年学者踊跃参与政治体制改革的探讨'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 98, 12, 22, 4]},
		 {'word': '治理整顿', 'descriptions': ['佳木斯以治理整顿促廉政建设', '中央关于特区政策是正确的  治理整顿对特区不搞一刀切', '坚定不移治理整顿在稳定中求得发展  完善民主安定秩序推进政治体制改革'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 88, 194, 38, 1]},
		 {'word': '党的建设', 'descriptions': ['薄一波谈整党和党的建设', '在改革开放的新形势下加强和改进机关党的建设', '临漳县委集中精力抓党的建设'], 'frequency': [2, 0, 4, 12, 58, 4, 22, 88, 418, 384, 143]},
		 {'word': '巴勒斯坦问题', 'descriptions': ['要求公正解决巴勒斯坦问题', '巴勒斯坦问题的新进展', '巴勒斯坦问题不结盟委员会部长级会议闭幕'], 'frequency': [12, 0, 0, 14, 52, 2, 34, 84, 60, 4, 14]},
 ]
    };
  },
  methods: {
    handleWordClicked(word) {
      this.clickedWord = word;
      console.log(word);
      
      // 查找匹配的词对应的描述
      const foundWord = this.wordData.find(item => item.word === this.clickedWord);
      if (foundWord) {
        console.log(foundWord.frequency);
	     this.chartData.description=foundWord.descriptions;
		 this.chartData.frequency=foundWord.frequency;
		 this.chartData.word=foundWord.word;
      } else {
        console.log('未找到匹配的词描述');
      }
    },
  },
};
</script>

<style>
.wordmain{
	margin-left:-5vw;
}
.wordcloudmain{
	width:40vw;
	margin-top: -15vh;
}
.wordcloudside{
	width:30vw;
}
.words{
    width: 40vw;
    height: 90vh;
	margin-top: -10vh;
}
.chart{
  width: 25vw;
  height: auto;
    
}

</style>