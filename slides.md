---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: none

# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
font:
  sans: 'Roboto'
  serif: 'Roboto'
  mono: 'Fira Code'
---

# λ

Lambda Calculation

---
transition: slide-left
layout: center
---

# Hello Lambda Expression
echo >> "hello"

```
(lambda echo (Y(lambda f. lambda x y c. (lambda c x y ) (echo x y) (f (add x lambda s z. s (s (s (s (s (s (s z)))))))
 (add y lambda s z. s (s (s (s (s (s (s (s (s (s z))))))))))) (add g lambda s z. s z) pred c)))
 (lambda x y. print (plus x lambda s z. s (s z)) (plus y lambda s z. s z) )
 (plus y lambda s z. s (s (s (s (s (s (s (s (s z))))))))
  (plus y lambda s z. s (s (s (s (s (s (s (s (s z)))))))) 
  (plus y lambda s z. s (s (s (s (s (s (s (s (s (s (s z)))))))))))))
```


---
transition: slide-up
layout: center
---

# What's Lambda Expression

<br>

$$
\lambda{x.\ x}
$$

<br>
---
transition: slide-up
layout: center
---

# Currying

<br>

$$
\lambda{x.\ y.\ x+y}
$$

<div v-click>
<p class="flex justify-center">⬇️</p>

<div class="flex justify-center">

$\lambda{x.\ \lambda{y.\ x + y}}$
</div>
</div>

<div v-click>
<br>
<br>
```haskell
divideByTen::(Floating a) => a -> a
divideByTen = (/10)
```

</div>

<br>



---
transition: slide-up
layout: center
---

# $\alpha$ conversion


<br>

$$
\lambda {x.\ x}
$$

<div v-click>
  <p class="flex justify-center">⬇️</p>

<div class="flex justify-center">

$$
\lambda {y.\ y}
$$
</div>
</div>

---
transition: slide-left
layout: center
---

# $\beta$ reduction

<br>

$$
(\lambda {x.\ x} + 5)\ 1
$$

  <p class="flex justify-center">Apply beta reduction</p>

$$
1 + 5
$$


---
transition: slide-left
layout: center
---

# $\alpha$ conversion & $\beta$ reduction

<br>

$$
(\lambda{x.\ } \lambda {y.\ x+y})\ y
$$

If the **Lambda** function is applied $\beta$ reduction without $\alpha$ conversion

$$
(\lambda{x.\ } \lambda {y.\ x+y})\ y \\
= \lambda{y.\ y + y}
$$
if y = 2; then
$$
(\lambda{x.\ } \lambda {y.\ x+y})\ 2 \\
= \lambda{y.\ 2 + 2} \\
= \lambda{y.\ 4}
$$

<br>

---
transition: slide-up
layout: center
---

Cause the variable `y` is bound on the function, but the outside `y` is a free variable.
So we should apply $\alpha$ conversion first:

$$
(\lambda{x.\ } \lambda {y.\ x+y})\ y \\
= (\lambda{x.\ } \lambda {z.\ x+z}) y \\
= (\lambda{z.\ y+z}) \\

$$
if y = 2; then
$$
= (\lambda{z.\ 2+z})
$$


---
transition: slide-left
layout: center

---

# Church Numerals

- $0 = \lambda{s\ z.\ z}$
- $1 = \lambda{s\ z.\ s \ z}$
- $2 = \lambda{s\ z.\ s\ (s \ z)}$
- $3 = \lambda{s\ z.\ s\ (s\ (s \ z))}$
- $4 = \lambda{s\ z.\ s\ (s\ (s\ (s \ z)))}$
- $5 = \lambda{s\ z.\ s\ (s\ (s\ (s\ (s \ z))))}$
- $6 = \lambda{s\ z.\ s\ (s\ (s\ (s\ (s\ (s \ z)))))}$
<br>
...

> s: successor function
<br>
>z: zero function


