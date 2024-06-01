
二次曲面
球面、柱面、旋转抛物面、圆锥面、椭球面，方程及其图形
球面
定义：\(动点M(x,y,z)距离一定点M_0(x_0,y_0,z_0)\)的距离等于正数R, 该动点轨迹即为球心为\(M_0\)半径为R的球面
方程：由距离公式得\((x-x_0)^2+(y-y_0)^2+(z-z_0)^2=R^2\)


柱面
定义：一动直线L沿一曲线\(\Gamma移动形成曲面，直线L为母线，曲线\Gamma为准线\)
条件：\(准线方程F(x,y)=0（此时准线在Oxy轴上）,  母线L的方向矢量：v=ai+bj+ck (设c\neq 0)\)
计算过程：\(设曲面上任一一点M(x,y,z), 过该点的母线交准线于点M_1(x_1,y_1,0), 构造矢量\overrightarrow{M_1M}//v，即\overrightarrow{M_1M}=mv\)，联立消去m
方程：计算得到\(x_1=x-\frac{a}{c}z,y_1=y-\frac{b}{c}z, 将其带入准线方程\Gamma F(x,y)，柱面方程为F(x-\frac{a}{c}z,y-\frac{b}{c}z)=0\)
其他情况：例如，准线为Oxy上的圆\(x^2+y^2=a^2,当方向矢量分别为v_1=j+k，v_2=k, 分别对应x_1=x,y_1=y-z(斜柱面);x_1=x,y_1=y(直柱面)\); 若方程F(x, y)表示一张柱面，其母线平行于z轴

锥面
定义：\(过O点的动直线L，沿空间曲线\Gamma(不过点O)移动生成的曲面，L为母线，\Gamma为准线,点O为该曲面的顶点\)
条件：\(准线：z=h上的平面曲线\Gamma:F(x,y)=0，顶点：原点\)
计算过程： \(设锥面上任一点M(x,y,z), 过M点的母线交准线于点M_1(x_1,y_1,h), 构造矢量\overrightarrow{OM_1}//\overrightarrow{OM}，即\overrightarrow{OM_1}=m\overrightarrow{OM}\)，联立消去m，得
方程：计算可得\(x_1=\frac{h}{z}x,y_1=\frac{h}{z}y，带入准线方程可得锥面方程F(\frac{h}{z}x,\frac{h}{z}y)=0（h为准线高度，z为等价x，y的变量）\)

旋转曲面
定义：一曲线\(\Gamma\)绕一定制线L旋转生成的曲面。L为旋转曲面的轴。(下面给出绕坐标轴的曲面方程)
计算：例如在Oxy上，曲线表达式：f(x,y)=0，绕z轴旋转曲面可视为，y保持不变，|x|为旋转半径，即替换\(x为x=\pm\sqrt{x^2+z^2}\)，其它轴同理.
方程：\(f(\pm\sqrt{x^2+z^2},y)=0\)

椭球面
方程：\(\frac{x^2}{a^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}=1（a>0,\ b>0,\ c>0）\)
可知：\(\frac{x^2}{a^2}\leq 1，\frac{y^2}{b^2}\leq 1，\frac{z^2}{c^2}\leq1\)
即：\(|x|\leq a,|y|\leq b,|z|\leq c，即a,b,c分别对应于x,y,z轴上的半轴长\)
特殊情况：当a=b时，\(\frac{x^2}{b^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}=1\), 可视为Oyz上的平面曲线\(\frac{y^2}{b^2}+\frac{z^2}{c^2}=1\)绕Oz轴旋转而成的曲面。

相关：
旋转曲面：轴平面上的曲线(即曲线在Oxy、Oxz、Oyz平面上)绕某一轴旋转。
例如在Oxy上，曲线表达式：f(x,y)=0，绕z轴旋转曲面可视为，y保持不变，x为旋转半径，即替换\(x为x=\pm\sqrt{x^2+z^2}\)

椭圆抛物面
方程：\(z=\frac{x^2}{a^2}+\frac{y^2}{b^2}\ (a>0,b>0)\)
即: \(\begin{cases}\frac{x^2}{a^2h}+\frac{y^2}{b^2h}=0,\\z=h.\end{cases}\)
几何图像：由方程可知z>0, 且随着z的增加，位于z点、平行于Oxy的平面对应的椭圆的两个半轴随之增大。
特殊情况：当a=b时，可视为抛物面\(z=\frac{y^2}{a^2}\)沿Oz轴旋转所得的旋转抛物面，\(y^2=x^2+y^2带入方程，即得z=\frac{x^2+y^2}{a^2}\)

相关：
二次锥面
双曲抛物面(马鞍面)
单叶曲面
双叶曲面



多元微积分
偏导、全微分、复合偏导、隐函数偏导、极值
偏导
定义：多元函数z=f(x,y)在某一点\(P_0(x_0,y_0)\)关于x的增量的变化率，称为关于x的偏导数
表示方式： \(f_x'(x_0,y_0)=\frac{d}{dx}f(x,y_0)|_{x=x_0}=\frac{\partial{z}}{\partial x}|_{y=y_0}^{x=x_0}=f_x'(x,y_0)|_{x=x_0}\)
/ \(=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}\)
几何意义：\(曲面f(x,y)与y=y_0平面的交线在点P_0处的点的切线(关于Ox轴)的斜率\)
表达式： \(\lim_{\triangle x\to0}{\frac{f(x_0+\triangle x,y_0)-f(x_0,y_0)}{\triangle x}}=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}\)
计算方法： 求偏导后带入、部分带入、定义法
$f_x'(x,y)|_{y=y_0}^{x=x_0}=\frac{\partial{z}}{\partial x}|_{y=y_0}^{x=x_0}=f_x'(x,y_0)|_{x=x_0}=\lim_{x\to x_0}{\frac{f(x,y_0)-f(x_0,y_0)}{x-x_0}}\\)

