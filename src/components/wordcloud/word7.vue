<template>
	<div class="wordmain" style="overflow:hidden">
		     <el-container style="overflow:hidden">
		        <el-main class="wordcloudmain" style="overflow:hidden">
					<div class="words">
						<words @word-clicked="handleWordClicked" :msg="words2" :clickyear="7"></words>

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
		  description:  ['中国人民解放军军医代表团离京赴美访问', '朝鲜人民的强烈愤慨', '这还象人民铁路吗？'],
		  frequency:  [7268, 2052, 34316, 44764, 40404, 2770, 3698, 5688, 9080, 8688, 6245],
		  word:'人民',
		  index:6
	   },
      clickedWord: '',
	words2 :[
		{'text': '人民', 'size': 1977},{'text': '恢复', 'size': 779},{'text': '台湾', 'size': 748},{'text': '四化', 'size': 676},{'text': '责任制', 'size': 473},{'text': '苏军', 'size': 458},{'text': '邓小平', 'size': 440},{'text': '改革', 'size': 440},{'text': '石油', 'size': 424},{'text': '东盟', 'size': 418},{'text': '广州', 'size': 348},{'text': '西藏', 'size': 298},{'text': '奥运会', 'size': 240},{'text': '多种经营', 'size': 238},{'text': '开放', 'size': 222},{'text': '计划生育', 'size': 194},{'text': '因地制宜', 'size': 148},{'text': '实事求是', 'size': 148},{'text': '艰苦奋斗', 'size': 76},{'text': '增产节约', 'size': 76},{'text': '真理标准', 'size': 74},{'text': '从实际出发', 'size': 70},{'text': '国际市场', 'size': 62},{'text': '经济责任制', 'size': 58},{'text': '第三世界国家', 'size': 54},{'text': '学雷锋', 'size': 52},{'text': '南北对话', 'size': 52},{'text': '城市建设', 'size': 46},{'text': '农业机械化', 'size': 46},{'text': '知识青年', 'size': 46},{'text': '革命精神', 'size': 46},{'text': '总结经验', 'size': 46},{'text': '四个现代化', 'size': 44},{'text': '树新风', 'size': 42},{'text': '三中全会精神', 'size': 42},{'text': '大丰收', 'size': 42},{'text': '劳动致富', 'size': 42},{'text': '联合政府', 'size': 42},{'text': '回归祖国', 'size': 38},{'text': '卫星', 'size': 38},{'text': '国际奥委会', 'size': 38},{'text': '团结工会', 'size': 38},{'text': '海峡两岸', 'size': 38},{'text': '社会主义建设', 'size': 36},{'text': '责任田', 'size': 36}
		],
      wordData: [
		{'word': '人民', 'descriptions': ['中国人民解放军军医代表团离京赴美访问', '朝鲜人民的强烈愤慨', '这还象人民铁路吗？'], 'frequency': [7268, 2052, 34316, 44764, 40404, 2770, 3698, 5688, 9080, 8688, 6245]},
		{'word': '恢复', 'descriptions': ['塞浦路斯希土族恢复谈判', '福建恢复平价定量供应鲜鱼', '乌干达首都恢复正常秩序'], 'frequency': [750, 90, 1442, 1672, 900, 234, 832, 1150, 2576, 1546, 644]},
		{'word': '台湾', 'descriptions': ['里根说要发展同中国关系又不抛弃台湾“盟友”', '美政府不要在同台湾打交道时损害美中关系', '台湾人民反割台斗争'], 'frequency': [232, 34, 1516, 1480, 688, 126, 1112, 2356, 2422, 1744, 507]},
		{'word': '四化', 'descriptions': ['开创四化建设的新局面', '发展外贸  促进“四化”', '进行人口普查是经济调整和四化建设的需要'], 'frequency': [0, 0, 0, 22, 0, 48, 826, 478, 60, 24, 26]},
		{'word': '责任制', 'descriptions': ['责任制促进洛阳公社农业基建', '河南实行生产责任制加强麦田管理', '石固公社落实分配政策巩固生产责任制'], 'frequency': [0, 0, 196, 210, 6, 12, 638, 562, 330, 108, 54]},
		{'word': '苏军', 'descriptions': ['北约外长会议一致要求苏军全部撤出阿富汗', '美议员对美苏军力对比表示忧虑', '苏军在阿富汗陷入困境仍要长期赖着不走'], 'frequency': [96, 18, 346, 204, 36, 36, 524, 408, 92, 6, 1]},
		{'word': '邓小平', 'descriptions': ['邓小平副总理前往宾馆看望卡拉曼利斯总理并继续会谈', '邓小平副总理会见图普奥拉总理', '邓小平副总理会见法国科研国务秘书艾格兰一行'], 'frequency': [0, 4, 44, 672, 1282, 392, 442, 476, 1654, 466, 37]},
		{'word': '改革', 'descriptions': ['嵊县进行工业管理体制改革', '有利调整的改革看准了要下决心去做', '中学的干部结构要改革'], 'frequency': [628, 58, 1168, 1372, 486, 40, 578, 8260, 9298, 5802, 5097]},
		{'word': '石油', 'descriptions': ['尼日利亚石油工业的明珠', '中法合作勘探开发南海石油第一口探井开钻', '石油输出国组织援助许多发展中国家'], 'frequency': [14, 4, 616, 784, 1286, 226, 782, 1242, 2018, 828, 202]},
		{'word': '东盟', 'descriptions': ['东盟各国采取措施克服能源困难', '东盟反对法国恢复对越援助', '东盟国家不再相信越南的话'], 'frequency': [0, 0, 0, 0, 8, 110, 532, 426, 914, 1312, 757]},
		{'word': '广州', 'descriptions': ['我国从泰国接受的首批印支难民抵广州', '侯赛因总理抵广州参观访问', '广州远洋运输公司海员大力节约外汇'], 'frequency': [78, 126, 942, 2044, 1880, 248, 498, 1354, 1568, 1760, 823]},
		{'word': '西藏', 'descriptions': ['西藏人工栽培灵芝', '西藏民族解放的道路', '西藏交通系统重视发挥党员模范作用'], 'frequency': [24, 6, 1012, 1896, 584, 156, 440, 1078, 2632, 2156, 833]},
		{'word': '奥运会', 'descriptions': ['莫斯科奥运会失去了意义', '英首相要求英奥委会抵制莫斯科奥运会', '禁止台北使用原有旗、歌和会徽参加冬季奥运会'], 'frequency': [0, 0, 20, 38, 16, 0, 326, 670, 1274, 1660, 183]},
		{'word': '多种经营', 'descriptions': ['科技工作者对发展多种经营的建议', '起用专业行家  发展多种经营', '遵化县发展多样化小型的多种经营'], 'frequency': [0, 0, 52, 264, 130, 58, 240, 82, 110, 4, 2]},
		{'word': '开放', 'descriptions': ['刘少奇同志在延安的旧居重新开放', '我国对外开放的八座山峰简介', '希望西湖风景区延长开放时间'], 'frequency': [56, 8, 170, 172, 34, 50, 294, 1976, 3690, 2436, 2469]},
		{'word': '计划生育', 'descriptions': ['笑声中的计划生育课', '韩淑兰做两万九千例计划生育手术无事故', '计划生育是实现四化的一个战略任务'], 'frequency': [0, 0, 0, 10, 46, 24, 230, 398, 514, 120, 18]},
		{'word': '因地制宜', 'descriptions': ['因地制宜  分类指导', '因地制宜推广专业承包联产计酬责任制', '树种要因地制宜多样化'], 'frequency': [0, 2, 18, 400, 116, 46, 148, 66, 126, 94, 83]},
		{'word': '实事求是', 'descriptions': ['坚持实事求是的科学态度', '长山公社实事求是规定干部劳动天数', '五中全会各项决策实事求是合乎民意'], 'frequency': [8, 2, 26, 118, 44, 92, 150, 152, 206, 74, 41]},
		{'word': '艰苦奋斗', 'descriptions': ['“艰苦奋斗才能创造美好的未来”', '基建工程兵艰苦奋斗贡献大', '各级领导干部要带头艰苦奋斗'], 'frequency': [26, 2, 20, 198, 990, 22, 82, 106, 252, 102, 38]},
		{'word': '增产节约', 'descriptions': ['立足国内自力更生增产节约粮食', '帮助解决问题推动增产节约运动', '上海工交系统增产节约形势喜人'], 'frequency': [16, 2, 990, 666, 184, 16, 104, 74, 6, 0, 0]},
		{'word': '真理标准', 'descriptions': ['开展真理标准讨论很有必要大有好处', '继续开展经济理论领域真理标准问题讨论', '在真理标准讨论中弄清当前主要矛盾'], 'frequency': [0, 0, 0, 0, 0, 4, 78, 2, 22, 6, 2]},
		{'word': '从实际出发', 'descriptions': ['从实际出发把南平建设好', '要敢于从实际出发', '从实际出发帮助穷队趋利避害'], 'frequency': [8, 0, 10, 114, 20, 26, 72, 70, 44, 22, 17]},
		{'word': '国际市场', 'descriptions': ['生产优质铝材畅销国际市场', '我国钟表专用机床进入国际市场', '上海机床厂产品进入国际市场'], 'frequency': [2, 0, 0, 8, 10, 0, 68, 270, 502, 84, 29]},
		{'word': '经济责任制', 'descriptions': ['江津地区工交企业普遍推行经济责任制', '集中力量完善稳定经济责任制', '四川６０％工交企业推行各种经济责任制'], 'frequency': [0, 0, 0, 0, 0, 0, 58, 38, 4, 0, 0]},
		{'word': '第三世界国家', 'descriptions': ['中国坚决同第三世界国家站在一起', '加强同第三世界国家团结合作 反对霸权主义维护世界和平', '秘鲁副总统呼吁第三世界国家联合保卫贸易利益'], 'frequency': [0, 0, 0, 0, 476, 158, 56, 78, 24, 2, 0]},
		{'word': '学雷锋', 'descriptions': ['厦门驻军组织一百五十多个学雷锋小组', '学雷锋学英模争当雷锋式革命军人', '沈阳部队涌现两万多名学雷锋积极分子'], 'frequency': [0, 0, 0, 6, 22, 68, 68, 34, 468, 90, 105]},
		{'word': '南北对话', 'descriptions': ['西欧应在南北对话中发挥积极作用', '关于朝鲜南北对话', '谴责南朝鲜沿军事分界线构筑高墙  《劳动新闻》指出南朝鲜对南北对话缺乏诚意'], 'frequency': [0, 0, 0, 0, 12, 2, 52, 36, 42, 14, 1]},
		{'word': '城市建设', 'descriptions': ['河南省委帮助洛阳制定城市建设方针', '索非亚的城市建设', '在经济调整中加强城市建设'], 'frequency': [10, 0, 32, 56, 4, 4, 48, 66, 118, 130, 93]},
		{'word': '农业机械化', 'descriptions': ['联产责任制给农业机械化带来生机', '走自己发展农业机械化的道路', '美国的农业机械化'], 'frequency': [6, 2, 32, 120, 138, 128, 50, 24, 22, 32, 12]},
		{'word': '知识青年', 'descriptions': ['清河门镇公社组织知识青年创办奶牛场', '下乡知识青年郑启中制成测光仪', '中央电视大学扩大招收社会知识青年'], 'frequency': [18, 0, 16, 254, 1312, 44, 52, 8, 4, 2, 1]},
		{'word': '革命精神', 'descriptions': ['学习高云涛田继跃舍己救人革命精神', '爱国主义革命精神的继承和发扬', '振奋革命精神，在党中央领导下同心同德夺取四化更大胜利'], 'frequency': [2, 0, 20, 782, 952, 42, 48, 38, 20, 22, 32]},
		{'word': '总结经验', 'descriptions': ['总结经验要实事求是', '总结经验解放思想', '总结经验'], 'frequency': [28, 2, 52, 256, 438, 34, 70, 60, 82, 80, 14]},
		{'word': '四个现代化', 'descriptions': ['全力为四个现代化献计出力', '中国四个现代化目标没有改变', '我国首批赴美留学的访问学者离京方毅副总理勉励他们刻苦学习美国的先进科学技术，为实现四个现代化出力'], 'frequency': [0, 0, 0, 0, 10, 94, 44, 14, 0, 2, 0]},
		{'word': '树新风', 'descriptions': ['学先烈  树新风  红领巾增荣誉', '开展学雷锋树新风做好事活动', '讲文明  守纪律  树新风'], 'frequency': [0, 0, 0, 2, 10, 6, 46, 22, 138, 124, 27]},
		{'word': '三中全会精神', 'descriptions': ['坚定不移继续贯彻三中全会精神', '贯彻三中全会精神发展大好形势', '三中全会精神带来了文艺的繁荣'], 'frequency': [0, 0, 0, 10, 0, 2, 42, 8, 22, 40, 25]},
		{'word': '大丰收', 'descriptions': ['山东棉花获得大丰收', '芜湖县夏季粮油大丰收', '内蒙古牧业和油料、甜菜获得大丰收'], 'frequency': [6, 0, 60, 648, 218, 16, 52, 56, 104, 34, 7]},
		{'word': '劳动致富', 'descriptions': ['靠正当经营劳动致富的队和户越多越好', '继续鼓励农民劳动致富', '是非分明不走邪道  是农民渔民劳动致富榜样'], 'frequency': [2, 0, 0, 0, 0, 0, 42, 60, 4, 0, 1]},
		{'word': '联合政府', 'descriptions': ['苏哈托表示印尼支持民柬联合政府', '瑞典温和联合党退出联合政府', '祝贺民主柬埔寨联合政府成立'], 'frequency': [46, 2, 42, 336, 82, 0, 56, 170, 138, 94, 13]},
		{'word': '回归祖国', 'descriptions': ['祝愿台湾早日回归祖国', '班禅衷心希望达赖回归祖国', '台湾回归祖国是人心所向'], 'frequency': [0, 0, 0, 2, 0, 0, 40, 10, 148, 70, 48]},
		{'word': '卫星', 'descriptions': ['美‘柏伽索斯—二号’卫星将坠落', '卫星大队制订明年增产增收计划', '西方九国研制大型通信卫星'], 'frequency': [6, 0, 14, 844, 286, 36, 134, 722, 1270, 692, 380]},
		{'word': '国际奥委会', 'descriptions': ['我国同国际奥委会的关系', '中国奥委会举行酒会欢迎国际奥委会主席', '姬鹏飞会见国际奥委会执委西佩尔科'], 'frequency': [0, 0, 6, 70, 24, 4, 54, 120, 396, 158, 96]},
		{'word': '团结工会', 'descriptions': ['波党十一名负责人退出团结工会', '波团结工会拒绝政府成立常设联合委员会建议', '波兰政府和团结工会达成协议'], 'frequency': [0, 0, 0, 0, 0, 0, 76, 14, 16, 0, 0]},
		{'word': '海峡两岸', 'descriptions': ['康克清发表书面谈话衷心拥护叶委员长谈话  祖国统一符合海峡两岸妇女根本利益', '海峡两岸渔民骨肉情深', '海峡两岸亲人盼团圆'], 'frequency': [0, 0, 0, 4, 0, 0, 40, 236, 796, 428, 76]},
		{'word': '社会主义建设', 'descriptions': ['愿为祖国社会主义建设尽一分力', '全党全民总动员实现社会主义建设新转变', '社会主义建设与生活方式、价值观和人的成长'], 'frequency': [6, 0, 216, 648, 514, 54, 38, 62, 56, 24, 21]},
		{'word': '责任田', 'descriptions': ['海龙县民兵帮助烈军属种好责任田', '及时制止社员在责任田上建房', '正确处理工作与种责任田的关系'], 'frequency': [0, 0, 0, 0, 0, 0, 36, 40, 12, 18, 19]},
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