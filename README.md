# Battery Projects — Week 1 to 5

锂离子电池 1D 单体尺度热-电化学分层建模与验证（5周递进课程作业）

## 项目结构

| 周次     | 目录                        | 物理层                | 核心文件                     |
| ------ | ------------------------- | ------------------ | ------------------------ |
| Week 1 | `week1_cycling/`          | 宏观循环老化经验分析         | `cycling_analysis.ipynb` |
| Week 2 | `week2_dfn/`              | Newman DFN 反应-传输   | `dfn_model.ipynb`        |
| Week 3 | `week3_nernst_planck/`    | Nernst-Planck 离子迁移 | `nernst_planck.ipynb`    |
| Week 4 | `week4_particle_size/`    | 颗粒粒径分布 + 固相扩散      | `particle_size.ipynb`    |
| Week 5 | `week5_thermal_coupling/` | 热-电化学双向耦合（物理天花板）   | `thermal_coupling.ipynb` |

每个子目录包含：

- `.ipynb` 源码
- `week*_output/` 输出图与数据
- 子目录内 `README.md`（详细运行说明与参数）

## 快速开始

bash

1. 安装依赖     
   pip install numpy scipy matplotlib pandas jupyter
2. 启动 Jupyter     
   jupyter lab     
   运行顺序：按 Week 1 至 Week 5 逐周打开对应目录下的 notebook，Cell 1→5 顺序执行。

## 关键结论

- **建模递进**：从宏观经验老化 → DFN 反应传输 → 离子迁移 → 颗粒固相扩散 → 热-电化学双向耦合。
- **物理天花板**：Week 5 实现 1D 单体尺度热-电化学耦合（反应产热→升温→Arrhenius 加速→产热放大正反馈）。
- **稳态验证**：稳态温升满足 $\Delta T = \dot{q}/h_{\text{vol}}$，C-rate 线性缩放；10 cm 单元尺度下体积散热等效正确刻画全表面换热。

## 学术报告

- 英文版：`REPORT.md`（若存在请按实际文件名修改）
- 中文版：`REPORT_CN.md`（若存在请按实际文件名修改）

## 提交与版本管理

按“每周一个 commit”推至 GitHub 仓库：  
`https://github.com/MaWangxuan/battery_projects.git`

## 作者

Ma Wangxuan · [替换学校邮箱] · 2026-10