$n = \lambda{s\ z.\ s^n\ z}$ 


---
transition: slide-left
layout: center
---

# Operators

- $add = \lambda{m\ n\ s\ z.\ m\ s\ (n\ s\ z)}$
- $mul = \lambda{n\ f\ x.\ n\ (m\ f)}$
- $succ = \lambda{n\ f\ x.\ f\ (n\ f\ x)}$
<br>
...


---
transition: slide-left
layout: center
---

# Add operator
<br>

<div v-click-hide class="flex justify-center">1 + 2</div>
<div v-click="1" class="flex justify-center">

$$
(\lambda{s\ z.\ s\ z}) + (\lambda{s\ z.\ s\ (s\ z)})
$$

</div>
<br>

<div v-click="2">

$$
  (\lambda{m\ n\ s\ z.\ m\ s\ (n\ s\ z)})\ (\lambda{s\ z.\ s\ z})\ (\lambda{s\ z.\ s\ (s\ z)}) \\
  = (\lambda{m\ n\ s\ z.\ m\ s\ (n\ s\ z)})\ (\lambda{s'\ z'.\ s'\ z'})\ (\lambda{s''\ z''.\ s''\ (s''\ z'')}) \\
  = \lambda{s\ z.\ (\lambda{s'\ z'.\ s'\ z'})\ s\ ( (\lambda{s''\ z''.\ s''\ (s''\ z'')})\ s\ z)}\\
  = \lambda{s\ z.\ (\lambda{s'\ z'.\ s'\ z'})\ s\ (s\ (s\ z))}\\
  = \lambda{s\ z.\ s\ (s\ (s\ z))} \\
$$

</div>

---
transition: slide-left
layout: center
---
# Control flow
<br>

$$
FALSE = \lambda{x\ y.\ y}\\
TRUE = \lambda{x\ y.\ x}\\
if = \lambda{x\ y\ z.\ x\ y\ z}\\
AND = \lambda{x\ y.\ x\ y\ FALSE}\\
OR = \lambda{x\ y.\ x\ TRUE\ y}\\
NOT = \lambda{x.\ x\ FALSE\ TRUE}\\
$$

---
transition: slide-left
layout: center
---
# Examples
<br>
if x == 0 AND y == 0; then 0 else 1

<div v-click="1">

$x = \lambda{s\ z.\ z}\\$
$y = \lambda{s\ z.\ s z}\\$
$iszero =  \lambda{n.\ n\ (\lambda{n.\ \lambda{x\ y.\ y}})\ (\lambda{x\ y.\ x}})\\$
</div>

<div v-click="2">

$$
(\lambda{iszero\ x\ y. (\lambda{x\ y\ z.\ x\ y\ z})\ (
  (\lambda{x\ y.\ x\ y\ FALSE})\ 
    (iszero\ x)\  
    (iszero\ y)
  )\ (\lambda{s\ z.\ z})\ (\lambda{s\ z.\ s\ z})})\ iszero\ x\ y
$$

</div>

<div v-click="3">

**$\alpha$ convert:**

$$
(\lambda{iszero\ x\ y. 
(\lambda{x\ y\ z.\ x\ y\ z})\ (
  (\lambda{x'\ y'.\ x'\ y'\ FALSE})\ 
    (iszero\ x)\  
    (iszero\ y)
  )\ (\lambda{s\ z.\ z})\ (\lambda{s\ z.\ s\ z})})\ iszero\ x\ y
$$

</div>

<div v-click="4">

**$\beta$ reduction:**

