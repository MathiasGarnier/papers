# Fourth-derivative estimates via small cap decoupling: audit, corrected theorem, limits

Nov 10, 2026 · @Mathias

## 1. Summary

The source report (M. Garnier, *Exponential sum estimates using Vinogradov Mean Value Theorem*, 2025) contains errors, so its headline result cannot be taken as a base. The claimed bound μ(11/15) ≤ 11/180 is not proved: one step of the argument is a non sequitur, and the bound it needs is not supplied by any estimate in the report. What survives is a genuine, smaller result on the fourth-derivative test, which is stated and proved here in corrected and extended form.

**What is proved here (Theorem A).** Let f have a continuous fourth derivative with 0 < λ ≤ f⁗ ≤ Aλ on (0, N), and write λ = N^(−ϖ). For 1 ≤ ϖ ≤ 4 and every ε > 0, the sum of e(f(n)) over n ≤ N is O(N^(E(ϖ)+ε)) with

```latex
E(\varpi)=\begin{cases}
1-\dfrac{\varpi}{4\varpi+8}, & 1\le \varpi\le 2,\\[2mm]
1-\dfrac{\varpi(4-\varpi)}{8(\varpi+2)}, & 2\le \varpi\le \tfrac83,\\[2mm]
\dfrac57+\dfrac{\varpi}{14}, & \tfrac83\le \varpi\le 4.
\end{cases}
```

This is the best available bound depending only on the fourth derivative in the range 2√2 − 1 < ϖ < 4, that is N^(−4) < λ < N^(−1.828…). For ϖ ≥ 8/3 it beats the classical van der Corput bound by a fixed factor N^(1/28). The range ϖ > 2 is not treated in the source report or in Heath-Brown's appendix.

**What the audit found.**

- Propositions 3.12 and 3.14 are true but their extra terms N^(7/8) and N^(6/7) are vacuous: under the stated hypothesis 1 ≤ ϖ ≤ 2 the first term always dominates. Both propositions say the same thing, namely the first line of E above.
- Proposition 3.20 (second range) and Corollary 3.23 are not proved. At N = t^(3/10) the corollary needs exponent 253/900 ≈ 0.28111, while the report's tools give 17/60 ≈ 0.28333.
- The value 1/15 for μ(11/15) is not the state of the art, as Heath-Brown himself notes. Classical van der Corput estimates alone give 49/750, the report's own toolbox gives 67/1050 ≈ 0.06381, and the current ANTEDB table gives ≈ 0.06143.
- Proposition 3.16 omits the constraint linking β to λ and is ill-posed as stated. A corrected conditional version is in Section 8.

**What is not achieved.** No bound on the Riemann zeta function is improved. Section 6 shows why: the new range of Theorem A corresponds to sums where the third-derivative test and exponent pairs are already stronger.

**Dependence on outside work.** Theorem A rests on Theorem 1.1 of Maldague–Oh (arXiv:2411.18016, a preprint when checked on 10 November 2026) and on two lemmas of Heath-Brown. I have not found Theorem A in the literature, but I cannot certify novelty.

## 2. Setting and external inputs

The proof of Theorem A uses three results from the literature, stated here in the form needed. Throughout, e(x) = exp(2πix), ‖x‖ is the distance from x to the nearest integer, and X ≪ Y means |X| ≤ CY with C depending only on the indicated parameters.

**Standing hypotheses (H).** N ≥ 2 is an integer, k ≥ 3, A ≥ 1, and f : \[0, N\] → ℝ is continuous with a continuous k-th derivative on (0, N) satisfying

```latex
0<\lambda\le f^{(k)}(x)\le A\lambda\le \tfrac14 \qquad (0<x<N).
```

We put K = k(k−1)/2 and H = ⌊(Aλ)^(−1/k)⌋, and we assume 2 ≤ H ≤ N. The case f^(k) < 0 follows by complex conjugation.

**Input 1 (Maldague–Oh, Theorem 1.1).** For σ ≥ 0, p ≥ 2, ε > 0, every N ≥ 1 and all complex a\_1, …, a\_N,

```latex
\Big(\int_{[0,1]^2\times[0,N^{-\sigma}]}\Big|\sum_{h=1}^{N}a_h\,e(hx_1+h^2x_2+h^3x_3)\Big|^{p}dx\Big)^{1/p}
\le C_{\varepsilon}N^{\varepsilon}D_p(\sigma,N)\Big(\sum_{h=1}^{N}|a_h|^{p}\Big)^{1/p},
```

```latex
D_p(\sigma,N)=\begin{cases}
N^{\frac12-\frac{\sigma+1}{p}}+N^{1-\frac7p}, & 0\le\sigma<\tfrac52,\\[1mm]
N^{\frac12-\frac{\sigma+1}{p}}+N^{\frac{\sigma}{3}-\frac{7\sigma}{3p}}+N^{1-\frac7p}, & \tfrac52\le\sigma<3.
\end{cases}
```

The range 0 ≤ σ ≤ 3/2 with unimodular coefficients is Theorem 3.3 of Demeter–Guth–Wang, and 0 ≤ σ ≤ 2 is due to Guth–Maldague. I checked the statement above against the arXiv text of Maldague–Oh. Two features matter: the coefficients are arbitrary, and the right side is an ℓ^p norm.

**Corollary 2.1 (shifted and truncated form).** Let X ≥ 1 be an integer, 0 ≤ β ≤ 5/2, s = 6 − β, c real and 1 ≤ x ≤ X. Then

```latex
\int_{[0,1]^2\times[c,\,c+X^{-\beta}]}\Big|\sum_{h\le x}e(h\alpha_1+h^2\alpha_2+h^3\alpha_3)\Big|^{2s}d\alpha\ \ll_{\varepsilon}\ X^{2s-6+\varepsilon}.
```

