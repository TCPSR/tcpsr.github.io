---
title: "`effectsize` 套件使用指南"
subtitle: 工作坊成員協作成果#1
date: 2022-05-24T06:44:58.536Z
---
經過[第一堂課程](https://rstat-project.github.io/seed_courses/Lecture01.html#/)，為了各位學員之後在各種場域教授與討論效果量的計算與解讀，提供示範用的R程式碼及說明範例是相當有用的。我們將彙整Ben-Shachar等人(2020)開發的[R套件`effect size`](https://easystats.github.io/effectsize/index.html)，與Ellis(2010)Chapter
1,2的內容，以接力協作的方式編輯這份作業。每位學員貢獻一點成果，換取更多人在研究教學上的便利。

> 編輯流程：<br>
>1. 混合純文字及[Latex編碼](http://tug.ctan.org/info/latex-refsheet/LaTeX_RefSheet.pdf)編輯效果量公式<br>
> 2. 在R chunk內放置可執行的R程式碼<br> 
> 3. 隨時按’Knit’渲染可得編輯成果<br> 
> 4. 編輯完成在[討論區](https://github.com/Rstat-project/seed_courses/discussions)留言提交編輯成果。

## 計算效果量

### d family ~ difference between groups

#### Groups compared on dichotomous outcomes

-   The risk difference in probabilities

-   The relative risk

-   The odds ratio

#### Groups compared on continuous outcomes

-   Cohen’s d

比較獨立樣本平均數的效果量Cohen’s d計算公式:

$$Cohen's \\space d = \\frac{M\_1 - M\_2}{SD\_{pooled}} $$

R程式碼範例:<br/>

``` r
## 獨立樣本比較範例
## 範例資料來自`mtcars`
cohens_d(mpg ~ am, data=mtcars)
```

    ## Cohen's d |         95% CI
    ## --------------------------
    ## -1.48     | [-2.27, -0.67]
    ## 
    ## - Estimated using pooled SD.

``` r
## 輸出效果量及95%信賴區間
```

-   Glass’s delta( △ )

-   Hedges’ g

-   Probability of superiority

### r family ~ measures of association

#### Correlation indexes

(Two variables are continuous)

-   The Pearson product moment correlation coefﬁcient (*r*)

**負責學員** [魏志名(嘉義大學)](https://github.com/Wei1108)

皮爾森積差相關公式:<br/>

$$Pearson's \\space r = \\frac {\\sum\_{i=1}^{n}(X\_i-\\overline{X})(Y\_i-\\overline{Y})}{{\\sqrt{\\sum\_{i=1}^{n}(X\_i-\\overline{X})^2}}{\\sqrt{\\sum\_{i=1}^{n}(Y\_i-\\overline{Y})^2}}}$$

R程式碼範例:<br/>

``` r
cor_results <- cor.test(mtcars$mpg, mtcars$disp,conf.level = 0.95) 
report::report_effectsize(cor_results)
```

    ##  
    ## 
    ## very large (r = -0.85, 95% CI [-0.92, -0.71])

``` r
## 輸出效果量及95%信賴區間
```

(Two variables are ordinal)

-   Spearman’s rho or the rank correlation coefﬁcient (*ρ*)

-   Kendall’s tau (*τ*)

(One continous and one ordinal)

-   The point-biserial correlation coefﬁcient (*r*<sub>*p**b*</sub>)

(Contigency table)

-   The phi coefﬁcient (*ϕ*)

-   Pearson’s contingency coefﬁcient (C)

-   Cram´er’s V (V)

-   Goodman and Kruskal’s lambda (*λ*)

#### Proportion of variance indexes

-   The coefﬁcient of determination (*r*<sup>2</sup>)

**負責學員** [蕭富聲(佛光大學)](https://github.com/FGU-Xiao)

-   the (uncorrected) coefﬁcient of multiple determination
    (*R*<sup>2</sup>$)

-   the coefﬁcient of multiple determination adjusted for sample size
    and the number of predictor variables
    (<sub>*a**d**j*</sub>*R*<sup>2</sup>$)

-   Cohen’s f (*f*)

-   Cohen’s f squared

-   Epsilon squared (*e**p**s*<sup>2</sup>)

-   the (uncorrected) correlation ratio (*η*<sup>2</sup>)

-   Omega squared (*ω*<sup>2</sup>)

-   The squared canonical correlation coefﬁcient
    (*R*<sub>*C*</sub><sup>2</sup>)

## 解讀效果量

> `effectsize`套件收錄統計學者的建議，使用者預估[效果量**份量**](https://easystats.github.io/effectsize/articles/interpret.html)。在此彙整解讀效果量的函式使用方法。

#### 參考資源

Ben-Shachar, M. S., Lüdecke, D., & Makowski, D. (2020). effectsize:
Estimation of effect size indices and standardized parameters. Journal
of Open Source Software, 5(56), 2815.
<https://doi.org/10.21105/joss.02815>

Ellis, P. D. (2010). The essential guide to effect sizes: Statistical
power, meta-analysis, and the interpretation of research results.
Cambridge University Press.
