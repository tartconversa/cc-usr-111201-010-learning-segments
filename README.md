# 混合教学指标的群体分型与稳定性

本项目保存高校公共算力与教学研究的虚构汇总资料和Python读取工具。现有工具仅解析输入并显示类型与记录数，不执行统计计算、优化、拟合或训练。样本不代表真实高校、个人或教学成效。

## 资料口径

每行是课程学期汇总，tokens_per_student为数值、review_rate为比例、format为无序类别、stage为有序等级。空值缺失，院系为稳定性重采样单元，不直接进入距离。

fixtures为只读资料目录，src/segment_reader.py为现有读取器，material-index.json记录文件内容摘要。研究结果可以放入独立.workspace-output目录，不要覆盖原始数据。

## 运行与开发

Python 3.11及以上版本；现有读取器只用标准库，无安装步骤。进入项目根目录：

    python -m src.segment_reader fixtures/course_metrics.csv

编译检查：

    python -m compileall -q src tests

输入契约测试：

    python -m unittest discover -s tests -v

## 容器环境

    docker build -t learning-segments:local .
    docker run --rm learning-segments:local

镜像按完整摘要固定，默认执行读取测试。容器不需要访问外部教学平台。
