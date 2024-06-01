# draft2

矢量与空间几何
二阶、三阶行列式
1. 二阶线性方程组 $x=\frac{D_x}{D},y=\frac{D_y}{D}$
（$D_x$）为方程组右端常数项取代D中的x列系数位置
三阶同理可得

相关
1. 对角线法则
2. 余子式、代数余子式 --- 按行展开、按列展开
3. 行列式等于 任一行(或列)的各元素与对应代数余子式乘积之和


矢量
1. 方向角、方向余弦与单位矢量的关系
2. 数量积(点积、内积)
    1. $a·b=|a||b|\cos{(a,b)}$
        1. 余弦定理: $c^2=a^2+b^2-2ab\cos{(a,b)}$
        2. $\cos{(a,b)}=\frac{a·b}{|a||b|}=\frac{a^2+b^2-c^2}{2ab}$
    2. 垂直为0
    3. 点乘单位矢量为在该方向的投影
    4. 数量积等于对应矢量坐标的乘积之和
3. 矢量积(叉乘、外积)
    1. 性质: 若$c=a\times b$
        1. c的方向：垂直于矢量a, b；其方向为右手定则(四指从 a 弯曲经过角(a, b)到 b，大拇指方向 )
        2. c的大小：$|c|=|a\times b|=|a||b|\sin{(a,b)}$
        3. 几何意义：其大小为两矢量所围成平行四边形的面积
        4. 平行为0  且两矢量平行满足 $a//b\leftrightarrows \frac{a_1}{b_1}=\frac{a_2}{b_2}=\frac{a_3}{b_3}$
        5. 计算方法：矢量(i, j, k)与 a, b 构成的行列式按第一行展开的结果, 展开项i、j、k对应x、y、z坐标
        6. 口诀：计算对应坐标、去掉对应坐标系数列的二阶行列式，y列乘以负一
4. 混合积
1. 计算方法：$a·(b\times c)=a_1\left|\begin{array}{cccc}b_2&b_3\\c_2&c_3\end{array}\right|-a_2\left|\begin{array}{cccc}b_1&b_3\\c_1&c_3\end{array}\right|+a_3\left|\begin{array}{cccc}b_1&b_2\\c_1&c_2\end{array}\right|=\left|\begin{array}{cccc}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{array}\right|$
2. 意义：当混合积为零时，共面 $a·(b\times c)=0$





平面与直线方程
1. 平面方程(点法式、一般式)
条件：任一点和法向量
一平面过点$P_0(x_0,y_0,z_0)$, 法向量为$n=Ai+Bj+Ck$, 
    1. 点法式： 平面方程为$A(x-x_0)+B(y-y_0)+C(z-z_0)=0$
    2. 一般式：$Ax+By+Cz+D=0,\ D=-(Ax_0+By_0+Cz_0)$
        1. D=0, 平面过原点；
        2. C=0, 平面平行Oz轴，因为法矢量n=Ai+Bj, n · k=0, A、B同理
        3. B=0, C=0, 平行于Oyz平面，截距为$-\frac{D}{A}$
        4. 截距式方程：$\frac{x}{-\frac{D}{A}}+\frac{y}{-\frac{D}{B}}+\frac{z}{-\frac{D}{C}}=1$, 分子为对应轴的截距
