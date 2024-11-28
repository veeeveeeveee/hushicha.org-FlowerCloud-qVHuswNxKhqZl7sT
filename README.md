
# 一.matcap材质


这个材质不会受到光照影响，但是如果图片本身有光就可以一直渲染这个图片本来的样子，用来将一个图片纹理渲染到物体上的材质


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203036600.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203036600.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112120314790.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112120314790.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203130183.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203130183.png)


代码实现


加载模型后，开启纹理渲染，并把它的材质变为这个材质，并且贴上纹理图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203303922.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203303922.png)


# 二.Lambert材质


Lambert网格材质是Three.js中最基本和常用的材质之一。本文将详细介绍Lambert网格材质的定义、特点、应用以及使用方法。


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203350029.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121203350029.png)


简单来说就是这个材质当你设置好各种贴图之后 实现凹凸不平地面等是比较好的


设置好Lambert材质后，打一个光进来，会发现是漫反射哑光的反射类似于


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121204636638.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121204636638.png)


# 三.phong材质


PHONG材质是Three.js中常用的一种材质，它是一种基于Phong光照模型的材质，可以用于实现高光和阴影效果。Phong光照模型是一种基于漫反射、镜面反射和环境反射的光照模型，可以用于模拟真实物体的光照效果。


比如涂了漆面的木材，光滑的材质


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121205608593.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121205608593.png)


设置为phone材质，在设置高光颜色就可以形成对点光源的反射


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121205751928.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121205751928.png)


设置好环境贴图后


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112120583105.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112120583105.png)


代码操作


创建光源，把一个平面设置成phone材质


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210053452.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210053452.png)


添加环境贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210317472.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210317472.png)


光滑的反射就出来了


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF.gif)


## 1\.实现玻璃水晶效果


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210637829.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121210637829.png)


加载模型，设置环境光，把这个模型改为phone材质，并且设置两个折射率


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211041274.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211041274.png)


envmap是环境贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211105343.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211105343.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211116253.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211116253.png)


如果想要折射效果还需要把环境贴图改为折射球形，上下不一样注意


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211244469.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211244469.png)


当把上面的反射变为折射后，这里的反射率也变为了折射率


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211339694.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121211339694.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17321948436222.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17321948436222.gif)


# 四.基础材质详解


## 1\.标准网格材质


在 Three.js 中，MeshBasicMaterial 是一个用于创建基本材质的类。它能够让您快速创建不需要光照效果的几何体，并且配置非常简单，可以使用颜色、透明度和纹理等属性来自定义材质。MeshBasicMaterial 在 Three.js 中非常重要，因为它是创建简单3D图形的常用材质之一，而且渲染速度很快，能够让您的应用程序保持流畅的交互体验。如果您想要创建更复杂的3D图形，了解 MeshBasicMaterial 是非常有用的，因为它是其他更复杂材质的基础。


注意：标准网格材质需要设定环境贴图


这里做一个记录，系统性的介绍一下各种贴图的作用，在之前的材质也有各种贴图，但是标准是最齐全的能够达到漫反射也能镜反射


加载一个剑的模型


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121212931300.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121212931300.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121212959222.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121212959222.png)


先上环境贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213022720.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213022720.png)


粗糙度为1，漫反射


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213104366.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213104366.png)


粗糙度为0，镜反射


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213122418.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213122418.png)


金属度为0


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213134760.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213134760.png)


金属度为1


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213145115.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213145115.png)


还原默认，先贴上贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213227685.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213227685.png)


金属度贴图和金属度是一个相乘的关系，越大就越金属


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112121332269.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112121332269.png)法线贴图实现凹凸不平的效果


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213350159.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213350159.png)


凹凸贴图同理，两个只能设置一个


置换贴图可以让顶点有一个起伏的效果，上面是看起来，这个是真起来


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213508952.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213508952.png)


粗糙度贴图可以让其光滑


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213603671.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213603671.png)


注意：真实环境只需要导入进来就是这个样子，不需要一个一个贴图，只是有时候改可以了解


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213659463.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121213659463.png)


代码实现


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121214628508.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121214628508.png)


创建环境贴图，背景一定要添加


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121220437668.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241121220437668.png)


## 2\.物理网格材质


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-202411212116590.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-202411212116590.png)


物理材质就是能够在刚才标准材质的基础上新增更多的功能


**透光率**


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204625828.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204625828.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204733564.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204733564.png)


当粗糙度为0，很光滑的时候就完全透明了


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204804798.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204804798.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112220481002.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112220481002.png)**厚度**


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204820807.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204820807.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204844113.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204844113.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204905093.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204905093.png)


**折射率，反射率**


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204934596.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122204934596.png)


**衰减颜色，距离**


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205004480.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205004480.png)


衰减距离越小，就越快到达衰减颜色


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205157040.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205157040.png)


偏红色


注意：衰减颜色最好都设置1以下不要整的


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205222422.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205222422.png)


**厚度贴图**


呈现一个不均匀的厚度


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205424614.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205424614.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205451174.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205451174.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF.gif)


**清漆效果与清漆透明度**


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205759196.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205759196.png)


单纯设置一个清漆强度为1后


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322803502753.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322803502753.gif)


清漆光滑度，1漫反射，0镜反射


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205955389.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122205955389.png)


map就是通过纹理决定哪些地方要清漆哪些地方不要


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211724856.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211724856.png)


