1) P(0<X<2 | Y>1) = P(X=1,Y=2) / P(Y=2) 
	= (5/36) / (15/36) 
	= 1/3 
	≈ 0.33

---

2) List all 2³=8 equally‐likely outcomes and for each record  
   - X = total # heads  
   - Y = points scored (first head on toss 1→1pt, toss 2→2pt, toss 3→3pt, no heads→–1pt)  

   | outcome | X | first head at | Y  |
   |:-------:|:-:|:-------------:|:--:|
   | TTT     | 0 | –             | –1 |
   | TTH     | 1 | 3             | 3  |
   | THT     | 1 | 2             | 2  |
   | THH     | 2 | 2             | 2  |
   | HTT     | 1 | 1             | 1  |
   | HTH     | 2 | 1             | 1  |
   | HHT     | 2 | 1             | 1  |
   | HHH     | 3 | 1             | 1  |
   
   We want  
   -  “fewer than three heads”: X<3 → outcomes with X=0,1,2  
   -  “score 1 or less”: Y≤1 → Y=1 or Y=–1  
   
   Identify matching outcomes:  
   - Y=–1 & X<3: only TTT ⇒ P=1/8=0.125  
   - Y=1 & X<3: HTT, HTH, HHT ⇒ 3 outcomes ⇒ P=3/8=0.375  

   Sum: 0.125+0.375=0.50  

Answer (to two decimals): 0.50

---


3) Compute `P(face card)=12/52=3/1`
	 `P(non-face)=1–3/13=10/13`  
	 
	For X=0 (bag A, 2 draws):  
   P(Y=1|X=0)=C(4,1)·C(11,1)/C(15,2)=44/105  
   
	For X=1 (bag B, 3 draws):  
   P(Y=1|X=1)=C(7,1)·C(13,2)/C(20,3)=546/1140 
    
	Law of total probability:  
   f_Y(1)= (3/13)(44/105)+(10/13)(546/1140) ≈0.47

---

4) Apply marginalization: `f_X(x)=∑_{y}f_{X,Y}(x,y)` ⇒ option 1 correct  
	Test option 2: `P(X,Y,Z)=P(X|Y,Z)·P(X)?` ⇒ fails  
	Test option 3: `P(X,Y,Z)=P(X|Y,Z)·P(Y|X)·P(X)?` ⇒ fails  
	Test option 4: `f_X(x)=∑_{x}f_{X,Y}(x,y)?` ⇒ index wrong ⇒ fails 
Answer: only option 1.

---
5) 
- Write two equations in a,b:  
	`a·∑_{x=1,2; y=0–2}(bx+y)=4/7
	`a·∑_{x=0–2; y=0–3}(bx+y)=1` 
-  Compute sums:  
	`∑_{x=1,2; y=0–2}(bx+y)=9b+6
	`∑_{x=0–2; y=0–3}(bx+y)=12b+18 
-  Equate and solve:  
   `a(9b+6)=4/7,  a(12b+18)=1  ⇒  b=2,  a=1/42`  
-  `f_{X,Y}(2,0)=a·(2b+0)=4/42=2/21≈0.10`
---
6)
- Total sequences with X=2: C(4,2)=6  
>C is a Combinatoric
$$
nCr = n!/r!(n-r)!
$$

- For Y=0, first toss=T, need 2 heads in tosses 2–4: C(3,2)=3  
- f_{Y|X=2}(0)=3/6=0.50
---
7)
- Numerator: `C(4,1)·C(3,1)=4·3=12`  
- Denominator: `C(9,2)=36`  
- `f_{XY}(1,1)=12/36=1/3≈0.33` 
---
8) $$Pr(X=1,Y=1) = 5!/(1!1!3!)·(1/6)²·(4/6)³ 
	 = 1280/7776 
	 ≈ 0.165
	 $$
---
9)
- Steps to find f_X(x):  
-  y runs over {–1,0,1}. For each y solve –2≤x+y≤2:  
   – y=–1 ⇒ x∈{–1,0,1,2,3} (5 pairs)  
   – y=0  ⇒ x∈{–2,–1,0,1,2} (5)  
   – y=1  ⇒ x∈{–3,–2,–1,0,1} (5)  
- Total pairs =15.  
-  Count how many y’s for each x:  
   x=–3→1, –2→2, –1→3, 0→3, 1→3, 2→2, 3→1  
-  f_X(x)=count/15 ⇒  
   f_X(x)=⎧1/15 if x=–3 or 3; 2/15 if x=–2 or 2; 3/15 if x=–1,0,1; 0 otherwise.  
---
10) 
-  Steps to find f_Y(y):  
-  For each y∈{–1,0,1} the x-range has 5 values (see above).  
-  Total=15 ⇒ f_Y(y)=5/15=1/3 for y=–1,0,1; 0 otherwise.