2. 平面关系、点面距离
条件：二平面的法向量
    1. 平面夹角
    设有两平面：
    $平面\pi_1: A_1x+B_1y+C_1z+D_1=0,\ 法矢量:n_1=A_1i+B_1j+C_1k;$
    $平面\pi_2: A_2x+B_2y+C_2z+D_2=0,\ 法矢量:n_2=A_2i+B_2j+C_2k;$
        1. 两平面夹角余弦：$\cos\theta=\cos{(n_1,n_2)}=\frac{n_1·n_2}{|n_1||n_2|}$
        =$\frac{A_1A_2+B_1B_2+C_1C_2}{\sqrt{A_1^2+B_1^2+C_1^2}\sqrt{A_2^2+B_2^2+C_2^2}}$
        1. 平面垂直：$n_1\perp n_2，即n_1·n_2=0$
        2. 平面平行：$n_1\ //\ n_2，n_1\times n_2=0即\frac{A_1}{A_2}=\frac{B_1}{B_2}=\frac{C_1}{C_2}$
    2. 点面距离
    条件：平面方程 和 点坐标
    平面上一点$P_0(x_0,y_0,z_0)到平面Ax+By+Cz+D=0$的距离
    距离公式：$d=\frac{|Ax_0+By_0+Cz_0+D|}{\sqrt{A^2+B^2+C^2}}$
    
3. 空间直线方程(点向式或对称式或标准式、一般式、参数式)
    1. 点向式
    条件：任一点 和 一方向矢量：$\nu=li+mj+nk$   方向数：l, m, n
    方程：$\frac{x-x_0}{l}=\frac{y-y_0}{m}=\frac{z-z_0}{n}=t$(若l为0，则直线垂直于Ox轴, 此时 $x=x_0$)
    2. 参数式
    条件：同上
    方程：$\begin{cases}x=x_0+lt,\\y=y_0+mt,&(-\infty<t<+\infty)，\\z=z_0+nt\end{cases}$
    3. 两点式
    条件：任意两点
    方程：$\frac{x-x_0}{x_1-x_0}=\frac{y-y_0}{y_1-y_0}=\frac{z-z_0}{z_1-z_0}$
    4. 一般式  (平面交线)
    条件：两平面方程
    方程：$\begin{cases}A_1x+B_1y+C_1z+D_1=0,\\A_2x+B_2y+C_2z+D_2=0\end{cases}$(其中$A_1,B_1,C_1与A_2,B_2,C_2$不成比例。即两平面不平行)
    用法：根据两平面方程的法向量，求出方向矢量: $\nu=n_1\times n_2$, 令任一x,y,z为0，求出任一点，可化为点向式或参数式
    
4. 线线平行、垂直条件，线面关系
    1. 直线夹角
    条件：两直线方程$L_1:\frac{x-x_1}{l_1}=\frac{y-y_1}{m_1}=\frac{z-z_1}{n_1},L2:..$ 或 两直线的法矢量$\nu_1,\nu_2=li+mj+nk$
    夹角余弦：$\cos\theta=\cos{(\nu_1,\nu_2)}=\frac{\nu_1·\nu_2}{|\nu_1||\nu_2|}$
        =$\frac{l_1l_2+m_1m_2+n_1n_2}{\sqrt{l_1^2+m_1^2+n_1^2}\sqrt{l_2^2+m_2^2+n_2^2}}$
    2. 线面夹角
    条件：线的方向矢量v 和 面的法矢量n
        1. v与n的夹角$\theta,线面夹角为\frac{\pi}{2}-\theta或\theta-\frac{\pi}{2}$
        2. 线面垂直: v // n ，向量比例相等；
        3. 线面平行: $v\perp n，即有v\times n=0$
    3. 点线距离
    条件：点坐标$P(x_0,y_0,z_0)，线方程L:\frac{x-x_0}{l}=\frac{y-y_0}{m}=\frac{z-z_0}{n},方向矢量为\nu=li+mj+nk$
    计算方法：几何面积法 —— 方向矢量与 点到直线上任意一点叉乘，得到面积，比上方向矢量的模得到高(距离)
    公式：在L上任取一点$P_1(x_1,y_1,z_1),设u=\overrightarrow{P_0P},则距离h=\frac{|u\times \nu|}{|\nu|}$
    4. 线线距离（异面）
    条件：两异面直线方程L1, L2, 对应方向矢量：v1, v2
    找点：$在L_1，L_2上分别任取一点M_1，M_2,设u=\overrightarrow{M_1M_2}$
    公式：$d=\frac{|u·(\nu_1\times\nu_2)|}{|\nu_1\times\nu_2|}$
    
    
    

