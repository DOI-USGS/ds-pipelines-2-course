In general, if building part of a pipeline is "expensive" (i.e., takes more than a trivial amount of time for a computer to execute), it should be a target. In the example above :point_up:, expensive sections included fetching data and plotting. 

Additional reasons to create a target include:
- If some element in the pipeline may fail (such as downloading data from the internet), isolating the this brittle part of the project as a target with a corresponding function makes it faster to get past. This is because your target focuses on accomplishing _only_ the brittle step, instead of, for example, also attempting to process and plot downloaded data all within the same function.
- Sometimes a target is created in order to make it easier to defer a decision for later. If we have an expensive geoprocessing task but the final way we summarize results is in flux, it might make sense to break this function and target into two things: the major parts of the geoprocessing step in one, and the smaller summary process in the second target. 
- Targets are easy to inspect and dig into (e.g., `my_target <- scmake('my_target')). If there is an intermediate step in a workflow that should be examined, it may deserve a target.
- Lastly, if a configuration or value is shared accross many other targets, the configuration itself might deserve a stand alone target, even if generating that target is computationally cheap. In our water quality data pull example, the `wqp.config` target is an example of a shared configuration. Within that target, there is (among other things) a string that specifies how lake sites are queried in the web service. If that query parameter changes in the future, making the change to the file behind the `wqp.config` would propagate into the necessary updates to the data pulls run with `get_wqp_data`.

---

But of course there is a cost to creating many targets: you'll end up typing a lot more, a lot of additional files will be created that need to be stored, and adding more targets makes it is harder to navitate the `remakefile`.


:keyboard: Activity: Make modifications to the working, but not ideal, pipeline that exists within your course repository

Within the course repo you should see only a `remake.yml` and directories with code or placeholder files for each phase. You should be able to run `scmake` and build the pipeline, although it may take a couple of tries, since some parts of this new workflow are brittle. Some hints to get you started: one of these targets is too big, and you should consider splitting it. Several of these targets are too small and it might make sense to combine them. 

When you are happy with your newer, better workflow, create a pull request with your changes and assign Jordan or Alison as reviewers. Add a comment to your own PR with thoughts on how you approached the task, as well as key decisions you made. See details below for some reminders of how to get started working with code and files that exist within the course repsository:


Open a git bash shell (Windows) or a terminal window (Mac) and change (`cd`) into the directory you work in for projects in R (for me, this is `~/Documents/R`). There, clone the repository and set your working directory to the new project folder that was created:
```
git clone git@github.com:{{ user.username }}/{{ repo }}.git
cd ds-pipelines-2
```

Now you should create a local branch called "targets" and push that branch up to the "remote" location (which is the github host of your repository). We're naming this branch "targets" to represent concepts in this section of the lab. In the future you'll probably choose branch names according to the type of work they contain - for example, "pull-oxygen-data" or "fix-issue-17".

```
git checkout -b targets
git push -u origin targets
```

<hr>
<h3 align="center">A human will interact with your pull request once you assign them as a reviewer</h3>




