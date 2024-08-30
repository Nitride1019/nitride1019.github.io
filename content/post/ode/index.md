+++
author = "Nitride"
title = "工程數學-常微分方程 重點整理"
date = "2024-08-01"
image="images.png"
tags = [
    "工程數學",
    "數學",
    "ODE",
]
categories = [
    "數學",
]
+++

# 前言
注意!!!
本文是拿來複習用的，所以**強烈建議**先學過一次再來看。我推薦劉明昌的<<工程數學學習要訣>>上下冊，本文大部分都是從這本書以及一些網路資源上看的。
撰寫本文花了我一個下午。因為我平常沒有做筆記的習慣，所以大家想看的話我再寫別ㄉ。

# 一階ODE
## 基本定義
### 通解
- 一曲線族
- 未定係數之數目等於原方程式階數
### 特解
- 一曲線
- 未定係數之數目小於原方程式階數

## 變數分離型
### 型態
$$f(x)dx=g(y)dy$$
### 解法
兩邊積分即可

## 齊次函數型
### 型態
$$M(x, y)dx+N(x,y)dy=0$$
$$其中M與N為齊次函數$$
$$即M(\lambda x,\lambda y)=\lambda^kM(x,y),\,N(\lambda x,\lambda y)=\lambda^k(x,y)$$
### 解法
$$\frac{dy}{dx}=-\frac{M(x,y)}{N(x,y)}=-\frac{M(\lambda x,\lambda y)}{N(\lambda x, \lambda y)}$$
$$令\lambda=\frac{1}{x}，得 \frac{dy}{dx}=-\frac{M\left( 1, \frac{y}{x} \right)}{N\left( 1, \frac{y}{x} \right)}$$
$$再令y=vx,dy=vdx+xdv$$
$$得 \frac{dy}{dx}= \frac{vdx+xdv}{dx}-\frac{M(1,v)}{N(1, v)}=f(v)$$
$$移項得 \frac{dv}{f(v)-v}=\frac{dx}{x}，即可用變數分離型解法求解$$

### 性質: 任意$(ax+by+c)^kdx+(dx+ey+f)^kdy$型之方程式皆可用此法解
#### 證明
$$平移兩函數使其成為齊次方程式即可$$
$$解\begin{cases}ax+by+c=0\newline dx+ey+f=0\end{cases}$$
$$得x=x_0,y=y_0後$$
$$令X=x-x_0,Y=y-y_0$$
$$帶回原方程式得(aX+bY)^kdX+(dX+eY)^kdY=0$$
$$即可用齊次函數法解$$


## 恰當型
### 型態
$$M(x,y)dx+N(x,y)dy=0$$
$$且存在\Phi使 \frac{d\Phi}{dx}=M(x,y), \frac{d\Phi}{dy}=N(x,y)
$$
$$即\frac{\partial M}{\partial y}= \frac{\partial^2 \Phi}{\partial x \partial y}=\frac{\partial N}{\partial x}$$

(與微積分4的Green's Theorem學到的保守函數一樣)

### 解法
$$對\Phi積分得\Phi=\int M(x,y) \, dx+f(y)=\int N(x,y) \, dy+g(x)$$

### 特殊情況:$M(x,y)dx+N(x,y)dy=0，但\frac{\partial M}{\partial y}\ne \frac{\partial N}{\partial x}，且存在積分因子I(x,y)使 \frac{\partial(MI)}{\partial y}=\frac{\partial(NI)}{\partial x}$
#### Case 1: $\frac{\frac{\partial M}{ \partial y}-\frac{\partial N}{\partial x}}{N}=f(x)$

$$I=e^{\int f(x) \, dx}$$
##### 證明
$$由\frac{\partial(MI)}{\partial y}= \frac{\partial(NI)}{\partial x}可得 M \frac{\partial I}{\partial y}+I \frac{\partial M}{\partial y}=N \frac{\partial I}{\partial x}+I \frac{\partial N}{\partial x}$$
$$且I僅與x有關，故 \frac{\partial I}{\partial y}=0$$
$$移項得I\left( \frac{\partial M}{\partial y}-\frac{\partial N}{\partial x} \right)=N \frac{\partial I}{\partial x}$$
$$再移項得\frac{\frac{\partial M}{ \partial y}-\frac{\partial N}{\partial x}}{N}dx=f(x)dx= \frac{dI}{I}$$
$$積分可得I=e^{\int f(x) \, dx}$$


#### Case 2: $\frac{\frac{\partial M}{ \partial y}-\frac{\partial N}{\partial x}}{M}=g(x)$

$$I=e^{\int g(y) \, dy}$$


#### Case 3: $M與N皆為x,y的多項式$

$$令I=x^ay^b，並求解a, b$$


## 一階線性ODE
### 型態
$$y'+P(x)y=Q(x)$$

### 解法
$$y=\frac{1}{I}\int IQ \, dx，其中I=e^{\int P(x) \, dx}。$$

$$微積分2學過，相信大家都還記得(,,・ω・,,)$$


## Bernoulli Differential Equation
### 型態
$$y'+P(x)y=Q(x)y^a，a\ne 0, 1$$

### 解法
$$令z=y^{1-a}$$
$$代回原方程式可得 \frac{1}{1-a}z'+P(x)z=Q(x)$$
$$即可用一階線性ODE公式求解。$$

## 變數變換法
### 解法
觀察哪一項最特殊，並對其使用變數變換。

### 例題: $y'=x^2+2xy+y^2+2x+2y,\,y(0)=0$

$$解: 注意到x^2+2xy+y^2+2x+2y=(x+y)^2+2(x+y)$$
$$令z=x+y,\,dz=dx+dy，代入即可求解。$$
$$Ans:-\frac{1}{x+y+1}=x-1$$


## Riccati 方程式
### 型態
$$y'=P(x)y^2+Q(x)y+R(x)$$

### 解法
$$令y(x)=s(x)+\frac{1}{z(x)}$$
$$代回原式可得z'+[2P(x)s+Q(x)]z=-P(x)$$
$$即可用一階線性ODE公式求解$$

## Clairaut 方程式
### 型態
$$y=xy'+f(y')$$