高阶偏导
表达：\(\frac{\partial^2{z}}{\partial{x^2}},\frac{\partial^2 z}{\partial x\partial y},f_{xx}''(x,y),f_{xy}''(x,y),f_{11}''(x,y),f_{12}''(x,y)\)
性质：混合偏导与顺序无关, 即\(f_{xy}''(x,y)=f_{yx}''(x,y)\)


全微分
定义：二元函数z=f(x,y)在点(x,y)处的全增量\(\triangle z=f(x+\triangle x,y+\triangle y)-f(x,y)=A\triangle x+B\triangle y+o(\rho)(\rho=\sqrt{(\triangle x)^2+(\triangle y)^2}\to0)\)
表达式：\((dz为\triangle x,y均趋于0时，\triangle z的极限)dz=A\triangle (d)x+B\triangle (d)y(A=\frac{\partial z}{\partial x},B=\frac{\partial z}{\partial y})\)
性质：
1. 必要：可微则连续、偏导均存在 
2. 充分：偏导均存在、且均连续(连续偏导)，则可微  
3. 不可微：1. 在该点处不连续 2. 有偏导不存在 3. 偏导存在，极限\(\lim_{\triangle x\to0,\triangle y\to0}{\frac{2\triangle x\triangle y}{(\triangle x)^2+(\triangle y)^2}}\)不存在或不为0.

复合函数
全导数(链导法则)：有几个相关中间变量，则为对应的中间变量偏导相加
例如：z(u,v,w)为u,v,w的函数，u,v,w是x的相关函数。
则z关于x的偏导\(\frac{\partial z}{\partial x}=\frac{\partial z}{\partial u}\frac{\partial u}{\partial x}+\frac{\partial z}{\partial v}·\frac{\partial v}{\partial x}+\frac{\partial z}{\partial w}·\frac{\partial w}{\partial x}\)
化简写法：\(\frac{\partial z}{\partial x}=f_1'u'+f_2'v'+f_3'w' (类似的f_{12}''=f_{21}'')\)
注：该函数的二阶偏导有三个对应的中间变量\(=f_{11}''(x)+f_{12}''(x)+f_{13}''(x)+f_{21}''(x)+...\)


