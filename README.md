# statedrift

**检查智能体内部状态与外部事实是否还一致。**

`statedrift` —— 比对状态快照与后端实际状态，标出已经失真的字段

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`statedrift.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install adsayi-statedrift
```

装完直接用命令名调用：

```bash
statedrift --help
```

也可以不用安装，直接把 `statedrift.py` 拷走用——它只依赖标准库。

## 为什么需要它

重点是「多久没同步」而不是「同不同步」

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 智能体状态漂移 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python statedrift.py --file input.txt
python statedrift.py --text "示例内容"
python statedrift.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 一致性靠字面差异判定，语义等价但写法不同会误报。
- 不解析跨文档的引用关系。

## 跑测试

```bash
python test_statedrift.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/adsayi/statedrift>

---

## 关于作者

adsayi 做智能体状态漂移相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://adsayi.github.io>
- 仓库：<https://github.com/adsayi/statedrift>

## 许可

MIT，见 [LICENSE](LICENSE)。