*Proof.* Substitute α\_3 = c + y with 0 ≤ y ≤ X^(−β). The sum becomes a sum over h ≤ X with coefficients a\_h = e(c h³) for h ≤ x and a\_h = 0 otherwise, so the sum of |a\_h|^(2s) is at most X. Apply Input 1 with N = X, σ = β, p = 2s. For β < 5/2 this gives X^(1+ε) (X^(s−β−1) + X^(2s−7)) up to a factor 2^(2s), which is X^ε (X^(s−β) + X^(2s−6)). Both exponents equal 2s − 6 when s = 6 − β. For β = 5/2, p = 7, the second case of D\_p applies and all three terms are X^0, so the integral is ≪ X^(1+ε) = X^(2s−6+ε). ∎

*Uniformity in β.* The constant C\_ε may depend on σ. This is harmless: an integral over \[c, c + X^(−β)\] is at most the integral over \[c, c + X^(−β′)\] when β′ ≤ β. Rounding β down to a multiple of ε leaves finitely many values of β′ and changes the exponents by O(ε).

**Input 2 (Heath-Brown 2017, Lemma 3; source report, Lemma 3.7).** Under (H), the number 𝒩 of pairs (m, n) with m, n ≤ N and ‖f^(j)(m)/j! − f^(j)(n)/j!‖ ≤ 2H^(−j) for 1 ≤ j ≤ k − 1 satisfies

```latex
\mathcal N\ \ll_{A,k}\ \big(N+\lambda N^{2}+\lambda^{-2/k}\big)\log N .
```

**Input 3 (Heath-Brown, localized form of the mean value lemma).** This is Lemma 4.1 below. It is Lemma 2 of Heath-Brown 2017 with the modification from the appendix to Demeter–Guth–Wang. I give a complete proof because the corresponding passage of the source report (equations (26)–(37)) contains steps that are not correct as written, although its conclusion is.

## 3. Audit of the source report