全微分
若有 z=f(x,y), x=x(s,t), y=y(s,t) 都具有连续偏导,
则\(dz=\frac{\partial z}{\partial x}dx+\frac{\partial z}{\partial y}dy\)
=\(\frac{\partial z}{\partial x}(\frac{\partial x}{\partial s}ds+\frac{\partial x}{\partial t}dt)+\frac{\partial z}{\partial y}(\frac{\partial y}{\partial s}ds+\frac{\partial y}{\partial t}dt)\)
=\((\frac{\partial z}{\partial x}\frac{\partial x}{\partial s}+\frac{\partial z}{\partial y}\frac{\partial y}{\partial s})ds+(\frac{\partial z}{\partial x}\frac{\partial x}{\partial t}+\frac{\partial z}{\partial y}\frac{\partial y}{\partial t})dt\)
=\(\frac{\partial z}{\partial s}ds+\frac{\partial z}{\partial t}dt\)
此为一阶微分形式不变性，多元函数全微分同一元函数一样，高阶不具有不变性


隐函数的偏导
函数形式：\(f(x,u(x,y),z(x,y))=0\)
解法：对两边同时求偏导、或求微分
注：求微分后, 将无关增量如dz取零，即可得到\(\frac{dx}{dy}=\frac{\partial x}{\partial y}\)