二次曲面
球面、柱面、旋转抛物面、圆锥面、椭球面，方程及其图形
球面
定义：$动点M(x,y,z)距离一定点M_0(x_0,y_0,z_0)$的距离等于正数R, 该动点轨迹即为球心为$M_0$半径为R的球面
方程：由距离公式得$(x-x_0)^2+(y-y_0)^2+(z-z_0)^2=R^2$


柱面
定义：一动直线L沿一曲线$\Gamma移动形成曲面，直线L为母线，曲线\Gamma为准线$
条件：$准线方程F(x,y)=0（此时准线在Oxy轴上）,  母线L的方向矢量：v=ai+bj+ck (设c\neq 0)$
计算过程：$设曲面上任一一点M(x,y,z), 过该点的母线交准线于点M_1(x_1,y_1,0), 构造矢量\overrightarrow{M_1M}//v，即\overrightarrow{M_1M}=mv$，联立消去m
方程：计算得到$x_1=x-\frac{a}{c}z,y_1=y-\frac{b}{c}z, 将其带入准线方程\Gamma F(x,y)，柱面方程为F(x-\frac{a}{c}z,y-\frac{b}{c}z)=0$
其他情况：例如，准线为Oxy上的圆$x^2+y^2=a^2,当方向矢量分别为v_1=j+k，v_2=k, 分别对应x_1=x,y_1=y-z(斜柱面);x_1=x,y_1=y(直柱面)$; 若方程F(x, y)表示一张柱面，其母线平行于z轴

锥面
定义：$过O点的动直线L，沿空间曲线\Gamma(不过点O)移动生成的曲面，L为母线，\Gamma为准线,点O为该曲面的顶点$
条件：$准线：z=h上的平面曲线\Gamma:F(x,y)=0，顶点：原点$
计算过程： $设锥面上任一点M(x,y,z), 过M点的母线交准线于点M_1(x_1,y_1,h), 构造矢量\overrightarrow{OM_1}//\overrightarrow{OM}，即\overrightarrow{OM_1}=m\overrightarrow{OM}$，联立消去m，得
方程：计算可得$x_1=\frac{h}{z}x,y_1=\frac{h}{z}y，带入准线方程可得锥面方程F(\frac{h}{z}x,\frac{h}{z}y)=0（h为准线高度，z为等价x，y的变量）$

旋转曲面
定义：一曲线$\Gamma$绕一定制线L旋转生成的曲面。L为旋转曲面的轴。(下面给出绕坐标轴的曲面方程)
计算：例如在Oxy上，曲线表达式：f(x,y)=0，绕z轴旋转曲面可视为，y保持不变，|x|为旋转半径，即替换$x为x=\pm\sqrt{x^2+z^2}$，其它轴同理.
方程：$f(\pm\sqrt{x^2+z^2},y)=0$

椭球面
方程：$\frac{x^2}{a^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}=1（a>0,\ b>0,\ c>0）$
可知：$\frac{x^2}{a^2}\leq 1，\frac{y^2}{b^2}\leq 1，\frac{z^2}{c^2}\leq1$
即：$|x|\leq a,|y|\leq b,|z|\leq c，即a,b,c分别对应于x,y,z轴上的半轴长$
特殊情况：当a=b时，$\frac{x^2}{b^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}=1$, 可视为Oyz上的平面曲线$\frac{y^2}{b^2}+\frac{z^2}{c^2}=1$绕Oz轴旋转而成的曲面。

相关：
旋转曲面：轴平面上的曲线(即曲线在Oxy、Oxz、Oyz平面上)绕某一轴旋转。
例如在Oxy上，曲线表达式：f(x,y)=0，绕z轴旋转曲面可视为，y保持不变，x为旋转半径，即替换$x为x=\pm\sqrt{x^2+z^2}$

