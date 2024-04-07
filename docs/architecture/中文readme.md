# Process for updating the backend architecture diagram 处理更新后端架构图的过程

The generation of the backend architecture diagram is partially automated. The diagram is generated from the type hints in the code using the py2puml tool. The diagram is then manually reviewed, adjusted and exported to PNG and SVG.

`backend architecture`后端架构图的生成是`partially automated`部分自动化的。该图是使用 py2puml 工具从代码中的类型提示生成的。然后手动审查、调整并导出为 PNG 和 SVG。

## Prerequisites 先决条件

- Running python environment in which opendevin is executable (according to the instructions in the README.md file in the root of the repository)
- [py2puml](https://github.com/lucsorel/py2puml) installed

- 运行 Python 环境，其中 opendevin 是可执行的（根据存储库根目录中 README.md 文件中的说明）
- 已安装 [py2puml](https://github.com/lucsorel/py2puml)

## Steps 步骤

1. Autogenerate the diagram by running the following command from the root of the repository:  
```py2puml opendevin opendevin > docs/architecture/backend_architecture.puml```

2. Open the generated file in a PlantUML editor, e.g. Visual Studio Code with the PlantUML extension or [PlantText](https://www.planttext.com/)

3. Review the generated PUML and make all necessary adjustments to the diagram (add missing parts, fix mistakes, improve positioning).  
*py2puml creates the diagram based on the type hints in the code, so missing or incorrect type hints may result in an incomplete or incorrect diagram.*

4. Review the diff between the new and the previous diagram and manually check if the changes are correct.  
*Make sure not to remove parts that were manually added to the diagram in the past and are still relevant.*

5. Add the commit hash of the commit that was used to generat the diagram to the diagram footer.

6. Export the diagram as PNG and SVG files and replace the existing diagrams in the `docs/architecture` directory. This can be done with (e.g. [PlantText](https://www.planttext.com/))

- 将以下命令从`root of the repository`存储库的根目录运行以`Autogenerate the diagram`自动生成图表：
```py2puml opendevin opendevin > docs/architecture/backend_architecture.puml```
- 在 PlantUML 编辑器`PlantUML editor`中打开生成的文件，例如 Visual Studio Code 与 PlantUML 扩展或 [PlantText](https://www.planttext.com/)
- 查看生成的 PUML 并对图表进行所有必要的调整（添加缺失部分，修复错误，改进定位）。*py2puml 根据代码中的类型提示创建图表，因此缺少或不正确的类型提示可能导致不完整或不正确的图表。*
- 查看新图表和以前图表之间的差异，并手动检查更改是否正确。*确保不要删除过去手动添加到图表中的仍然相关的部分。*
- 将用于生成图表的提交哈希添加到图表页脚。
- 将图表导出为 PNG 和 SVG 文件，并替换 `docs/architecture` 目录中的现有图表。可以使用（例如 [PlantText](https://www.planttext.com/)）