Sections 2 and 3.1–3.2 of the report (van der Corput estimates, Heath-Brown's Theorem 1 and Theorem 11.1) are correct in their conclusions. The problems are in Section 3.3, where the new claims are made.

| Statement in the report | Verdict | Reason |
| --- | --- | --- |
| Prop. 3.12 (term N^(7/8)) | True, second term vacuous | For 1 ≤ ϖ ≤ 2 one has ϖ/(4ϖ+8) ≤ 1/8 |
| Prop. 3.14 (term N^(6/7)) | True, identical in content to 3.12 | Same reason; the cap β = 5/2 is never reached |
| Remark after Prop. 3.14 | False | N^(ϖ/4) dominates only for ϖ > (1+√33)/2 ≈ 3.37 |
| Prop. 3.16 (general k) | Ill-posed | β is left free; it must satisfy β ≤ k(ϖ−1)/ϖ |
| Prop. 3.20, second range | Not proved | Non sequitur, see 3.2 below |
| Cor. 3.23, μ(11/15) ≤ 11/180 | Not proved | Depends on Prop. 3.20; gap for t^(11/48) < N < t^(1/3) |
| "Heath-Brown's 1/15 is the latest result" | Incorrect | See 3.3 below |

### 3.1 Propositions 3.12 and 3.14 carry no information beyond their first term

Both propositions assume N^(−2) ≪ λ ≪ N^(−1), that is 1 ≤ ϖ ≤ 2. In that range

```latex
\frac{\varpi}{4\varpi+8}\le\frac18\iff \varpi\le 2,
\qquad\text{so}\qquad N^{1-\varpi/(4\varpi+8)}\ \ge\ N^{7/8}\ \ge\ N^{6/7}.
```

Equivalently, the localization parameter is β = 4(ϖ−1)/ϖ ≤ 2, so a cap at 2 or at 5/2 never acts. Heath-Brown's cap at 3/2 does act, for ϖ > 8/5, and produces his term N^(8/9). The correct reading is therefore: the Guth–Maldague theorem removes the term N^(8/9) from Heath-Brown's Theorem 11.1, giving N^(1−ϖ/(4ϖ+8)+ε) on all of 1 ≤ ϖ ≤ 2. The Maldague–Oh theorem adds nothing there. The sentence "a global improvement of nearly 0.0317" should be deleted. Maldague–Oh does matter for ϖ > 2, a range the report does not consider; this is Theorem A.

### 3.2 The gap in Proposition 3.20 and Corollary 3.23

Write N = t^θ. The required bound (60) reads: the exponent of t in the estimate for the sum of n^(it) over N < n ≤ 2N is at most σ₀θ + α. In the range t^(α/(1−σ₀)) ≤ N ≤ t^(1/3) the report uses the bound N^(2/3) t^(1/12), valid for 1/4 ≤ θ ≤ 1/3, and argues: N^(2/3) t^(1/12) ≤ t^(11/36) because N ≤ t^(1/3); also N^(σ₀) t^α ≤ t^(σ₀/3+α); hence, if 11/36 ≤ σ₀/3 + α, the bound holds. Two upper bounds for two quantities do not compare the quantities. The correct condition is

```latex
\tfrac23\theta+\tfrac1{12}\ \le\ \sigma_0\theta+\alpha
\iff \theta\ \ge\ \frac{\frac1{12}-\alpha}{\sigma_0-\frac23}\qquad(\sigma_0>\tfrac23),
```

which binds at the left end of the range, not at θ = 1/3. For (σ₀, α) = (11/15, 11/180) it gives θ ≥ 1/3: the bound holds at the single point θ = 1/3. For Heath-Brown's (11/15, 1/15) it gives θ ≥ 1/4, which is why his proof works.

The interval 11/48 < θ < 1/3 is thus uncovered. Part of it can be repaired with the k = 5 case of Heath-Brown's Theorem 1, which handles 11/48 ≤ θ ≤ 1/4 and a little more. It cannot be repaired completely with the estimates in the report. At θ = 3/10:

| Estimate at N = t^(3/10) | Exponent of t |
| --- | --- |
| Needed for μ(11/15) ≤ 11/180 | 253/900 ≈ 0.28111 |
| Classical van der Corput, k = 5 | 17/60 ≈ 0.28333 |
| Heath-Brown Theorem 1, k = 4 | 17/60 ≈ 0.28333 |
| Heath-Brown Theorem 1, k = 5 | 57/200 = 0.28500 |
| Exponent pair A(13/84, 55/84) = (13/194, 76/97) | 547/1940 ≈ 0.28196 |

The number 11/180 has a simple origin. With e(θ) the best exponent from the report's tools, the function e(θ) − (11/15)θ has a local minimum at θ = 1/3, where it equals 11/36 − 11/45 = 11/180. The corollary takes the value at a local minimum for the supremum.

### 3.3 The value 1/15 is not the benchmark

Heath-Brown writes, right after his Theorem 11.2, that he does not claim the bound μ(11/15) ≤ 1/15 is new, and that it can be improved by using k = 5 for small N and exponent pairs for large N. Indeed:

| Source | Bound on μ(11/15) | Decimal |
| --- | --- | --- |
| Heath-Brown, Theorem 11.2 | 1/15 | 0.06667 |
| Classical: μ(5/7) ≤ 1/14, μ(5/6) ≤ 1/30 and convexity | 49/750 | 0.06533 |
| Tools of the report, optimized (Section 6) | 67/1050 | 0.06381 |
| ANTEDB Table 6.2 (Tao–Trudgian–Yang), read 10 Nov 2026 | 1550227/25237350 | 0.06143 |
| Claimed in Corollary 3.23 (unproved) | 11/180 | 0.06111 |

The ANTEDB value comes from the line μ(σ) ≤ 157319/560830 − (251324/841245)σ, valid for 0.7322 ≤ σ ≤ 0.8001. The claim 11/180 would beat the database; it is not established.

### 3.4 Smaller points in the proofs

- Proof of Lemma 3.5, equation (26): the point H₀ maximizing |S\_n(x)| depends on n, but is then used as if uniform in n. The fix is to keep the supremum over x until after summing over n, as in Lemma 4.1 below.
- Equation (37) and the lines after it: the step from the integral of ν^(2s/(2s−1)) to the stated bound invokes "N ≪ H^(−k(k−1)/(8s)) 2^((k−1)/(4s)) because these quantities are fixed and finite". N and H are not fixed. The correct step is Hölder's inequality between the first and second moments of ν (Step 5 of Lemma 4.1).
- Proof of Lemma 3.5: "f(n+h) = f\_n(h) + O(h^n)" should read O(λ h^k).
- Proof of Lemma 3.7: K = \[4ANλ\] can be 0; use K = 1 + \[4ANλ\].
- Theorem 2.2 is applied through Lemma 3.5, which needs Aλ ≤ 1/4; this should be stated (the theorem is trivial otherwise).

None of these affects the truth of Heath-Brown's theorems, which I take from the original papers.

## 4. The main theorem and its proof

**Theorem A.** Let A ≥ 1 and ε > 0. Let N ≥ 2 and let f : \[0, N\] → ℝ be continuous, with a continuous fourth derivative on (0, N) such that 0 < λ ≤ f⁗(x) ≤ Aλ there. Write λ = N^(−ϖ) and suppose 1 ≤ ϖ ≤ 4. Then

```latex
\sum_{n\le N}e(f(n))\ \ll_{A,\varepsilon}\ N^{E(\varpi)+\varepsilon},
\qquad
E(\varpi)=1-\frac{2-\max(1,\varpi/2)}{12-2\beta},\quad \beta=\min\Big(\frac{4(\varpi-1)}{\varpi},\frac52\Big).
```

Explicitly, E is the three-piece function displayed in Section 1. It is continuous, equals 11/12 at ϖ = 1, has its minimum 7/8 at ϖ = 2, equals 19/21 at ϖ = 8/3 and 1 at ϖ = 4.

### 4.1 The localized mean value lemma

**Lemma 4.1.** Assume (H) of Section 2. Put

```latex
\alpha^*=\frac{f^{(k-1)}(1)}{(k-1)!},\qquad \zeta=H^{1-k}+\frac{AN\lambda}{(k-1)!},\qquad
\mathfrak B=[0,1]^{k-2}\times\{u\in[0,1):\ \|u-\alpha^*\|\le\zeta\},
```

```latex
S(x;\alpha)=\sum_{h\le x}e(\alpha_1h+\dots+\alpha_{k-1}h^{k-1}),\qquad
J^*=\sup_{1\le x\le H}\int_{\mathfrak B}|S(x;\alpha)|^{2s}\,d\alpha .
```

Then for every real s ≥ 1, with 𝒩 as in Input 2,

```latex
\sum_{n\le N}e(f(n))\ \ll_k\ H+N^{1-1/s}\,\mathcal N^{1/(2s)}\,\big(H^{-2s+K}J^*\big)^{1/(2s)} .
```

*Proof.* **Step 1 (shifting).** For each integer h in \[1, H\], the sum of e(f(m)) over 1 ≤ m ≤ N equals the sum of e(f(n+h)) over 1 − h ≤ n ≤ N − h. The indices n ≤ 0 or n > N − H number exactly H. Averaging over h,

```latex
\Big|\sum_{n\le N}e(f(n))\Big|\ \le\ H+\frac1H\sum_{n=1}^{N-H}|T_n|,\qquad T_n=\sum_{h=1}^{H}e(f(n+h)).
```

**Step 2 (Taylor expansion and partial summation).** Fix n in \[1, N − H\] and set c\_j = f^(j)(n)/j!. Let B\_n be the set of α in \[0,1)^(k−1) with ‖c\_j − α\_j‖ ≤ H^(−j) for 1 ≤ j ≤ k − 1. Since H ≥ 2, its measure is exactly 2^(k−1) H^(−K). Fix α in B\_n and write c\_j = m\_j + α\_j + δ\_j with m\_j an integer and |δ\_j| ≤ H^(−j). Put

```latex
g_n(x)=f(n+x)-\sum_{j=0}^{k-1}c_jx^j,\qquad G(x)=g_n(x)+\sum_{j=1}^{k-1}\delta_jx^j .
```

For integer h the terms m\_j h^j are integers, so e(f(n+h)) = e(f(n)) · e(α\_1 h + … + α\_(k−1) h^(k−1)) · e(G(h)). By Taylor's theorem applied to f′, g\_n′(x) = f^(k)(ξ) x^(k−1)/(k−1)! for some ξ in (n, n+x). For 0 ≤ x ≤ H this gives |g\_n′(x)| ≤ Aλ H^(k−1) ≤ 1/H, because Aλ H^k ≤ 1. Also |δ\_j j x^(j−1)| ≤ j/H. Hence |G′(x)| ≤ (K+1)/H on \[0, H\]. Partial summation (Proposition 2.10 of the report) with weights e(G(h)) yields

```latex
|T_n|\ \le\ |S(H;\alpha)|+\frac{2\pi(K+1)}{H}\int_0^H|S(x;\alpha)|\,dx\qquad(\alpha\in B_n).
```

**Step 3 (averaging over α and summing over n).** Integrate the last inequality over B\_n, divide by the measure of B\_n, and sum over n. With ν(α) the number of n in \[1, N − H\] such that α lies in B\_n, and I(x) the integral of |S(x; α)| ν(α) over \[0,1)^(k−1),

```latex
\sum_{n=1}^{N-H}|T_n|\ \le\ 2^{1-k}H^{K}\Big(I(H)+\frac{2\pi(K+1)}{H}\int_0^HI(x)\,dx\Big)\ \ll_k\ H^{K}\sup_{1\le x\le H}I(x).
```

(S(x; α) vanishes for x < 1.) Note that the supremum over x is taken after the sum over n.

**Step 4 (support of ν).** If ν(α) ≠ 0 there is n with ‖α\_(k−1) − f^(k−1)(n)/(k−1)!‖ ≤ H^(1−k). By the mean value theorem |f^(k−1)(n) − f^(k−1)(1)| ≤ AλN. Hence ‖α\_(k−1) − α\*‖ ≤ ζ, so ν is supported in 𝔅.

**Step 5 (moments of ν and Hölder).** The first moment of ν is (N − H) 2^(k−1) H^(−K). The second moment is the sum over pairs (m, n) of the measure of B\_m ∩ B\_n. A nonempty intersection forces ‖c\_j(m) − c\_j(n)‖ ≤ 2H^(−j) for all j, so the second moment is at most 2^(k−1) H^(−K) 𝒩. Put q = 2s/(2s−1). By Hölder with exponents 2s and q, and then Hölder between the first and second moments (ν^q = ν^((2s−2)/(2s−1)) · ν^(2/(2s−1))),

```latex
I(x)\le\Big(\int_{\mathfrak B}|S(x;\alpha)|^{2s}d\alpha\Big)^{\frac1{2s}}\Big(\int\nu\Big)^{1-\frac1s}\Big(\int\nu^2\Big)^{\frac1{2s}}
\ \ll_k\ (J^*)^{\frac1{2s}}\,H^{-K(1-\frac1{2s})}\,N^{1-\frac1s}\,\mathcal N^{\frac1{2s}} .
```

Inserting this into Step 3 and then Step 1 gives the factor H^(−1) · H^(K/(2s)) (J\*)^(1/(2s)) = (H^(−2s+K) J\*)^(1/(2s)), which is the claim. ∎

### 4.2 Proof of Theorem A

Take k = 4, so K = 6. If N < 16A the trivial bound suffices, so assume N ≥ 16A. Since λ ≤ 1/N, we get Aλ ≤ 1/16, hence H = ⌊(Aλ)^(−1/4)⌋ ≥ 2. Since ϖ ≤ 4 and A ≥ 1, H ≤ λ^(−1/4) ≤ N. So (H) holds.

*Size of the localization.* Here ζ = H^(−3) + ANλ/6. From H ≥ (Aλ)^(−1/4)/2 we get H^(−3) ≤ 8(Aλ)^(3/4) ≤ 8ANλ, the last step because λ^(3/4) ≤ Nλ is equivalent to ϖ ≤ 4. So ζ ≤ 9ANλ. Let β = min(4(ϖ−1)/ϖ, 5/2). Then, using H ≤ λ^(−1/4) and βϖ/4 ≤ ϖ − 1,

```latex
H^{-\beta}\ \ge\ \lambda^{\beta/4}=N^{-\beta\varpi/4}\ \ge\ N^{1-\varpi}=N\lambda .
```

Thus the arc {‖u − α\*‖ ≤ ζ} has length at most 18A H^(−β) and is covered by at most 18A + 2 intervals of length H^(−β).

*The mean value.* Apply Corollary 2.1 with X = H and s = 6 − β on each of these intervals. This gives J\* ≪ H^(2s−6+ε), with a constant depending on A and ε, so H^(−2s+6) J\* ≪ H^ε ≤ N^ε.

*The counting function.* By Input 2 with k = 4, 𝒩 ≪ (N + λN² + λ^(−1/2)) log N. Since ϖ ≥ 1, λN² ≤ N, so 𝒩 ≪ N^(ν+ε) with ν = max(1, ϖ/2).

*Conclusion.* Lemma 4.1 gives

```latex
\sum_{n\le N}e(f(n))\ \ll_{A,\varepsilon}\ H+N^{\,1-\frac1s+\frac{\nu}{2s}+\varepsilon}
= H+N^{\,1-\frac{2-\nu}{12-2\beta}+\varepsilon}.
```

The three cases are as follows.

| Range of ϖ | β | 2s = 12 − 2β | ν | Exponent E |
| --- | --- | --- | --- | --- |
| 1 ≤ ϖ ≤ 2 | 4(ϖ−1)/ϖ | (4ϖ+8)/ϖ | 1 | 1 − ϖ/(4ϖ+8) |
| 2 ≤ ϖ ≤ 8/3 | 4(ϖ−1)/ϖ | (4ϖ+8)/ϖ | ϖ/2 | 1 − ϖ(4−ϖ)/(8(ϖ+2)) |
| 8/3 ≤ ϖ ≤ 4 | 5/2 | 7 | ϖ/2 | 5/7 + ϖ/14 |

Finally H ≤ N^(ϖ/4) ≤ N^(E(ϖ)): in the first two ranges ϖ/4 ≤ 2/3 < 7/8 ≤ E, and in the third 5/7 + ϖ/14 ≥ ϖ/4 is equivalent to ϖ ≤ 4. ∎

### 4.3 Remarks

**The choice of s is optimal.** For general s ≥ 1 the method gives the exponent 1 − (2−ν)/(2s) + (ϖ/4) · max(6 − β − s, 0)/(2s). For s ≥ 6 − β it increases with s. For s < 6 − β its s-dependence is ((ϖ/4)(6−β) − (2−ν))/(2s), and the numerator is positive for ϖ ≥ 1 in all three ranges, so it decreases as s grows. The minimum is at s = 6 − β.

**The range 5/2 < β < 3 does not help.** For ϖ > 8/3 one could try β = 4(ϖ−1)/ϖ in (5/2, 3) with the three-term constant of Maldague–Oh. The middle term then governs for s between (4β−3)/(2β−3) and 7/2, and the resulting exponent has s-coefficient (4−ϖ)/12 > 0, so the optimum is again s = 7/2 with the same value 5/7 + ϖ/14. A numerical search over s and β (step 0.005 in s, ϖ from 1.05 to 3.95) confirms that no choice beats E(ϖ).

**Consistency checks.** For ϖ ≤ 1 the same proof with β = 0 and ν = 2 − ϖ returns Heath-Brown's exponent 1 − ϖ/12. For f(x) = λx⁴/24 with 3 < ϖ < 4 the sum has size about λ^(−1/4) = N^(ϖ/4), which is below N^(E(ϖ)); the term H in Lemma 4.1 is therefore sharp, and the bound is consistent with this example.

**Variable coefficients.** By Remark 3.4 of Demeter–Guth–Wang, Theorem 3.3 there holds with k³ replaced by a curved phase. Whether the same is true for Input 1 in the range σ > 3/2 is not stated in the sources I read, and is not needed here.

## 5. Comparison with existing fourth-derivative tests

Theorem A is strictly better than every earlier estimate that uses only the fourth derivative exactly when 2√2 − 1 < ϖ < 4. The competitors, for λ = N^(−ϖ) and up to N^ε, are:

- classical van der Corput (Theorem 2.1 of the report, k = 4): exponent max(1 − ϖ/14, 3/4 + ϖ/14);
- Heath-Brown 2017, Theorem 1 with k = 4: exponent max(1 − ϖ/12, 11/12, 5/6 + ϖ/24);
- Heath-Brown, Theorem 11.1 in Demeter–Guth–Wang (1 ≤ ϖ ≤ 2 only): exponent max(1 − ϖ/(4ϖ+8), 8/9).

| ϖ | Theorem A | van der Corput | Heath-Brown 2017 | Heath-Brown 11.1 |
| --- | --- | --- | --- | --- |
| 1 | 0.9167 | 0.9286 | 0.9167 | 0.9167 |
| 3/2 | 0.8929 | 0.8929 | 0.9167 | 0.8929 |
| 7/4 | 0.8833 | 0.8750 | 0.9167 | 0.8889 |
| 2√2 − 1 ≈ 1.828 | 0.8806 | 0.8806 | 0.9167 | 0.8889 |
| 2 | 0.8750 | 0.8929 | 0.9167 | 0.8889 |
| 8/3 | 0.9048 | 0.9405 | 0.9444 | not applicable |
| 3 | 0.9286 | 0.9643 | 0.9583 | not applicable |
| 7/2 | 0.9643 | 1 (trivial) | 0.9792 | not applicable |

**Proposition 5.1.** (a) For 1 ≤ ϖ ≤ 3/2, Theorem A coincides with Heath-Brown's Theorem 11.1, which is the best of the three. (b) For 3/2 < ϖ ≤ 2√2 − 1 the classical van der Corput bound is the best. (c) For 2√2 − 1 < ϖ < 4, Theorem A is strictly the best. For 8/3 ≤ ϖ < 7/2 it improves the van der Corput exponent by exactly 1/28.

*Proof.* Against van der Corput. On \[3/2, 7/4\] its exponent is 1 − ϖ/14 ≤ 1 − ϖ/(4ϖ+8), since 4ϖ + 8 ≥ 14. On \[7/4, 2\] it is 3/4 + ϖ/14, and

```latex
1-\frac{\varpi}{4\varpi+8}<\frac34+\frac{\varpi}{14}\iff \varpi^2+2\varpi-7>0\iff \varpi>2\sqrt2-1 .
```

On \[2, 8/3\] the inequality 1 − ϖ(4−ϖ)/(8(ϖ+2)) < 3/4 + ϖ/14 reduces to 3ϖ² − 22ϖ + 28 < 0, true for 1.64 < ϖ < 5.69. On \[8/3, 4\] the difference is (3/4 + ϖ/14) − (5/7 + ϖ/14) = 1/28.

Against Heath-Brown 2017. On (1, 2\] its exponent is 11/12 > E. On \[2, 8/3\], E < 5/6 + ϖ/24 reduces to ϖ/(ϖ+2) > 1/3, that is ϖ > 1. On \[8/3, 4), 5/7 + ϖ/14 < 5/6 + ϖ/24 is equivalent to ϖ < 4.

Against Theorem 11.1: the exponents agree for ϖ ≤ 8/5 and E < 8/9 for 8/5 < ϖ ≤ 2. ∎

**Scope.** The gain is real but narrow in use. When the third derivative is also controlled, with λ₃ of size Nλ, the third-derivative test is stronger than any of these for ϖ near 2 and beyond; Heath-Brown makes this remark after his Theorem 11.1. Theorem A is the relevant tool when only f⁗ is known, for instance when f‴ changes sign on the interval. For polynomial phases Weyl's inequality is stronger (Section 7.3).

## 6. The zeta application

Theorem A does not improve any bound for μ(σ), and the report's tools give μ(11/15) ≤ 67/1050, not 11/180. Both statements are proved below.

### 6.1 The duality that governs the method

Write N = t^θ with 0 ≤ θ ≤ 1/2. Suppose e(θ) is a function such that, for every ε > 0, the sum of n^(it) over N < n ≤ 2N is ≪ t^(e(θ)+ε), uniformly. Then (Lemma 3.19 of the report in general form; Lemma 6.7 of the ANTEDB)

```latex
\mu(\sigma)\ \le\ \sup_{0\le\theta\le 1/2}\big(e(\theta)-\sigma\theta\big)\qquad(\tfrac12\le\sigma\le1).
```

For f(x) = (t/2π) log x on \[N, 2N\], the k-th derivative has size tN^(−k), so λ\_k = N^(−ϖ\_k) with ϖ\_k = k − 1/θ up to O(1/log N). The available exponents are:

| Tool | e(θ) | Valid for |
| --- | --- | --- |
| Trivial | θ | all θ |
| van der Corput k = 3 | θ/2 + 1/6 | θ ≤ 1/2 |
| van der Corput k = 4 | 1/14 + 5θ/7 | θ ≤ 4/9 |
| van der Corput k = 5 | 1/30 + 5θ/6 | θ ≤ 8/25 |
| Heath-Brown 2017, k = 4 | 2θ/3 + 1/12 | 1/4 ≤ θ ≤ 1/3 |
| Theorem 11.1 and Theorem A | F(θ) = θ(20θ − 3)/(24θ − 4) | 1/3 ≤ θ ≤ 1/2 (Theorem 11.1: θ ≤ 5/12) |

The validity ranges for van der Corput are those where the first term of the estimate dominates the second.

### 6.2 Theorem A is never the minimum

**Proposition 6.1.** On 0 ≤ θ ≤ 1/2, replacing Heath-Brown's Theorem 11.1 by Theorem A does not lower the minimum of the exponents in the table at any θ. Consequently it improves no bound on μ(σ) obtained by this method.

*Proof.* For θ ≤ 1/2 we have ϖ₄ = 4 − 1/θ ≤ 2, so only the first range of Theorem A occurs, and it differs from Theorem 11.1 only for ϖ₄ > 8/5, that is θ > 5/12. For θ ≥ 2/5 (ϖ₄ ≥ 3/2) we have F(θ) ≥ 1/14 + 5θ/7, as in Proposition 5.1; this covers 5/12 < θ ≤ 4/9. Next,

```latex
F(\theta)-\Big(\frac{\theta}{2}+\frac16\Big)=\frac{24\theta^2-15\theta+2}{3(24\theta-4)}\ \ge 0
\quad\text{for }\theta\ge\theta^*=\frac{15+\sqrt{33}}{48}\approx 0.4322,
```

and θ\* < 4/9, so the third-derivative exponent is at most F(θ) on \[4/9, 1/2\]. ∎

The range ϖ₄ > 2, where Theorem A is new, corresponds to N > t^(1/2). The approximate functional equation removes that range.

### 6.3 What the report's toolbox gives at σ = 11/15

**Proposition 6.2.** With e(θ) the minimum of the exponents in the table, sup (e(θ) − (11/15)θ) = 67/1050, attained at θ = 2/5. Hence μ(11/15) ≤ 67/1050 ≈ 0.06381.

*Proof.* Put Φ(θ) = e(θ) − 11θ/15 and bound it piece by piece.

| Interval of θ | Tool used | Φ(θ) is at most | Maximum on the interval |
| --- | --- | --- | --- |
| \[0, 1/5\] | trivial | 4θ/15 | 4/75 ≈ 0.0533 |
| \[1/5, 3/10\] | van der Corput k = 5 | 1/30 + θ/10 | 19/300 ≈ 0.0633 |
| \[3/10, 1/3\] | Heath-Brown 2017, k = 4 | 1/12 − θ/15 | 19/300 ≈ 0.0633 |
| \[1/3, 2/5\] | Theorem 11.1 | F(θ) − 11θ/15 | 67/1050 ≈ 0.0638 |
| \[2/5, 4/9\] | van der Corput k = 4 | 1/14 − 2θ/105 | 67/1050 ≈ 0.0638 |
| \[4/9, 1/2\] | van der Corput k = 3 | 1/6 − 7θ/30 | 17/270 ≈ 0.0630 |

On \[1/3, 2/5\] the function F is convex with F′(1/3) = 3/4 > 11/15, so F(θ) − 11θ/15 increases and its maximum is F(2/5) − 22/75 = 5/14 − 22/75 = 67/1050. A grid search over 200 000 values of θ gives the same supremum, at θ = 0.4. ∎

The point θ = 2/5 is where ϖ₄ = 3/2: Theorem 11.1 and the classical fourth-derivative test meet there, and neither Guth–Maldague nor Maldague–Oh changes the exponent at that point. This is the structural reason the decoupling improvements of 2022–2024 do not reach the zeta function through this argument.

### 6.4 Position relative to the literature

67/1050 improves Heath-Brown's illustrative 1/15 and the classical 49/750, but it is weaker than the bound ≈ 0.06143 recorded in the ANTEDB, which uses exponent pairs (Bourgain's pair and the new pairs of Tao–Trudgian–Yang). It is not a new result. To improve the database value at σ = 11/15 by this route one would need a better exponent near θ = 2/5 and near θ = 3/10 simultaneously.

