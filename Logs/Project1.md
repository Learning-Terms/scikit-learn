# 学习 Scikit-learn 的详细路径
##  📌 第 0 阶段：准备环境

```bash
# 克隆项目
git clone https://github.com/scikit-learn/scikit-learn.git
cd scikit-learn

# 创建虚拟环境并安装依赖
conda create -n sklearn-dev python=3.10 -y
conda activate sklearn-dev
pip install -r requirements.txt
pip install -e .
```

💡 -e . 是以开发模式安装，方便你本地修改代码后即时生效。

## 📌 第 1 阶段：理解基本结构
学习仓库目录结构，重点理解：

```text
/sklearn           # 所有核心源码
/sklearn/tests     # 各模块的测试代码
/doc               # Sphinx 生成文档目录
/examples          # 示例代码
```

## 📌 第 2 阶段：动手运行项目代码

```bash
# 进入 examples 子目录，运行一两个入门示例
cd examples/classification
python plot_classifier_comparison.py
```
在 Jupyter Notebook 中运行更方便，可以使用 VS Code 的 Python 插件。

## 📌 第 3 阶段：阅读核心源码模块
推荐从这几个开始读起（都是经典机器学习算法）

```bash
/sklearn/tree/decision_tree.py       # 决策树
/sklearn/ensemble/random_forest.py   # 随机森林
/sklearn/linear_model/logistic.py    # 逻辑回归
```

- 看每个类的 __init__，fit，predict 方法;
- 阅读注释 + 文档字符串（docstring）;

## 📌 第 4 阶段：文档 typo 修复与 PR 提交流程（简单！）

- 找一个文档中的拼写错误或表达不清之处（doc/ 中 .rst 文件或源码中的 docstring 都可以）
- 修改 typo（例如把 simlar 改为 similar）
- 提交修改：

```bash
git checkout -b fix-typo-doc
# 编辑相关文件
git add .
git commit -m "DOC: fix typo in decision_tree.py"
git push origin fix-typo-doc
```
- 打开 GitHub，创建 Pull Request（PR）

## 📌 第 5 阶段：参与测试代码改进（初学者友好）
Scikit-learn 使用 pytest 测试框架。你可以做：
- 阅读 sklearn/tests/ 中的测试
- 添加断言或改进测试覆盖率

比如：
📄 sklearn/tests/test_decision_tree.py
你可以添加一段：

```
def test_fit_predict_consistency():
    clf = DecisionTreeClassifier()
    X = [[0, 0], [1, 1]]
    y = [0, 1]
    clf.fit(X, y)
    assert clf.predict([[1, 1]])[0] == 1
```

然后运行所有测试：

```bash
pytest sklearn/tests
```

## 📌 第 6 阶段：参与社区，扩大影响力
- 🌍 浏览 [issues](https://github.com/scikit-learn/scikit-learn/issues) 页面
  - 过滤 good first issue 标签
- 🧠 阅读并参与讨论
- 💬 提出你自己的 issue 或使用改进建议

## 🏁 Bonus：Scikit-learn 的 PR 模板（官方非常专业）

你提交 PR 时，需要填写：

```markdown
#### What does this implement/fix?
Fix typo in class docstring.

#### Any other comments?
N/A
```

## 🧭 总结学习路径一览
| 阶段         | 内容                         | 成果                         |
|--------------|------------------------------|------------------------------|
| 0 环境准备   | clone + conda + pip          | 本地可运行                   |
| 1 结构学习   | 理解 sklearn 模块目录结构     | 知道代码在哪、测试在哪       |
| 2 示例实践   | 跑 examples/classification    | 理解典型算法使用方法         |
| 3 源码阅读   | 看逻辑回归/决策树等核心算法   | 能够解释 fit/predict 流程    |
| 4 文档 PR    | 改一个 typo，推送 PR         | 获得第一个开源成就 🛠️        |
| 5 测试改进   | 改进单元测试逻辑             | 学会写断言 / 使用 pytest     |
| 6 社区互动   | 回答 issue / 提问            | 展现参与度，积累信誉         |

## 