椭圆抛物面
方程：$z=\frac{x^2}{a^2}+\frac{y^2}{b^2}\ (a>0,b>0)$
即: $\begin{cases}\frac{x^2}{a^2h}+\frac{y^2}{b^2h}=0,\\z=h.\end{cases}$
几何图像：由方程可知z>0, 且随着z的增加，位于z点、平行于Oxy的平面对应的椭圆的两个半轴随之增大。
特殊情况：当a=b时，可视为抛物面$z=\frac{y^2}{a^2}$沿Oz轴旋转所得的旋转抛物面，$y^2=x^2+y^2带入方程，即得z=\frac{x^2+y^2}{a^2}$

相关：
二次锥面
双曲抛物面(马鞍面)
单叶曲面
双叶曲面



多元微积分
偏导、全微分、复合偏导、隐函数偏导、极值
偏导
定义：多元函数z=f(x,y)在某一点$P_0(x_0,y_0)$关于x的增量的变化率，称为关于x的偏导数
表示方式： $f_x'(x_0,y_0)=\frac{d}{dx}f(x,y_0)|_{x=x_0}=\frac{\partial{z}}{\partial x}|_{y=y_0}^{x=x_0}=f_x'(x,y_0)|_{x=x_0}$
/ $=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}$
几何意义：$曲面f(x,y)与y=y_0平面的交线在点P_0处的点的切线(关于Ox轴)的斜率$
表达式： $\lim_{\triangle x\to0}{\frac{f(x_0+\triangle x,y_0)-f(x_0,y_0)}{\triangle x}}=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}$
三种计算方法： 求偏导后带入、部分带入、定义法
$f_x'(x,y)|_{y=y_0}^{x=x_0}=\frac{\partial{z}}{\partial x}|_{y=y_0}^{x=x_0}=f_x'(x,y_0)|_{x=x_0}=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}$

高阶偏导
表达：$\frac{\partial^2{z}}{\partial{x^2}},\frac{\partial^2 z}{\partial x\partial y},f_{xx}''(x,y),f_{xy}''(x,y),f_{11}''(x,y),f_{12}''(x,y)$
性质：混合偏导与顺序无关, 即$f_{xy}''(x,y)=f_{yx}''(x,y)$


全微分
定义：二元函数z=f(x,y)在点(x,y)处的全增量$\triangle z=f(x+\triangle x,y+\triangle y)-f(x,y)=A\triangle x+B\triangle y+o(\rho)(\rho=\sqrt{(\triangle x)^2+(\triangle y)^2}\to0)$
表达式：$(dz为\triangle x,y均趋于0时，\triangle z的极限)dz=A\triangle (d)x+B\triangle (d)y(A=\frac{\partial z}{\partial x},B=\frac{\partial z}{\partial y})$
性质：
1. 必要：可微则连续、偏导均存在 
2. 充分：偏导均存在、且均连续(连续偏导)，则可微  
3. 不可微：1. 在该点处不连续 2. 有偏导不存在 3. 偏导存在，极限$\lim_{\triangle x\to0,\triangle y\to0}{\frac{2\triangle x\triangle y}{(\triangle x)^2+(\triangle y)^2}}$不存在或不为0.

复合函数
全导数(链导法则)：有几个相关中间变量，则为对应的中间变量偏导相加
例如：z(u,v,w)为u,v,w的函数，u,v,w是x的相关函数。
则z关于x的偏导$\frac{\partial z}{\partial x}=\frac{\partial z}{\partial u}\frac{\partial u}{\partial x}+\frac{\partial z}{\partial v}·\frac{\partial v}{\partial x}+\frac{\partial z}{\partial w}·\frac{\partial w}{\partial x}$
化简写法：$\frac{\partial z}{\partial x}=f_1'u'+f_2'v'+f_3'w' (类似的f_{12}''=f_{21}'')$
注：该函数的二阶偏导有三个对应的中间变量$=f_{11}''(x)+f_{12}''(x)+f_{13}''(x)+f_{21}''(x)+...$