## 7. Connection with algebraic geometry

The algebraic method (Weil, Deligne, Katz) and the analytic method of this report cover complementary ranges of sum length, and the algebraic method cannot repair the zeta application. This section makes the comparison explicit on the one family where both apply: f(n) = P(n)/p with P a polynomial and p a prime.

### 7.1 Complete sums as traces of Frobenius

Let p be a prime, ψ(x) = e(x/p), and P a polynomial over 𝔽\_p of degree d with 2 ≤ d < p. For b in 𝔽\_p put

```latex
S(b)=\sum_{x\in\mathbb F_p}\psi\big(P(x)+bx\big).
```

**Theorem W (Weil).** |S(b)| ≤ (d − 1)√p for every b.

In Katz's language, the Artin–Schreier sheaf ℒ = ℒ\_ψ(P(x)+bx) is lisse of rank 1 on the affine line, with Swan conductor d at infinity. The Grothendieck–Lefschetz trace formula gives S(b) = −Tr(Frob | H¹\_c), since H⁰\_c and H²\_c vanish. The Grothendieck–Ogg–Shafarevich formula gives dim H¹\_c = d − 1, and H¹\_c is pure of weight 1 (Weil for curves; Deligne in general). The d − 1 eigenvalues of absolute value √p give Theorem W.