$$
(\lambda{x\ y\ z.\ x\ y\ z})\ (
  (\lambda{x'\ y'.\ x'\ y'\ (\lambda{x\ y.\ y})})\ 
    (iszero\ x)\  
    (iszero\ y)
  )\ (\lambda{s\ z.\ z})\ (\lambda{s\ z.\ s\ z})

  \\
  =(\lambda{x'\ y'.\ x'\ y'\ (\lambda{x\ y.\ y})})\ 
    (iszero\ (\lambda{s\ z.\ z}))\  
    (iszero\ (\lambda{s\ z.\ s\ z}))

  \\
  
  =(\lambda{x'\ y'.\ x'\ y'\ (\lambda{x\ y.\ y})})\ 
    (\lambda{x\ y.\ x})\  
    (\lambda{x\ y.\ y})

  \\

  = (\lambda{x\ y.\ x})\ (\lambda{x\ y.\ y})\ (\lambda{x\ y.\ y})
  \\
  = (\lambda{x\ y.\ y})
  \\
  = FALSE

$$

</div>

---
transition: slide-left
layout: center
---

# What's the fixed point


---
transition: slide-left
layout: center
---

# The cycles
<br>

$$f^n(x)=x$$

<div v-click="1">

$f(x)=-2x^3+1.5x+0.5\\$
$f(0)=0.5\\$
$f(0.5)= -0.25 + 0.75 + 0.5 = 1 \\$
$f(1) = -2 + 1.5 + 0.5 = 0\\$

</div>

---
transition: slide-left
layout: center
---

# Fixed point
<br>

$$f^n(x)=x\ (n = 1)$$

<img src="https://upload.wikimedia.org/wikipedia/commons/3/3c/Fixed_Point_Graph.png" />


---
transition: slide-left
layout: center
---

# The FP of functional
<br>

If the `g` is a function rather than a value, so the `f` must be a functional.

$$
f(g) = g
$$

---
transition: slide-left
layout: center
---

# FP combinator
<br>
<!-- 这跟要实现的循环，跟递归有什么关系？ -->


Assume I have a `rec` functional which look like:

$
rec \ f = f(rec\ f)
$

then

$
rec\ f = f(f(f(...)))
$

<br>
<br>

<div v-click>

$rec \ f = f(rec\ f)\\$

The FP is `rec f`

</div>

---
transition: slide-left
layout: center
---

# Y FP combinator

<br>

$$ 
Y = \lambda{f.\ (\lambda{x.\ f\ (x\ x)})\ (\lambda{x.\ f\ (x\ x)})}
$$

<br>

In strict evaluation programming language:
```js
def Y = f -> (x -> x(x))(y -> f(x -> y(y)(x)))
```

In lazy evaluation programming language:
```hs
yCombinator::(a -> a) -> a
yCombinator = \f -> (\x -> f (unsafeCoerce x x)) (\x -> f (unsafeCoerce x x))
```

---
transition: slide-left
layout: center
---

# Why "Y"

<img src="http://cgnail.github.io/images/y.jpg">

---
transition: slide-left
---

# How does the Y FP combinator works?
<br>

$fac = \lambda{f.\ \lambda{n.\ (iszero\ n)\ 1\ (mul\ n\ (f\ (pred\ n)))}}$

$factorial = Y\ fac = fac\ (Y\ fac) = fac\ (fac\ (Y\ fac)) = fac\ (fac\ (fac\ (Y\ fac)))\ \ ...$

$factorial\ 3 
\\= Y\ fac 
\\= fac\ (Y\ fac) 
\\= fac\ (fac\ (Y\ fac)) 
\\= fac\ (fac\ (fac\ (...Y\ fac)))\ 3
\\= mul\ 3\ ((fac (fac (...Y fac)))\ 2)
\\= mul\ 3\ (mul\ 2\ ((fac (...Y fac))\ 1))
\\= mul\ 3\ (mul\ 2\ (mul\ 1\ (((...Y fac))\ 0)))
\\= mul\ 3\ (mul\ 2\ (mul\ 1\ 1))
\\= 6
$

---
transition: slide-left
layout: center
---

# Thinking 🤔

Why introduce lambda expressions into a programming language

---
transition: slide-left
layout: center
---

# 🙋‍♂️Q & A
