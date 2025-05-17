---
bibliography:
  - references.bib
---

# 文档撰写
讲如何生成这样一个网站



## 在 Sphinx 中加入 markdown 格式的支持，参考了下面的文献
- https://blog.csdn.net/whahu1989/article/details/140307613
- https://www.sphinx-doc.org/en/master/usage/markdown.html
- https://myst-parser.readthedocs.io/en/latest/syntax/optional.html


## 加入参考文献

https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html#known-issues-and-workarounds

This is a parenthetical citation {cite:p}`Strunk1979`.
You can also use a narrative citation with {cite:t}`Strunk1979`.
You can also use a narrative citation with {cite:p}`edwards2014kokkos`.
You can also add prefix and suffix {cite:p}`{see}Strunk1979{fig 1}`.
Also see :cite:`ma2024unconditionally`, :cite:`edwards2014kokkos`, :cite:`Strunk1979` for details.