As b varies, b ↦ S(b) is the trace function of the Fourier transform sheaf of ℒ\_ψ(P), which is lisse of rank d − 1 and pure of weight 1 on the affine line (Katz, Laumon). Two consequences matter here. First, Plancherel gives the exact mean square: the sum of |S(b)|² over b equals p². Second, by Deligne's equidistribution theorem and Katz's monodromy computations, the normalized sums S(b)/√p are distributed like traces of random elements of a compact group of size-(d − 1) matrices. So √p is the true size of S(b) for most b, and there is no hidden extra saving.

### 7.2 From complete to incomplete sums

**Proposition 7.1 (completion).** With p odd and P as above, for 1 ≤ N ≤ p,

```latex
\Big|\sum_{n\le N}e\Big(\frac{P(n)}{p}\Big)\Big|\ \le\ (d-1)\sqrt p\,(2+\log p).
```

*Proof.* Detect n ≡ x (mod p) by additive characters:

```latex
\sum_{n\le N}\psi(P(n))=\frac1p\sum_{b \bmod p}S(b)\,G(b),\qquad G(b)=\sum_{n\le N}e\Big(-\frac{bn}{p}\Big).
```

Here |G(0)| = N ≤ p, and |G(b)| ≤ 1/|sin(πb/p)| ≤ p/(2|b|) for 1 ≤ |b| ≤ (p−1)/2. By Theorem W the sum is at most (d−1)√p times N/p plus the sum of 1/b over 1 ≤ b ≤ (p−1)/2, which is at most 1 + (1 + log p). ∎

