# 文献模型复现
本工程复现了论文Evaluation of Classification algorithms for Distributed Denial of Service Attack Detection中的四种模型

## Folders:
The repository is organised as follows:

- `layers/` 定义各种层(聚合、注意力层)
- `model_zoo/` 定义模型
- `hin/` 构造异质信息网络
- `Getdata/` 数据预处理
- `utils/`　评价指标 
- `train.py`  训练模型的入口脚本
- `setting.py`  全局配置文件

## Data:
- 数据集使用的是Ember公司的开源数据集，获取地址：https://github.com/elastic/ember.git
- 预处理后会生成以下文件：
- graph.edge存放异质图所有边；graph.node存放异质图所有的节点；
- pe_export.npz,pe_imports.npz,pe_characteristics.npz,pe_dll_characteristics.npz和pe_sections.npz这些文件是存放节点邻接矩阵；
- adj_pe_export_pe.pkl,adj_pe_imports_pe.pkl,adj_pe_characteristics_pe.pkl,adj_pe_dll_characteristics_pe.pkl和adj_pe_sections_pe.pkl这些文件是存放同质图；
- feat.npz存放属性特征；
- label.json存放标签特征。

## Models：
- **GraphSage** supervised, singleview, inductive(参考GraphSage论文)
- **HANSage** supervised, multiview, inductive. 在每个metapath中独立使用**GraghSage**得到嵌入向量，最后使用Attention融合。

## Run：
``` 
python3 train.py --model GraphSage --view tpl
```
## 其他：
Windows检测系统的web端开发工程见：https://github.com/strugglingeagle/MD-system.git
