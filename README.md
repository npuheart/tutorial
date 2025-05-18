SimCardiac 文档, 参考自 pyvista tutorial. 还没完全替换掉pyvista的内容。

rm -r doc/build && \
make -C doc html SPHINXOPTS="-W --keep-going" && \
python -m http.server 8000 --directory doc/build/html --bind 0.0.0.0