The formula in the proof is the precise link: the incomplete sum is a weighted average of Frobenius traces S(b) against the Dirichlet-type kernel G(b), which has mass on about p/N frequencies. The result is non-trivial only when N > √p (log p). Below that length, completion returns nothing, whatever is known about the sheaf.

### 7.3 Three regimes for a quartic phase

Take P(n) = n⁴ + (lower terms) and f(x) = P(x)/p, so that f⁗ = 24/p is constant and the hypothesis of Theorem A holds with A = 1 and λ = 24/p. Write N = p^(1/ϖ) up to bounded factors. The exponents of N, up to N^ε, are:

| Length of the sum | ϖ | Completion and Weil | Theorem A | Weyl's inequality |
| --- | --- | --- | --- | --- |
| p^(4/7) < N < p | 1 < ϖ < 7/4 | ϖ/2 (best) | 1 − ϖ/(4ϖ+8) | 7/8 |
| p^(1/2) < N < p^(4/7) | 7/4 < ϖ < 2 | ϖ/2 | 1 − ϖ/(4ϖ+8) | 7/8 (best) |
| p^(1/3) < N < p^(1/2) | 2 < ϖ < 3 | trivial | E(ϖ) | 7/8 (best) |
| p^(1/4) < N < p^(1/3) | 3 < ϖ < 4 | trivial | 5/7 + ϖ/14 | 1/2 + ϖ/8 (best) |