中间光滑，周围不清漆


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211758974.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211758974.png)


注意此时应该粗糙度为1，到时候纹理会乘以粗糙度，如果为0始终 都是光滑


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211904061.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211904061.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221191452.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221191452.png)


法线贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211946090.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122211946090.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212038525.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212038525.png):[豆荚加速器官网PodHub](https://doujiaa.com)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212051464.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212051464.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212020950.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212020950.png)


## 3\. 布料织物材料光泽效果


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212504250.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122212504250.png)


创建一个物理材质球体


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221310557.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221310557.png)


设置光泽及颜色后


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213125629.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213125629.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213133129.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213133129.png)


光泽粗糙程度


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221315201.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221315201.png)


设置纹理贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213308545.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213308545.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213313943.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213313943.png)


## 4\.肥皂泡、油滴、蝴蝶翅膀等薄膜的虹彩效应


反射出各种颜色的材质


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213453225.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122213453225.png)


这种效果实际是有两层组成，外面一层负责反射折射


创建一个基本球体，有粗糙度，透明度，还有一层厚度


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214131627.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214131627.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214150959.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214150959.png)


设置彩虹色，反射率和彩虹色折射率


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214426056.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214426056.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322831071195.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322831071195.gif)


薄膜厚度范围


默认


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214542012.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214542012.png)


设置薄膜厚度贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214626750.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122214626750.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221461734.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-2024112221461734.png)


## 5\.清除物体\_几何体\_材质\_纹理保证性能和内存不泄漏


比如这里不断创建一个随机材质，随机几何体的物体，不断回调自身


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122215953044.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122215953044.png)


此时cpu使用率和内存大小都在不断增加，到一定程度就会网页崩溃


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322840509849-173228405129611.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-17322840509849-173228405129611.gif)


要优化这种情况就是


每一帧渲染完毕，render.render就是渲染的语句，就去清除掉物体几何体等


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122220154401.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122220154401.png)


## 6\.巧用物理发光属性打造逼真IPHONE产品


在很多建模软件直接导出来给到3D导入会发现有些属性发光等会缺失，这是因为两者有些内容并不兼用，所以这个时候通常是加载到three的编辑器里面，进行编辑之后，满意之后再导出到three里面进行模型加载


刚加载进来


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122221251880.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122221251880.png)


找到屏幕材质，设置好之后导出


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122222931053.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122222931053.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122222937759.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122222937759.png)


加载进来就行了


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223013122.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223013122.png)


## 7\.修改模型光泽效果打造逼真室内场景


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223145966.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223145966.png)


刚导入进来


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223537547.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223537547.png)


设置光泽光泽颜色


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223739589.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122223739589.png)


毛绒效果，法线贴图


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122224209173.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122224209173.png)


控制角度


如果让用户随意去转动很容易穿帮


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122224856196.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122224856196.png)


首先设置起始位置


可以添加轨道控制器来辅助查看


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225650253.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225650253.png)


设置相机初始位置，以及一开始看向的角度，x轴是横向看多宽，y是看多高，要设置lookat一开始看的角度还得配合控制器


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225756210.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225756210.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225836884.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225836884.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225823919.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225823919.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225912473.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225912473.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225928130.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122225928130.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230031381.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230031381.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-173228765973313.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-173228765973313.gif)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230117022.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230117022.png)


垂直的最小角度是网上旋转，最大角度是往下旋转


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230255085.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230255085.png)


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-173228777871015.gif)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/GIF-173228777871015.gif)


水平左右的角度


[![](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230404132.png)](https://raw.githubusercontent.com/HeymarJR/blog-pic/main/image-20241122230404132.png)


  * [一.matcap材质](#%E4%B8%80matcap%E6%9D%90%E8%B4%A8)
* [二.Lambert材质](#%E4%BA%8Clambert%E6%9D%90%E8%B4%A8)
* [三.phong材质](#%E4%B8%89phong%E6%9D%90%E8%B4%A8)
* [1\.实现玻璃水晶效果](#tid-nZSKKh)
* [四.基础材质详解](#%E5%9B%9B%E5%9F%BA%E7%A1%80%E6%9D%90%E8%B4%A8%E8%AF%A6%E8%A7%A3)
* [1\.标准网格材质](#tid-PwGjne)
* [2\.物理网格材质](#tid-aNmxGp)
* [3\. 布料织物材料光泽效果](#tid-Z3Aj35)
* [4\.肥皂泡、油滴、蝴蝶翅膀等薄膜的虹彩效应](#tid-AbD4G8)
* [5\.清除物体\_几何体\_材质\_纹理保证性能和内存不泄漏](#tid-RYD4wz)
* [6\.巧用物理发光属性打造逼真IPHONE产品](#tid-AChkri)
* [7\.修改模型光泽效果打造逼真室内场景](#tid-MFTSxB)

   \_\_EOF\_\_

   ![](https://github.com/heymar)Heymar  - **本文链接：** [https://github.com/heymar/p/18573314](https://github.com)
 - **关于博主：** 评论和私信会在第一时间回复。或者[直接私信](https://github.com)我。
 - **版权声明：** 本博客所有文章除特别声明外，均采用 [BY\-NC\-SA](https://github.com "BY-NC-SA") 许可协议。转载请注明出处！
 - **声援博主：** 如果您觉得文章对您有帮助，可以点击文章右下角**【[推荐](javascript:void(0);)】**一下。
     
