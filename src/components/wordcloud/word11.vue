<template>
	<div class="wordmain" style="overflow:hidden">
		     <el-container style="overflow:hidden">
		        <el-main class="wordcloudmain" style="overflow:hidden">
					<div class="words">
						<words @word-clicked="handleWordClicked" :msg="words2" :clickyear="11"></words>

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
		   description: ['习近平等领导同志当选  为十二届全国人大代表', '习近平会见梅德韦杰夫总理', '习近平接受十四国新任驻华大使递交国书'],
		   frequency: [0, 0, 0, 0, 0, 0, 0, 0, 4, 1304, 4910],
		   word:'习近平',
		   index:10
	   },
      clickedWord: '',
	words2 :[
		{'text': '发展', 'size': 14997},{'text': '习近平', 'size': 8155},{'text': '创新', 'size': 5343},{'text': '新时代', 'size': 3600},{'text': '脱贫', 'size': 3260},{'text': '乡村', 'size': 3044},{'text': '人民', 'size': 3004},{'text': '高质量发展', 'size': 2941},{'text': '李克强', 'size': 2934},{'text': '疫情', 'size': 2684},{'text': '一带一路', 'size': 2582},{'text': '国际', 'size': 2454},{'text': '科技', 'size': 2182},{'text': '健康', 'size': 2168},{'text': '法治', 'size': 2164},{'text': '基层', 'size': 2026},{'text': '生态', 'size': 1989},{'text': '转型', 'size': 1728},{'text': '民生', 'size': 1688},{'text': '中国特色', 'size': 1518},{'text': '和平发展', 'size': 200},{'text': '以人民为中心', 'size': 200},{'text': '国家安全', 'size': 200},{'text': '自我革命', 'size': 196},{'text': '民营经济', 'size': 194},{'text': '工匠精神', 'size': 194},{'text': '依法治国', 'size': 188},{'text': '协商民主', 'size': 188},{'text': '供给侧结构性改革', 'size': 187},{'text': '贫困县', 'size': 186},{'text': '简政放权', 'size': 182},{'text': '人与自然', 'size': 182},{'text': '讲好中国故事', 'size': 178},{'text': '网络安全', 'size': 177},{'text': '幸福感', 'size': 176},{'text': '智慧城市', 'size': 176},{'text': '从严治党', 'size': 176},{'text': '产业扶贫', 'size': 172},{'text': '自主创新', 'size': 169},{'text': '中国力量', 'size': 168},{'text': '党的领导', 'size': 168},{'text': '全面依法治国', 'size': 162},{'text': '中国道路', 'size': 160},{'text': '党的建设', 'size': 158},{'text': '稳中求进', 'size': 158},{'text': '和谐共生', 'size': 158},{'text': '数字化转型', 'size': 158}
		],
      wordData: [
		 {'word': '发展', 'descriptions': ['昂首阔步，融入国家发展大局', '处理好农民和土地关系 促进“三农”工作健康发展', '关注中国发展蓝图'], 'frequency': [1260, 228, 3616, 8240, 9422, 1598, 4514, 9872, 22528, 25846, 18006]},
		 {'word': '习近平', 'descriptions': ['习近平等领导同志当选  为十二届全国人大代表', '习近平会见梅德韦杰夫总理', '习近平接受十四国新任驻华大使递交国书'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 4, 1304, 4910]},
		 {'word': '创新', 'descriptions': ['守望创新  成就梦想', '以互联网思维整合科技创新资源', '烟台三站批发交易市场：创新共享模式，支持外贸企业发展'], 'frequency': [30, 20, 70, 118, 120, 20, 150, 510, 2932, 8336, 7333]},
		 {'word': '新时代', 'descriptions': ['新青年引领新时代', '在弘扬传统中续写新时代双拥工作新篇章', '奋发有为显担当 建功立业新时代'], 'frequency': [92, 26, 110, 80, 64, 2, 26, 38, 138, 164, 2255]},
		 {'word': '脱贫', 'descriptions': ['让脱贫人口端稳就业饭碗', '组织走前头 脱贫有奔头', '老区通了“脱贫路”'], 'frequency': [0, 0, 4, 6, 4, 0, 2, 250, 786, 196, 2040]},
		 {'word': '乡村', 'descriptions': ['为乡村振兴注入强劲动力', '以法治助力乡村振兴', '清洁乡村资金管理应规范'], 'frequency': [60, 4, 122, 102, 92, 8, 28, 234, 588, 1030, 2682]},
		 {'word': '人民', 'descriptions': ['王学风：战斗英雄 人民铭记', '“建设一支听党指挥能打胜仗作风优良的人民军队”', '中国教育，把答卷写在人民的心上'], 'frequency': [7268, 2052, 34316, 44764, 40404, 2770, 3698, 5688, 9080, 8688, 6245]},
		 {'word': '高质量发展', 'descriptions': ['培养高技能人才 推动高质量发展', '微创机器人公司：持续创新，推动行业高质量发展', '推动新时代党的民族工作高质量发展'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 4, 2081]},
		 {'word': '李克强', 'descriptions': ['李克强将出席2012中国国际投资贸易洽谈会  暨第三届中国—阿拉伯国家经贸论坛开幕式', '李克强向乌兹别克斯坦新任总理阿里波夫致贺电', '李克强同齐普拉斯出席第二届中希海洋合作论坛并致辞'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 6, 826, 1626]},
		 {'word': '疫情', 'descriptions': ['为打赢疫情防控阻击战提供支持', '王毅主持四国外长应对疫情视频会议', '克服疫情影响 打赢脱贫攻坚战'], 'frequency': [0, 10, 4, 4, 0, 0, 2, 12, 42, 850, 1412]},
		 {'word': '一带一路', 'descriptions': ['乌克兰成立一带一路贸易投资促进中心', '一带一路绘就民心相通美好画卷', '强化一带一路建设学理支撑'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1568]},
		 {'word': '国际', 'descriptions': ['坚定维护国际公平正义', '中方将派团出席在沙特吉达举行的乌克兰问题国际会议', '王东明出席第十届国际生态大会'], 'frequency': [590, 196, 4196, 5082, 3004, 660, 2356, 6990, 17496, 8906, 5053]},
		 {'word': '科技', 'descriptions': ['商务部、科技部调整发布《中国禁止出口限制出口技术目录》', '全国工商联民营企业科技创新工作会议召开', '科技 引领文化新跨越'], 'frequency': [0, 0, 2, 388, 498, 376, 1088, 3346, 9778, 4182, 3215]},
		 {'word': '健康', 'descriptions': ['用法治促进民营企业健康成长', '金融为实体经济健康发展提供有力支撑', '抓住“丝路”机遇打造健康生态圈'], 'frequency': [58, 10, 258, 348, 284, 18, 266, 506, 1886, 2680, 2189]},
		 {'word': '法治', 'descriptions': ['筑牢公共卫生安全法治防线', '将法治精髓融入点滴生活', '给利益博弈套上法治缰绳'], 'frequency': [6, 0, 10, 16, 16, 0, 40, 150, 884, 1060, 2218]},
		 {'word': '基层', 'descriptions': ['能上艺术殿堂 能下基层边防', '在基层，需妥善处理利益关系', '科技赋能基层党建'], 'frequency': [4, 2, 444, 810, 818, 86, 346, 988, 2522, 2840, 1834]},
		 {'word': '生态', 'descriptions': ['出台生态河道评价标准', '你改变，政治生态就改变', '80余家港航企业签倡议书保护长江生态'], 'frequency': [0, 0, 0, 12, 4, 4, 30, 264, 1442, 2644, 3143]},
		 {'word': '转型', 'descriptions': ['服务贸易 转型升级新引擎', '经济转型给外资注入长远信心', '文化部全面推动文化娱乐行业转型升级'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 4, 72, 1338, 1657]},
		 {'word': '民生', 'descriptions': ['流动党员 服务民生', '培育民生文化  打造文化民生', '西藏七成以上财力投向民生领域'], 'frequency': [214, 48, 654, 380, 198, 30, 144, 196, 358, 2384, 1495]},
		 {'word': '中国特色', 'descriptions': ['坚定建设中国特色世界一流大学的自信', '中国特色强军之路迈出新步伐', '学习贯彻习近平新时代中国特色社会主义思想主题教育对外宣讲会举行'], 'frequency': [0, 0, 0, 0, 0, 0, 2, 88, 550, 1150, 990]},
		 {'word': '和平发展', 'descriptions': ['着眼世界大局  促进和平发展', '把握和平发展、互利合作大方向  推进东亚合作健康发展', '第二届两岸和平发展法学论坛在京举行'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 4, 36, 276, 217]},
		 {'word': '以人民为中心', 'descriptions': ['以人民为中心 书写人权保障光辉篇章', '与时代同步伐以人民为中心', '构建以人民为中心的智慧社会'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 10, 134]},
		 {'word': '国家安全', 'descriptions': ['中华人民共和国香港特别行政区维护国家安全法', '王小洪会见所罗门群岛警察、国家安全与惩教部部长维科', '切实履行好维护国家安全的神圣使命'], 'frequency': [0, 0, 10, 40, 28, 14, 32, 46, 138, 180, 424]},
		 {'word': '自我革命', 'descriptions': ['协同推进社会革命和自我革命', '以党的自我革命引领社会革命', '在推进自我革命中当先锋作表率'], 'frequency': [0, 0, 0, 20, 10, 0, 0, 0, 2, 8, 110]},
		 {'word': '民营经济', 'descriptions': ['第三届民营经济法治建设峰会举行', '发挥桥梁纽带作用，助力民营经济高质量发展', '中国光彩事业促进会第六次会员代表大会暨全国抗击新冠肺炎疫情民营经济先进个人表彰大会召开'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 2, 50, 148, 150]},
		 {'word': '工匠精神', 'descriptions': ['我们的“工匠精神”去哪儿了', '格兰仕：弘扬工匠精神 实现智能制造', '以推进供给侧结构性改革为主线形成新动能培育与传统动能改造提升互促共进弘扬企业家精神和工匠精神提升中国制造水平'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 108]},
		 {'word': '依法治国', 'descriptions': ['深入推进全面依法治国', '充分发挥律师队伍在全面依法治国中的重要作用', '开辟全面依法治国新境界'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 210, 110, 182]},
		 {'word': '协商民主', 'descriptions': ['协商民主大势所趋', '协商民主是符合中国国情的民主实现形式', '协商民主走进新时代'], 'frequency': [0, 0, 2, 0, 0, 0, 0, 12, 2, 30, 108]},
		 {'word': '供给侧结构性改革', 'descriptions': ['打赢供给侧结构性改革硬仗', '把创新贯穿于供给侧结构性改革全过程', '河北 大力推进供给侧结构性改革'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 115]},
		 {'word': '贫困县', 'descriptions': ['贵州贫困县全部脱贫摘帽', '广西贺州“三变”清零贫困县', '贫困县的“富”教育'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 44, 110, 38, 99]},
		 {'word': '简政放权', 'descriptions': ['江西 “三单一网”推动简政放权落地', '简政放权应便民利民', '四问：简政放权怎样更“有感”'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 42, 4, 6, 93]},
		 {'word': '人与自然', 'descriptions': ['建设人与自然和谐共生的美丽中国', '促进人与自然和谐共生', '读懂“人与自然是生命共同体”的深刻意蕴'], 'frequency': [0, 0, 2, 0, 0, 0, 0, 0, 46, 98, 136]},
		 {'word': '讲好中国故事', 'descriptions': ['运用数字艺术讲好中国故事', '聚焦华人生活  讲好中国故事', '“创新国际传播 讲好中国故事”研讨会在京举行'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 103]},
		 {'word': '网络安全', 'descriptions': ['我国将调查2015年信息网络安全状况', '长亭科技发布全新网络安全产品', '孟建柱会见美国网络安全执法跨部门代表团'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 24, 58, 157]},
		 {'word': '幸福感', 'descriptions': ['“幸福感”：发展中凸显人的分量', '民生改善，提升公众“幸福感”', '着力增强国民幸福感'], 'frequency': [0, 0, 0, 2, 0, 0, 0, 2, 0, 48, 107]},
		 {'word': '智慧城市', 'descriptions': ['一些国家推进新型智慧城市建设', '依托智慧城市推进治理升级', '知识产权保护助推智慧城市建设'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 22, 106]},
		 {'word': '从严治党', 'descriptions': ['从严治党 有腐必反', '全面从严治党是党永葆生机活力、走好新的赶考之路的必由之路', '从严治党看会风'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 54, 64, 22, 325]},
		 {'word': '产业扶贫', 'descriptions': ['产业扶贫别“编故事”', '怎样推进精准扶贫产业扶贫', '产业扶贫要放水养鱼'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 4, 6, 90]},
		 {'word': '自主创新', 'descriptions': ['树立自主创新发展的时代标杆', '自主创新产业支撑下的移动互联网时代', '中国二重：自主创新驱动企业'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 16, 844, 139]},
		 {'word': '中国力量', 'descriptions': ['为世界发展贡献中国力量', '为推动全球知识产权生态系统发展贡献中国力量', '为推进新型经济全球化贡献中国力量'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 54, 98]},
		 {'word': '党的领导', 'descriptions': ['坚持党的领导是宪法一以贯之的精神', '充分发挥党的领导核心作用', '坚持党的领导  才能发展繁荣西藏'], 'frequency': [8, 2, 66, 248, 152, 12, 66, 36, 106, 48, 111]},
		 {'word': '全面依法治国', 'descriptions': ['在全面依法治国中恪尽法律监督职责', '坚持党对全面依法治国的领导', '全面依法治国 推进国家治理现代化'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 84]},
		 {'word': '中国道路', 'descriptions': ['“中国道路”的三个有机统一', '增强学术自信 讲清中国道路', '中国道路的世界历史意义'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 8, 52, 97]},
		 {'word': '党的建设', 'descriptions': ['党的建设不断迈向科学化', '把党的建设新的伟大工程推向前进', '就《关于加强新时代离退休干部党的建设工作的意见》答记者问'], 'frequency': [2, 0, 4, 12, 58, 4, 22, 88, 418, 384, 143]},
		 {'word': '稳中求进', 'descriptions': ['我国经济步入稳中求进的新征程', '稳中求进，向世界传递信心', '把握稳中求进总基调促进经济平稳较快发展'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 34, 84, 122]},
		 {'word': '和谐共生', 'descriptions': ['为人与自然和谐共生的现代化提供有力科技支撑', '建设人与自然和谐共生的美丽家园', '站在人与自然和谐共生的高度谋划发展'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 4, 121]},
		 {'word': '数字化转型', 'descriptions': ['北京银行积极推进数字化转型', '科大讯飞助力数字化转型 为建设“数字中国”贡献力量', '浙江中小企业加快数字化转型'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 104]},
		 {'word': '习近平谈治国理政', 'descriptions': ['《习近平谈治国理政》第一卷僧伽罗文版分享交流会在斯里兰卡举行', '《习近平谈治国理政》韩文版首发式在首尔举行', '《习近平谈治国理政》秘鲁版首发式举行'], 'frequency': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 84]},
		 {'word': '农业现代化', 'descriptions': ['助力上合组织国家农业现代化', '给农业现代化插上科技的翅膀', '长治以园区推动农业现代化'], 'frequency': [0, 0, 0, 14, 0, 24, 74, 26, 88, 66, 99]},
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