全微分
若有 z=f(x,y), x=x(s,t), y=y(s,t) 都具有连续偏导,
则$dz=\frac{\partial z}{\partial x}dx+\frac{\partial z}{\partial y}dy$
=$\frac{\partial z}{\partial x}(\frac{\partial x}{\partial s}ds+\frac{\partial x}{\partial t}dt)+\frac{\partial z}{\partial y}(\frac{\partial y}{\partial s}ds+\frac{\partial y}{\partial t}dt)$
=$(\frac{\partial z}{\partial x}\frac{\partial x}{\partial s}+\frac{\partial z}{\partial y}\frac{\partial y}{\partial s})ds+(\frac{\partial z}{\partial x}\frac{\partial x}{\partial t}+\frac{\partial z}{\partial y}\frac{\partial y}{\partial t})dt$
=$\frac{\partial z}{\partial s}ds+\frac{\partial z}{\partial t}dt$
此为一阶微分形式不变性，多元函数全微分同一元函数一样，高阶不具有不变性


隐函数的偏导
函数形式：$f(x,u(x,y),z(x,y))=0$
解法：对两边同时求偏导、或求微分
注：求微分后, 将无关增量如dz取零，即可得到$\frac{dx}{dy}=\frac{\partial x}{\partial y}$



多元函数极值(多元泰勒公式 待学)
性质：(设极值点$P(x_0,y_0)$)
1. 必要：若在极值点存在偏导，则偏导均为0. (该点也称为驻点或稳定点)
2. 充分：前提：若在P点邻域内，连续且有二阶偏导，$f_x'(x_0,y_0)=f_y'(x_0,y_0)=0,设A=f_{xx}''(x_0,y_0),B=f_{xy}''(x_0,y_0),C=f_{yy}''(x_0,y_0)$
    (1) $B^2-AC<0,f(x_0,y_0)$一定为极值，A(或C)>0时，为极小值，A(或C)<0时，为极大值;
    (2) $B^2-AC>0,f(x_0,y_0)$不为极值;
    (2) $B^2-AC=0,$无法判断，需要进一步研究
极值怀疑点： 驻点、偏导数不存在点、边界点
技巧：若问题中一定有最大值(或最小值)，内部有唯一的怀疑点，则该函数值无需判断，必为最值

条件极值
极值求法(消元法、拉格朗日乘数法)
消元法：三元函数消成二元函数，分别求偏导=0，求出驻点或偏导不存在点。
拉格朗日乘数法：
1. 条件：$\psi$=G(x,y,z)=0  目标函数：u=f(x,y,z)
2. 引进拉格朗日函数$L(x,y,z,\lambda)=u+\lambda \psi$
(若有多个约束条件则：$L(x,y,z,\lambda_1,\lambda_2,..)=u+\lambda_1\psi_1+\lambda_2\psi_2+..;其中\lambda_1,\lambda_2..称为拉格朗日乘数$)
3. 分别对x,y,z,$\lambda$求偏导=0，构造四个函数，求出四个未知数(若能在不求出$\lambda$的情况下求解，则最好)
4. 求出的解为最值怀疑点，若有多个怀疑点，还需进一步判断



二重积分性质、计算、应用
概念：面积乘以高，计算曲顶柱体的体积
1. 分割面积区域   dxdy
2. 近似点域，乘以对应趋于对应的高  f(x,y)
3. 在趋于范围内求和   $\Sigma f(x,y)dxdy$
4. 求分割面积趋于0的极限
性质：1. 线性变换与定积分相同
2. （被积函数大等于时，积分函数大于）若$f(x,y)\geq g(x,y),f(x,y)\not\equiv g(x,y),则\iint_\sigma{f(x,y)d\sigma}>\iint_\sigma{g(x,y)d\sigma}$（二重积分和定积分等同，是一个累加的过程）
3. 中值定理：f(x,y)在有界闭区域$\sigma上连续，则在\sigma上至少存在一点P(x^*,y^*),$
使得$\iint_\sigma{f(x,y)d\sigma}=f(x^*,y^*)d\sigma；(f(x^*,y^*)区域内某一高度)$
几何意义：二重积分$\iint_\sigma{f(x,y)d\sigma}所求的曲顶柱体体积，等于以f(x^*,y^*)d\sigma为高，\sigma为底的柱体体积$


