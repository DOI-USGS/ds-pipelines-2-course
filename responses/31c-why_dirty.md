#### Using which_dirty() and why_dirty() for target status of pipeline targets

In the previous comment, you may have noticed the faded color of the targets. That styling signifies that the targets are out of date ('dirty') or haven't been created yet. 

We've put some fragile elements in the pipeline that will be addressed later, but if you were able to muscle through the failures with multiple calls to `scmake()`, you likely were able to build the figure. For this example, we'll stop short of building the `"3_visualize/out/figure_1.png"` target by calling `scmake('site_data_styled')` instead. 

##### Which targets are incomplete/dirty?

The updated `remake::diagram()` output looks like this:
![image](https://user-images.githubusercontent.com/2349007/82731263-29b14900-9ccb-11ea-81ad-a35fedd09be2.png)

Only the colors have changed from the last example, signifying that the darker targets are "complete", but that `"3_visualize/out/figure_1.png"` and the two `data.csv` files don't yet exist. 

the `scipiper` package has a nice function called `which_dirty()` which will list the incomplete ('dirty') targets that need to be updated in order to satisfy the output (once again, the default for this function is to reference the `all` target in this case)

```r
which_dirty()
[1] "1_fetch/out/nwis_01427207_data.csv" "3_visualize/out/figure_1.png"       "all"                
```
This output tells us the same thing as the visual, namely that these three targets :point_up: are incomplete/dirty. 

---

##### Why are these targets dirty?

Calling `why_dirty()` on a single target 


---

:keyboard: comment on what you learned from exploring `remake::diagram()`.

<hr>
<h3 align="center">I'll sit patiently until you comment</h3>
