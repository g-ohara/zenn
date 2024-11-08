---
title: "ニューラルネットワークの誤差逆伝播"
emoji: "⚙️"
type: "tech"
topics: ["neuralnetwork"]
published: true
---

# 概要

- 誤差逆伝播を今さらながら復習したのでまとめておく

# 説明

## 設定

隠れ層が $k$ 層の場合を考える． 第 $m$ 層のユニット数を $N^{m}$，出力を $\bm{x}^m=[x_1^m,x_2^m,\dots,x_{N^m}^m]^\top$ とし，第 $m$ 層の $i$ 番目のユニットの重みを $\bm{w}_i^m=[w_{i1}^{m},w_{i2}^{m},\dots,w_{iN^{m-1}}^{m}]^\top$ とする．
入力層を第 0 層の隠れ層，出力層を第 $k+1$ 層の隠れ層とみなし，入力を $\bm{x}^0$，出力を $\bm{x}^{k+1}$ とする．
正解データを $\bm{d}={[d_1,d_2,\ldots,d_{N^{k+1}}]}^\top$ とし，誤差関数を

$$E=\frac{1}{2}\sum_{i=1}^{N^{k+1}}{\left(x_i^{k+1}-d_i\right)}^2=\frac{1}{2}\|\bm{x}^{k+1}-\bm{d}\|^2$$

とする．活性化関数を $f:\mathbb{R}\to\mathbb{R}$ とし，第 $m$ 層のユニットの内部状態 (活性化関数に通す前の値) を $\bm{s}^m=[s_1^m,s_2^m,\dots,s_{N^m}^m]^\top$ とすると，各ユニットにおける順伝播は

$$\begin{aligned}s_i^m&={\bm{w}_i^m}^\top\bm{x}^{m-1},\\x_i^m&=f(s_i^m)\end{aligned}$$

と表される．

## 誤差逆伝播 (backpropagation)

出力層における誤差関数の勾配は

$$\begin{aligned}\frac{\partial E}{\partial w_{ij}^{k+1}}&=\sum_{l=1}^{N^{k+1}}\frac{\partial E}{\partial x_l^{k+1}}\frac{\partial x_l^{k+1}}{\partial {s_l^{k+1}}}\frac{\partial{s_l^{k+1}}}{\partial w_{ij}^{k+1}}\\&=(x_i^{k+1}-d_i)\cdot f'(s_i^{k+1})\cdot x_j^{k}\end{aligned}$$

となる．また第 $m$ 層 ($1\le m\le k$) における誤差関数の勾配は

$$\begin{aligned}\frac{\partial E}{\partial w_{ij}^{m}}&=\sum_{l=1}^{N^{m}}\frac{\partial E}{\partial x_l^{m}}\frac{\partial x_l^{m}}{\partial s_l^m}\frac{\partial s_l^m}{\partial w_{ij}^{m}}\\&=\frac{\partial E}{\partial x_i^{m}}\cdot f'(s_i^m)\cdot x_j^{m-1}\end{aligned}$$

となる．ここで

$$\delta_i^m=\frac{\partial E}{\partial s_i^{m}}\cdot f'(x_i^{m+1})$$

とすると，

$$\begin{aligned}\frac{\partial E}{\partial w_{ij}^{m}}&=\delta_i^m\cdot x_j^{m-1}\\\delta_j^m & =\sum_{i=1}^{N^{m+1}}\delta_i^{m+1}\cdot f'(x_i^{m+1})\cdot w_{ij}^{m}\end{aligned}$$

となる．
