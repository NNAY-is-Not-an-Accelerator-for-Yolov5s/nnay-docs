# NNAY 文档

## 如何编写

首先克隆仓库：

```bash
git clone https://github.com/NNAY-is-Not-an-Accelerator-for-Yolov5s/nnay-docs.git
```

然后安装依赖：

```bash
cd nnay-docs
pip install mkdocs
```

然后运行：

```bash
mkdocs serve
```

然后访问 http://127.0.0.1:8000/ 即可查看文档。

## 如何部署

修改完成后，执行：

```bash
mkdocs gh-deploy
```

强烈建议执行前先commit，不然会把未提交的修改也部署上去。