### 解法
$$兩邊微分得y'=y'+xy''+y'' \cdot f'(y')$$
$$移項得y''[x+f'(y')]=0，產生2組解:$$
$$(1)\,若y''=0$$
$$積分兩次得y=c_{1}x+c_2，有2個未定係數，與原ODE階數不同$$
$$故須代回原式得c_{1}x+c_{2}=c_{1}x+f(c_{1})$$
$$得c_{2}=f(c_{1}),\,y=c_{1}x+f(c_{1})$$

$$(2)\,若x+f'(y')=0$$
$$令y'(x)=g(x)，代回原式得y=xg(x)+f(g(x))$$


# 高階ODE
## 常係數ODE
### 型態
$$a_{n}y^{(n)}+a_{n-1}y^{(n-1)}+\dots+a_{1}y'+a_{0}y=0$$

### 齊次解$y_{h}$解法
令$y=e^{\lambda x}，代入得a_{n}\lambda^{n}+a_{n-1}\lambda^{n-1}+\dots+a_{1}\lambda+a_{0}=0，求出\lambda的n個根$

#### (1) 若所有根均為相異實根
$$y=c_{1}e^{\lambda_{1}x}+c_{2}e^{\lambda_{2}x}+\dots+c_{n}e^{\lambda_{n}x}$$

#### (2) 存在複數根$a+bi$，必成共軛複數出現
$$y=c_{1}e^{(a+bi)x}+c_{2}e^{(a-bi)x}=e^{ax}[(c_{1}+c_{2})\cos bx+i(c_{1}-c_{2})\sin bx]$$
$$=e^{ax}(C_{1}\cos bx+C_{2}\sin bx)$$
(因目前所解的ODE均為實數系，故須將虛數以實數表示)

#### (3) 存在$k$個重根，即$\lambda_{1}=\lambda_{2}=\dots=\lambda_{k}$

$$y=(c_{0}+c_{1}x+\dots+c_{k-1}x^{k-1})e^\lambda x$$


### 特解$y_{p}$解法
#### 觀察法
觀察具有微分規律的項

#### 參數變異法，以二階ODE $y''+a(x)y'+b(x)y=Q(x)$為例
$$令特解y_{p}=u_{1}(x)y_{1}+u_{2}(x)y_{2}$$
$$此時強加一個條件: u_{1}'y_{1}+u_{2}'y_{2}=0$$

$$可得\begin{cases}u_{1}'y_{1}+u_{2}'y_{2}=0\newline u_{1}'y_{1}'+u_{2}'y_{2}'=Q(x)\end{cases}$$
$$即可用克拉瑪公式求得u_'{1},u_'{2}。$$

$$再積分即得u_{1},u_{2}$$
$$高階ODE也可用此方法，再加入一些強制條件後求得。$$


## Cauchy-Euler 方程式
### 型態
$$a_{n}x^ny^{(n)}+a_{n-1}x^{n-1}y^{(n-1)}+\dots+b_{1}xy'+b_{0}y=Q(x)$$

### 齊次解$y_h$解法
$$令y_{h}=x^m，求出m的n個根。以二階ODE為例$$