Weyl's inequality here is the classical bound N^(1+ε) (1/q + 1/N + q/N⁴)^(1/8) with q = p. Three conclusions follow.

1. For long sums, N > p^(4/7), the algebraic method wins. It gives square-root cancellation in p, which no derivative test can reach.
2. For short sums, N < p^(1/2), only analytic differencing methods give anything. Theorem A is non-trivial down to N = p^(1/4+δ), the same threshold as Weyl's inequality.
3. For a genuine polynomial, Weyl's inequality is at least as good as Theorem A for every ϖ, with equality at ϖ = 2 and ϖ = 4. Theorem A does not improve the theory of Weyl sums. Its content is that the same range of lengths is reached for any phase with a fourth derivative of constant size, with no algebraic structure.

### 7.4 Where arithmetic geometry enters the decoupling input

In the full Vinogradov mean value, the term N^(2s − k(k+1)/2) is the major-arc contribution. Around each rational point (a₁/q, …, a\_k/q) the exponential sum factors into a smooth integral and the complete sum over residues mod q of e((a₁x + … + a\_k x^k)/q), which is bounded by Theorem W for prime q. In the small cap domain \[0,1\]² × \[0, N^(−β)\] of Input 1, a rational point with third coordinate a₃/q ≠ 0 needs q ≥ N^β. For smaller q only a₃ = 0 occurs, and the complete sums are quadratic Gauss sums, of absolute value exactly √q (Theorem 1.1 of the report). So in the regime used for Theorem A the arithmetic input is Gauss's evaluation, not Weil or Deligne. This matches the remark of Maldague–Oh that for σ ≥ 3 the problem reduces to the parabola by Fubini.

### 7.5 Why this does not help the zeta function

