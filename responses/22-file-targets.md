File targets are very flexible and of course, are also easy to share or store elsewhere. 

Additionally, many targets are either language agnostic (e.g., csv, tsv, txt, nc files) _or_ are meant to be shared across languages, such as the [feather file](https://blog.rstudio.com/2016/03/29/feather/)

When specifying a target in a remakefile recipe withg file targets, the path to the file needs to be either absolute or relative to the working directory that the `remake.yml` file is in. 

Most of the guidance you'd see on the [remake package](https://github.com/richfitz/remake) whould steer you away from using files as targets, since the benefits are quite small. In fact, one of the edits I made to the background on target types that was borrowed from `remake` was to remove the statement "With remake though, [file targets] should probably only be the beginning or end points of an analysis", which is referring to the end products of a pipeline likely being figures, tables, markdown files, or documents (all files) and encouraging all other targets to be objects. Instead, we recommend that files be used more liberally than objects because of two reasons: 1) ability to store data remotely in file format, and 2) ease of collaboration. The justification for this will become clearer in our intermediate pipelines courses. 

---
:keyboard: Activity: Close this issue when you are ready to move on to the next assignment

<hr>
<h3 align="center">I'll sit patiently until this issue is closed.</h3>