#### (1) 均為相異實根
$$y_{h}=c_{1}x^{m_{1}}+c_{2}x^{m_{2}}$$

#### (2) 存在複數根，必成共軛複數出現
$$令m_{1}=a+bi,\,m_{2}=a-bi$$
$$代入得y_{h}=x^a[C_{1}\cos(b\ln x)+C_{2}\sin(b\ln x)]$$

#### (3) 存在重根
$$y_{h}=c_{1}x^m+c_{2}x^m\ln x$$

##### 證明
$$令第二個解y_2=u(x)y_{1}$$
$$代入即可得u(x)=\ln x$$


### 通解解$y_p$解法
- 參數變異法
- 未定係數法

## 恰當型
### 型態
$$一個n階微分方程a_{n}(x)y^{(n)}+a_{n-1}(x)y^{(n-1)}+\dots+a_{1}(x)y'+a_{0}(x)y=R(x)$$
$$可由另一個n-1階微分方程b_{n-1}(x)y^{(n-1)}+b_{n-2}(x)y^{(n-2)}+\dots+b_{1}(x)y'+b_{0}y=Q(x)微分1次而得$$

### 條件
$a_{0}-a_1'+a_{2}''-\dots=0$

#### 證明
設原方程式可由另一方程式得到，比較係數即可。

## 降階法
### 型態
$$y''+P(x)y'+Q(x)y=0$$

$$且已知或易知一解y_{1}$$

### 解法
$$令y_2=u(x)y_{1}$$
$$即可轉換為u'的一階微分方程並求解$$

#### 特殊情況
##### (1) $P(x)+xQ(x)=0$

$$y_{1}=x為一齊次解$$

##### (2) $存在一實數C使C^2+CP(X)+Q(X)=0$

$$y_{1}=e^{ mx}為一齊次解$$


## 可化為一階ODE之解法
### $f(x,y',y'')=0$

$$缺y項，令z(x)=y'$$

### $f(y,y',y'')=0$

$$缺x項，令z(y)=y'$$



## 特殊變數代換
### 型態
$y''+P(x)y'+Q(x)y=R(x)$