The phase (t/2π) log n is not a polynomial modulo a prime, so no sheaf on a curve over a finite field has the sums of n^(it) as trace function. The closest algebraic analogue is p-adic: for a Dirichlet character χ modulo p^m, the map x ↦ χ(1 + px) equals e(Q(x)/p^(m−1)) for a polynomial Q coming from the p-adic logarithm (Postnikov's formula), and p^m plays the role of t. In that setting van der Corput's method has a p-adic counterpart, and a p-adic version of Theorem A is a natural question. I state this from memory of the literature (Postnikov, Gallagher, Iwaniec, and more recently Milićević and Blomer–Milićević) and did not re-verify the references for this report.

## 8. A corrected conditional statement for general k, and open questions

### 8.1 Corrected form of Proposition 3.16

Proposition 3.16 of the report leaves β free. In the method, β is not free: the localized box must contain the support of ν, which forces H^(−β) ≳ Nλ, that is β ≤ k(ϖ−1)/ϖ. With this constraint the proof of Theorem A extends verbatim to any k, under the following hypothesis.

**Hypothesis SC(k).** For 0 ≤ β ≤ k − 2, s = k(k−1)/2 − β, every integer X ≥ 1, every 1 ≤ x ≤ X and every real c, the integral of |S(x; α)|^(2s) over \[0,1\]^(k−2) × \[c, c + X^(−β)\] is ≪ X^(2s − k(k−1)/2 + ε).

This is Conjecture 2.5 of Demeter–Guth–Wang for the moment curve in dimension k − 1 (Conjecture 3.15 of the report), in the shifted and truncated form. SC(4) is a theorem by Corollary 2.1. For k ≥ 5 it is open as far as I know.

**Theorem B (conditional on SC(k)).** Let k ≥ 4, and let f satisfy 0 < λ ≤ f^(k) ≤ Aλ on (0, N) with λ = N^(−ϖ) and 1 ≤ ϖ ≤ k/2. Then

```latex
\sum_{n\le N}e(f(n))\ \ll_{A,k,\varepsilon}\ N^{\,1-\frac{\varpi}{k(k-3)\varpi+2k}+\varepsilon}.
```

*Proof.* As in Section 4.2: H is of size λ^(−1/k), ζ ≪ Nλ, and β = k(ϖ−1)/ϖ satisfies H^(−β) ≥ Nλ and β ≤ k − 2 exactly when ϖ ≤ k/2. In that range λ^(−2/k) ≤ N and λN² ≤ N, so 𝒩 ≪ N^(1+ε) by Input 2. Lemma 4.1 with s = k(k−1)/2 − β gives the exponent 1 − 1/(2s), and 2s = (k(k−3)ϖ + 2k)/ϖ. ∎

For k = 4 this is the first range of Theorem A. For ϖ = 1 it is Heath-Brown's saving 1/(k(k−1)). For k = 5 the saving runs from 1/20 at ϖ = 1 to 1/14 at ϖ = 5/2.

Even this conditional estimate does not rescue Corollary 3.23. At N = t^(3/10) one has ϖ₅ = 5/3, and Theorem B with k = 5 gives the exponent (3/10)(15/16) = 9/32 = 0.28125, still above the required 253/900 ≈ 0.28111.

### 8.2 Open questions

- Is the exponent 5/7 + ϖ/14 of Theorem A for ϖ ≥ 8/3 improvable? The only lower bound I know is the example f(x) = λx⁴/24, of size N^(ϖ/4). The loss comes from the bound 𝒩 ≪ λ^(−1/2), which uses only two of the three congruence conditions.
- Is there a fourth-derivative test with exponent below 25/28 at ϖ = 3/2? That point, not the range treated by small cap decoupling, is what limits the zeta application (Section 6.3).
- Prove SC(5), the small cap estimate for the moment curve in dimension 4, in the range 0 ≤ β ≤ 3.
- Formulate and prove the p-adic analogue of Theorem A for characters of prime-power modulus (Section 7.5).

### 8.3 Verification

Every exponent, crossover point and table entry in this report was recomputed with a short script (exact fractions where stated, a grid in θ for Proposition 6.2, a grid in s and β for Remark 4.3). The statements of Input 1 and of Heath-Brown's Theorems 11.1 and 11.2 were read from the arXiv texts on 10 November 2026. Input 2 and the original proofs behind Lemma 4.1 were not re-derived from the primary papers beyond what is written here.

## Sources

- [Maldague, Oh — On the small cap decoupling for the moment curve in ℝ³, arXiv:2411.18016](https://arxiv.org/abs/2411.18016) (Theorem 1.1)
- [Guth, Maldague — Small cap decoupling for the moment curve in ℝ³, Analysis & PDE 17 (2024)](https://msp.org/apde/2024/17-10/p04.xhtml)
- [Demeter, Guth, Wang — Small cap decouplings, with an appendix by D. R. Heath-Brown, arXiv:1908.09166](https://arxiv.org/abs/1908.09166) (Theorem 3.3, Conjecture 2.5, Theorems 11.1 and 11.2)
- [Tao, Trudgian, Yang — Analytic Number Theory Exponent Database, chapter on growth exponents of zeta](https://teorth.github.io/expdb/blueprint/zeta-growth-chapter.html) (Lemma 6.7, Tables 6.1 and 6.2)
- [Tao, Trudgian, Yang — New exponent pairs, zero density estimates, and zero additive energy estimates, arXiv:2501.16779](https://arxiv.org/abs/2501.16779)
- [Heath-Brown — Bounds for the quartic Weyl sum, arXiv:2312.14531](https://arxiv.org/abs/2312.14531) (related work on quartic Weyl sums, not used)
- D. R. Heath-Brown, A new k-th derivative estimate for exponential sums via Vinogradov's mean value, Proc. Steklov Inst. Math. 296 (2017), arXiv:1601.04493 (Theorem 1, Lemmas 2 and 3; cited through the source report and the appendix above)
- M. Garnier, Exponential sum estimates using Vinogradov Mean Value Theorem, bachelor thesis report, 2025 (the source report audited here)
- E. C. Titchmarsh, The Theory of the Riemann Zeta-function, 2nd ed., Theorems 5.9–5.14 (classical van der Corput bounds; cited from memory)
- N. M. Katz, Sommes exponentielles, Astérisque 79 (1980); Gauss sums, Kloosterman sums, and monodromy groups (1988) (background for Section 7.1; cited from memory)