多元函数极值(多元泰勒公式 待学)
性质：(设极值点\(P(x_0,y_0)\)
1. 必要：若在极值点存在偏导，则偏导均为0. (该点也称为驻点或稳定点)
2. 充分：前提：若在P点邻域内，连续且有二阶偏导，\(f_x'(x_0,y_0)=f_y'(x_0,y_0)=0,设A=f_{xx}''(x_0,y_0),B=f_{xy}''(x_0,y_0),C=f_{yy}''(x_0,y_0)\)
    (1) \(B^2-AC<0,f(x_0,y_0)\)一定为极值，A(或C)>0时，为极小值，A(或C)<0时，为极大值;
    (2) \(B^2-AC>0,f(x_0,y_0)\)不为极值;
    (2) \(B^2-AC=0,\)无法判断，需要进一步研究
极值怀疑点： 驻点、偏导数不存在点、边界点
技巧：若问题中一定有最大值(或最小值)，内部有唯一的怀疑点，则该函数值无需判断，必为最值

条件极值
极值求法(消元法、拉格朗日乘数法)
消元法：三元函数消成二元函数，分别求偏导=0，求出驻点或偏导不存在点。
拉格朗日乘数法：
1. 条件：\(\psi\)=G(x,y,z)=0  目标函数：u=f(x,y,z)
2. 引进拉格朗日函数\(L(x,y,z,\lambda)=u+\lambda \psi\)
(若有多个约束条件则：\(L(x,y,z,\lambda_1,\lambda_2,..)=u+\lambda_1\psi_1+\lambda_2\psi_2+..;其中\lambda_1,\lambda_2..称为拉格朗日乘数\)
3. 分别对x,y,z,\(\lambda\)求偏导=0，构造四个函数，求出四个未知数(若能在不求出\(\lambda\)的情况下求解，则最好)
4. 求出的解为最值怀疑点，若有多个怀疑点，还需进一步判断



二重积分性质、计算、应用
概念：面积乘以高，计算曲顶柱体的体积
1. 分割面积区域   dxdy
2. 近似点域，乘以对应趋于对应的高  f(x,y)
3. 在趋于范围内求和   \(\Sigma f(x,y)dxdy\)
4. 求分割面积趋于0的极限
性质：1. 线性变换与定积分相同
2. （被积函数大等于时，积分函数大于）若\(f(x,y)\geq g(x,y),f(x,y)\not\equiv g(x,y),则\iint_\sigma{f(x,y)d\sigma}>\iint_\sigma{g(x,y)d\sigma}\)（二重积分和定积分等同，是一个累加的过程）
3. 中值定理：f(x,y)在有界闭区域\(\sigma上连续，则在\sigma上至少存在一点P(x^*,y^*),\)
使得\(\iint_\sigma{f(x,y)d\sigma}=f(x^*,y^*)d\sigma；(f(x^*,y^*)区域内某一高度)\)
几何意义：二重积分\(\iint_\sigma{f(x,y)d\sigma}所求的曲顶柱体体积，等于以f(x^*,y^*)d\sigma为高，\sigma为底的柱体体积\)


二重积分的计算(直角坐标系、极坐标)
(注意：积分是求和的过程)
直角坐标系计算二重积分：
计算过程：\(\Sigma(长 \times \Sigma(宽 \times 高))\)
条件为：1. 长、宽、高的表达式；2. 两次求和范围(长、宽)；
例：表达式：长为x，宽为y，高为f(x,y)，\(y_1=\phi_1(x),y_2=\phi_2(x)；求和范围：x\in[a,b],y\in[\phi_1(x),\phi_2(x)]\)
则二重积分表达式为：\(\iint_\sigma{f(x,y)d\sigma}=\int_a^b{dx(长增量)\int_{\phi_1(x)}^{\phi_2(x)}f(x,y)(高)dy(宽增量)}\)
也可写成: \(\iint_\sigma{f(x,y)(高)d\sigma(面积增量)}=\iint_\sigma{f(x,y)(高)dx(长/宽)dy(宽/长)}\)； 其位置可以任意调换(对应x-型，y-型), 积不出来或计算复杂时，可尝试调换顺序


极坐标计算二重积分
计算过程：划分面积\(\triangle \sigma=\frac{\triangle\theta}{2}(r+\triangle r)^2-\frac{\triangle\theta}{2}r^2=r\triangle \theta\triangle r+\frac{\triangle \theta}{2}(\triangle \theta)^2\approx r\triangle \theta\triangle r=d\sigma\)
因为\(x=r\cos{\theta},y=r\sin{\theta},所以高f(x,y)=f(r\cos{\theta},r\sin{\theta})\)
得\(\iint_\sigma{f(x,y)d\sigma}=\iint_\sigma{f(r\cos{\theta},r\sin{\theta})rdrd\theta}\)
\\)
计算过程：\(\Sigma(角度增量\times \Sigma(长度\times长度增量 \times 高))\)
因此，条件为：1. 角度、长度、高的表达式；2. 两次求和范围(角度、半径)；
例：表达式：角度为\(\theta，长度为r，高为f(r\cos{\theta},r\sin{\theta})，r_1=\phi_1(\theta),r_2=\phi_2(\theta)；求和范围：\theta\in[a,b],r\in[\phi_1(\theta),\phi_2(\theta)]\)
则二重积分表达式为：\(\iint_\sigma{f(r\cos{\theta},r\sin{\theta})d\sigma}=\int_a^b{d\theta(角度)\int_{\phi_1(\theta)}^{\phi_2(\theta)}f(r\cos{\theta},r\sin{\theta})(高)rdr(长度)}\)
也可写成: \(\iint_\sigma{f(r\cos{\theta},r\sin{\theta})(高)d\sigma(增量面积)}=\iint_\sigma{f(r\cos{\theta},r\sin{\theta})(高)r(长度)d\theta(角度增量)dr(长度增量)}\)； 其位置可以任意调换(对应\(\theta\)-型，r-型--比较少见), 积不出来或计算复杂时，可尝试调换顺序


第一类曲线积分
定义：已知曲线线密度，求曲线质量
即:  \(M=\Sigma\rho(线密度) ds(曲线弧长)\)
方程：\(\int_\gamma{f(x(t),y(t),z(t))ds}；其中\gamma为曲线函数\)
曲线：\(\gamma=\begin{cases}x=x(t)\\y=y(t)\\z=z(t)\end{cases};t\in(\alpha,\beta)\ \ ds=\sqrt{x'^2+y'^2+z'^2}dt;\)
则方程表达式为：\(\int_\alpha^\beta{f(x(t),y(t),z(t)\sqrt{x'^2+y'^2+z'^2}dt;\ t\in(\alpha,\beta)}；\)


定积分的性质、条件
必要：可积必有界
充分：1. 连续有界；2. 有界，且有限个间断点；3. 闭区间单调(必有界)
性质：1. 线性运算；2. 区间可加性；3. 被积函数大等于且不恒等，积分必大于 4. 积分中值定理 \(\int_a^bf(x)dx=f(\xi)(b-a)\)


微积分学基本定理
变上限函数：\(一定值a\in I区间，f(t)在区间[a,x]上连续，从而可积，有G(x)=\int_a^xf(t)dt.x\in I 有结论G'(x)=f(x)\)（可用牛顿莱布尼兹公式和导数定义求解）
同理: \(G(x)=\int_{v(x)}^{u(x)}f(t)dt;\ G'(x)=f(u(x))u'+f(v(x))v'\) （同样可用牛顿莱布尼兹公式和定积分的区间可加性质求解）