### 因變數變更法
#### 解法
$$令y(x)=u(x)v(x)$$
$$代入原方程式得uv''+(2u'+Pu)v'+(u''+Pu'+Qu)v=R$$

$$(1)若u''+Pu'+Qu=0，則u為原ODE之解$$

$$代回原式得uv''+(2u'+Pu)v'=R$$
$$可直接用一階ODE公式解出v'再積分得到v$$

$$(2)若2u'+Pu=0$$
$$則u=e^{\int -\frac{P}{2} \, dx}$$
$$代回原式得v''+\left( Q-\frac{1}{4}P^2-\frac{1}{2}P' \right)v=\frac{R}{u}$$

$$若v''+\left( Q-\frac{1}{4}P^2-\frac{1}{2}P' \right)v=C，則解二階常係數ODE即可$$

$$若v''+\left( Q-\frac{1}{4}P^2-\frac{1}{2}P' \right)v=\frac{C}{x^2}，則得到v''+\frac{C}{x^2}v=\frac{R}{u}，為Cauchy-Euler方程式$$


### 自變數變更法
#### 解法
$$令z=z(x)$$
$$整理得 \frac{d^2y}{dz^2}+\frac{z''+Pz'}{(z')^2} \frac{dy}{dz}+\frac{Q}{(z')^2}y=\frac{R}{(z')^2}$$
$$此時若可令 \frac{Q}{(z')^2}=a, \frac{z''+Pz'}{(z')^2}=b，即可化為常係數ODE並求解。$$


# ODE之級數解
## Frobenius Method
### 型態
$$y''+P(x)y'+Q(x)y=0$$

$$且x=x_{0}為規則異點$$

### 解法
$$y=\sum^{\infty}_{n=0} a_n (x-x_0)^{n+r} $$


## Legendre Polynomials
### 型態
$$(1-x^2)y''-2xy'+n(n+1)y=0$$

### 解法

$$將y=\sum^\infty_{i=0}a_{i}x^i代入後可得$$
$$a_{i+2}= \frac{(i-n)(i+n+1)}{(i+2)(i+1)}a_{i}$$
$$並得解為y(x)=P_n=a_{0}y_{1}+a_{1}y_{2}$$

$$其中y_{1}是偶函數，y_{2}是奇函數$$

$$且須滿足P_{n}(1)=1$$

### 性質
#### Rodrigue公式
$$P_{n}(x)=\frac{1}{2^nn!} \frac{d^n}{dx^n}[(x^2-1)^n]$$

#### 生成函數
$$(1-2xt+t^2)^{-1/2}=\sum^\infty_{n=0}P_{n}(n)t^n$$


## Bessel方程式
### 型態
$$x^2y''+xy'+(x^2-p^2)y=0$$

### 解法
$$用Frobenius\,Method可得a_{n}=-\frac{1}{n(n\pm2p)}a_{n-2}$$
$$括弧內取正號可求得J_{p}=\frac{\sum^\infty_{n=0}(-1)^nx^{2n+p}}{2^{2n+p}n!\Gamma(n+p+1)}
$$
$$取負號可求得J_{-p}=\frac{\sum^\infty_{n=0}(-1)^nx^{2n-p}}{2^{2n-p}n!\Gamma(n-p+1)}$$

$$y=c_{1}J_{p}+c_{2}J_{-p}$$

### 性質
$$若p為整數，則J_p=(-1)^pJ_{-p}$$

$$此時J_{p}與J_{-p}已不線性獨立，故須尋求另解$$


### 第二類Bessel函數
$$令Y_{p}=\frac{J_{p}\cos p\pi-J_{-p}}{\sin p\pi}$$
$$則Bessel方程式的解為y(x)=c_{1}J_{p}+c_{2}Y_{p}$$
$$當p為整數時，用羅必達法則可求得$$

$$Y_p=\frac{2}{\pi} ( \ln \frac{x}{2} ) J_n- \frac{1}{\pi}\sum_{m=0}^{n-1} \frac{(n-m-1)!}{m!} \frac{x}{2}^{2m-n}- \frac{1}{\pi}\sum^\infty_{m=0} [\Phi(m)+ \Phi(n+m)] \frac{(-1)^m}{m!(n+m)!} \frac{x}{2}^{2m+n}$$


$$其中\Phi(x)=1+\frac{1}{2}+\frac{1}{3}+\dots+\frac{1}{p},\Phi(0)=0$$

### 第三類Bessel函數
$$令H^{(1)}_p(x)=J_p(x)+iY_p(x)$$

$$H^{(2)}_p(x)=J_p(x)-iY_p(x)$$

$$得Bessel方程式通解為y(x) = c_1H^{(1)}_p(x) + c_2H^{(2)}_p(x) $$


### 修正型Bessel函數
$$解x^2y''+xy'-(x^2+p^2)y=0$$

$$得通解為y(x)=c_{1}J_{p}(ix)+c_{2}Y_{p}(ix)$$


#### 第一類修正型Bessel函數

$$令I_{p}(x)=\sum^\infty_{m=0} \frac{x^{2m+p}}{2^{2m+p}m!\Gamma(p+m+1)}$$

$$得I_{p}(x)=i^{-p}J_{p}(ix),I_{-p}(x)=i^pJ_{-p}(ix)$$
$$故當p不為整數時，通解y(x)=c_{1}I_{p}(x)+c_{2}I_{-p}(x)$$

#### 第二類修正型Bessel函數
$$令K_p(x)=\frac{\pi}{2} \frac{I_{-p}(x)-I_{p}(x)}{\sin p\pi}$$

$$則通解可寫為y(x)=c_{1}I_{p}(x)+c_{2}K_{p}(x)，p\in R$$


### Bessel函數之微分
$$\frac{d}{dx}[x^pJ_{p}(x)]=x^pJ_{p-1}(x)$$

$$\frac{d}{dx}[x^{-p}J_{p}(x)]=-x^{-p}J_{p+1}(x)$$

$$pJ_{p}(x)+xJ_'p(x)=J_{p-1}(x)$$

$$pJ_{p}(x)+xJ_'p(x)=xJ_{p-1}(x)$$

$$-pJ_{p}(x)+xJ_'p(x)=-xJ_{p+1}(x)$$

$$J_{p+1}(x)=\frac{2p}{x}J_{p}(x)-J_{p-1}(x)$$

### 半階Bessel函數

$$J_{\frac{1}{2}}(x)= \sqrt{ \frac{2}{\pi x} }\sin x$$

$$J_{-\frac{1}{2}}(x)= \sqrt{ \frac{2}{\pi x} }\cos x$$

$$I_{\frac{1}{2}}(x)= \sqrt{ \frac{2}{\pi x} }\sinh x$$

$$I_{-\frac{1}{2}}(x)= \sqrt{ \frac{2}{\pi x} }\cosh x$$

# 後記
把工程數學學習要訣上冊打完3/8了(灑花)。

發現還有下冊ヾ(;ﾟ;Д;ﾟ;)ﾉﾞ

還好有Obsidian有Latex的快捷輸入 我才花比較少時間。

原本Notion上寫 寫到快懷疑人生。

還有架網站也花了蠻多時間的(畢竟我平常也不會沒事去架網站)
![p](20240731_195146.jpg)