# 这是一个markdown文档


## 在 Sphinx 中加入 markdown 格式的支持，参考了下面的文献
- https://blog.csdn.net/whahu1989/article/details/140307613
- https://www.sphinx-doc.org/en/master/usage/markdown.html
- https://myst-parser.readthedocs.io/en/latest/syntax/optional.html

This is a parenthetical citation {cite:p}`Strunk1979`.
You can also use a narrative citation with {cite:t}`Strunk1979`.
You can also use a narrative citation with {cite:p}`Strunk1979`.
You can also add prefix and suffix {cite:p}`{see}Strunk1979{fig 1}`.

.. toctree::
   :maxdepth: 2
   :caption: Lessons
   :hidden:

   tutorial/00_jupyter/index
   tutorial/05_action/index
   tutorial/10_poroelasticity/index