https://david-ta-ai.github.io/ChristmasTree/
# ChristmasTree
A Christams tree partcles creatyed by vibe coding on Gemini3

The promp are based on the following: 你是一名擅长 React（假定为 v19）、TypeScript 和 Three.js / React Three Fiber 的 3D 交互体验工程师兼艺术指导。 任务目标:实现一个高保真 3D Web 项目 ，生成的是一个html文件：「Your Signature Interactive Christmas Tree」。 整体气质要求： • 夸张奢华、金碧辉煌，但保持高级感； • 主色系为深祖母绿 + 高亮金属金； • 有电影感的辉光与光晕效果

一、核心交互与状态设计

1.	状态机（TreeMorphState）
•	至少包含两个主要状态：
•	SCATTERED：所有元素在空间中无序漂浮、散落；
•	TREE_SHAPE：所有元素收拢、聚合为一个圣诞树圆锥体。
•	需要支持在这两个状态之间平滑切换，带有过渡动画。
2.	双位置系统（Dual Position System）
•	每个元素（针叶粒子、装饰物实例）在初始化时就分配两套坐标：
•	scatterPosition：随机分布在一定半径的球体空间中；
•	treePosition：对应圣诞树圆锥体上预计算好的坐标。

二、树体与装饰系统

1.	针叶粒子层（Foliage Layer）
•	使用 THREE.Points + 自定义 ShaderMaterial 绘制大量粒子，形成树的“针叶”轮廓；
•	粒子需支持：轻微抖动/呼吸感、基于辉光的边缘高亮
•	粒子颜色以深绿为主，边缘叠加一点金色或暖白发光
2.	装饰物系统（Ornament System）
•	使用 InstancedMesh 优化渲染，每个物体的颜色是随机的：
•	重型元素：礼物盒（方形、体积大，金属反射），铃铛
•	轻型元素：彩球（圆形、金属反射），
•	极轻元素：小灯点、星星等。
•	不同类别赋予不同“受力权重”（例如在散落状态时飘动幅度不同）
•	树的最顶端有一个五角星

三、视觉与后期特效

1.	场景与相机
•	相机位置建议为 [0, 4, 20]，略微俯视圣诞树；
•	使用 HDRI 环境（如 典雅大厅   / Lobby 风格）提供环境反射与整体氛围光；
•	根据需要添加一两盏聚光灯，突出树体与顶部装饰。
2.	后期处理（Post-processing）
•	启用 Bloom 类辉光效果，营造柔和金色光晕：
•	阈值约 0.8 左右；
•	强度约 1.2 左右；
•	重点让金色装饰物和灯光有“高档金属 + 镀金”感觉，而不是廉价霓虹。

四、BGM

• 使用默认音乐链接或者上传音乐作为bgm • 在增加音乐可视化功能， 这个圣诞树上的粒子随着音乐旋律的变化，进行有节奏的变换颜色和抖动
• 音乐变化类似频谱环，始终位于树的地下，长度随因频频率伸缩，
