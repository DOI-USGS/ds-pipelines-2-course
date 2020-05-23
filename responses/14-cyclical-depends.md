#### What are cyclical dependencies and how to avoid them?
The `remake` package has a nice function called `diagram()` that we haven't covered yet. It produces a dependency diagram for the target(s) you specify (remember that `all` is the default target). For the initial example in your repo, it looks like this
```r
remake::diagram()
```

![image](https://user-images.githubusercontent.com/2349007/82158949-afa73d00-9850-11ea-906c-92c1e71bb7a6.png)

Note the arrows capturing the dependency flow, and how `site_data` sits at the top, since it is the first target that needs to be built. 

Also note that there are no backward looking arrows. What if `site_data` relied on `site_data_styled`? In order to satisfy that relationship, an arrow would need to swing back up from `site_data_styled` and connect with `site_data`. Unfortunately, this creates a [cyclical dependency](https://en.wikipedia.org/wiki/Circular_dependency) since changes to one target change the other target and changes to that target feed back and change the original target...so on, and so forth...

This potentially infinite loop is confusing to think of and also something that dependency managers can't support. We won't say much more about this issue here, but note that in the early days of building pipelines if you run into a cyclical dependency error, this is what's going on. 

---

:keyboard: Add a comment when you are ready to move on.  

<hr>
<h3 align="center">I'll sit patiently until you comment</h3>