二重积分的计算(直角坐标系、极坐标)
(注意：积分是求和的过程)
直角坐标系计算二重积分：
计算过程：$\Sigma(长 \times \Sigma(宽 \times 高))$
因此，条件为：1. 长、宽、高的表达式；2. 两次求和范围(长、宽)；
例：表达式：长为x，宽为y，高为f(x,y)，$y_1=\phi_1(x),y_2=\phi_2(x)；求和范围：x\in[a,b],y\in[\phi_1(x),\phi_2(x)]$
则二重积分表达式为：$\iint_\sigma{f(x,y)d\sigma}=\int_a^b{dx(长增量)\int_{\phi_1(x)}^{\phi_2(x)}f(x,y)(高)dy(宽增量)}$
也可写成: $\iint_\sigma{f(x,y)(高)d\sigma(面积增量)}=\iint_\sigma{f(x,y)(高)dx(长/宽)dy(宽/长)}$； 其位置可以任意调换(对应x-型，y-型), 积不出来或计算复杂时，可尝试调换顺序


极坐标计算二重积分
计算过程：划分面积$\triangle \sigma=\frac{\triangle\theta}{2}(r+\triangle r)^2-\frac{\triangle\theta}{2}r^2=r\triangle \theta\triangle r+\frac{\triangle \theta}{2}(\triangle \theta)^2\approx r\triangle \theta\triangle r=d\sigma$
因为$x=r\cos{\theta},y=r\sin{\theta},所以高f(x,y)=f(r\cos{\theta},r\sin{\theta})$
得$\iint_\sigma{f(x,y)d\sigma}=\iint_\sigma{f(r\cos{\theta},r\sin{\theta})rdrd\theta}$

计算过程：$\Sigma(角度增量\times \Sigma(长度\times长度增量 \times 高))$
因此，条件为：1. 角度、长度、高的表达式；2. 两次求和范围(角度、半径)；
例：表达式：角度为$\theta，长度为r，高为f(r\cos{\theta},r\sin{\theta})，r_1=\phi_1(\theta),r_2=\phi_2(\theta)；求和范围：\theta\in[a,b],r\in[\phi_1(\theta),\phi_2(\theta)]$
则二重积分表达式为：$\iint_\sigma{f(r\cos{\theta},r\sin{\theta})d\sigma}=\int_a^b{d\theta(角度)\int_{\phi_1(\theta)}^{\phi_2(\theta)}f(r\cos{\theta},r\sin{\theta})(高)rdr(长度)}$
也可写成: $\iint_\sigma{f(r\cos{\theta},r\sin{\theta})(高)d\sigma(增量面积)}=\iint_\sigma{f(r\cos{\theta},r\sin{\theta})(高)r(长度)d\theta(角度增量)dr(长度增量)}$； 其位置可以任意调换(对应$\theta$-型，r-型--比较少见), 积不出来或计算复杂时，可尝试调换顺序


第一类曲线积分
定义：已知曲线线密度，求曲线质量
即:  $M=\Sigma\rho(线密度) ds(曲线弧长)$
方程：$\int_\gamma{f(x(t),y(t),z(t))ds}；其中\gamma为曲线函数$
曲线：$\gamma=\begin{cases}x=x(t)\\y=y(t)\\z=z(t)\end{cases};t\in(\alpha,\beta)\ \ ds=\sqrt{x'^2+y'^2+z'^2}dt;$
则方程表达式为：$\int_\alpha^\beta{f(x(t),y(t),z(t)\sqrt{x'^2+y'^2+z'^2}dt;\ t\in(\alpha,\beta)}；$
