# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.


## Answer

The reccurence relation I found is $$T(n) = 3T\left(\frac{n}{3}\right) + n^5$$. And i=log<sub>3</sub>n.

I found this recurrence relation from the three instances of $$\frac{n}{3}$$ , and the three for loops, two having $$n^2$$ time and one having n time.

$$T(n) = 3[3T\left(\frac{n}{3^2}\right) + (\frac{n}{3})^5] + n^5$$

$$T(n) = 3^2T\left(\frac{n}{3^2}\right) + (\frac{n}{3^4})^5 + n^5$$

$$T(n) = 3^3T\left(\frac{n}{3^3}\right) + (\frac{n}{3^8})^5+ (\frac{n}{3^4})^5 + n^5$$

I can see the following pattern:

$$3^iT(\frac{n}{3^i}) + \sum_{i=0}^n\frac{n^5}{3^{4^i}}$$, and *i=log<sub>3</sub>n*

$$3^{log_3n}T(\frac{n}{3^{log_3n}}) + n^5 * (\frac{1}{3})^{4^{log_3n}}$$

$$n*T(1) + n^5 * \frac{1}{1-\frac{1}{3}}$$

$$n^5 ∈ O(n^5)$$

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
