# 南方科技大学材料系实验报告 LaTeX 模板

仓库中的 LaTeX 模板由个人制作与整理，报告模板是本人在实际课程中使用过的版本，现将其中的个人信息、实验数据和具体报告内容替换为填写说明与占位内容，供参考使用。截止2026年春季，当前仓库模板在材料系的材科专业与光电专业的综合实验课中通用。

需要说明的是，**封面是在实验课程结束后，才由AI制作并添加到 TeX 文件中的**。实际课程中使用过的是报告模板，当前版本新增的封面不属于当时实际使用的部分。

## 模板目录

| 目录 | 内容 |
| --- | --- |
| [Fundamental_Experiments](Fundamental_Experiments/) | 材料科学与工程基础实验报告模板 |
| [Comprehensive_Experiment_1](Comprehensive_Experiment_1/) | 材料综合实验（一）报告模板 |
| [Comprehensive_Experiment_2](Comprehensive_Experiment_2/) | 材料综合实验（二）报告模板 |

各目录包含主文件 `template.tex`、预览文件 `template.pdf`、图片目录 `fig`和编译配置 `.latexmkrc`。

## 安装 LaTeX 环境

完整安装 TeX Live 或 MacTeX（通常已包含 XeLaTeX 和 `latexmk`）。

**Ubuntu / WSL2 Ubuntu**：在终端安装完整 TeX Live 和 `latexmk`：

```sh
sudo apt update
sudo apt install texlive-full
```

完整安装需要较多下载流量和磁盘空间。

**macOS**：已安装 Homebrew 时，可通过以下命令安装完整 MacTeX（包含 XeLaTeX 和 `latexmk`）：

```sh
brew install --cask mactex
```

安装完成后，检查编译工具是否可用：

```sh
xelatex --version
latexmk -v
```

## 编译方法

当前模板已在 Ubuntu 的 TeX Live 和 macOS 的 MacTeX 环境中尝试编译并成功。Windows 上推荐使用 WSL2 的 Ubuntu 环境，安装 TeX Live 后按以下方式编译。

三个模板统一使用 **XeLaTeX**。安装好上述环境后，进入所选课程的模板目录，执行：

```sh
latexmk -xelatex -interaction=nonstopmode -halt-on-error template.tex
```

每个模板目录的 `.latexmkrc` 均将默认引擎设为 XeLaTeX，因此在模板目录内也可直接执行 `latexmk template.tex`。编译后会生成或更新该目录的 `template.pdf`。

未安装 `latexmk` 时，连续执行两遍以下命令，以解析交叉引用和参考文献：

```sh
xelatex -interaction=nonstopmode -halt-on-error template.tex
```

使用 Overleaf 时，上传所选模板目录，将 `template.tex` 设为主文件，编译器选择 **XeLaTeX**。尚未单独验证 Overleaf 环境。

模板优先使用 Times New Roman，未安装时回退至 TeX Gyre Termes；正式提交时请使用课程要求的字体。

## VS Code 工作区配置

[`.vscode/settings.json`](.vscode/settings.json) 中的 LaTeX Workshop 设置及 `[latex]` 编辑器设置仅对当前工作区生效，不修改全局配置。使用时请在 VS Code 中打开本仓库根目录，并安装 **LaTeX Workshop** 扩展（`James-Yu.latex-workshop`）；LaTeX 编译环境仍需按上文单独安装。

## 填写说明

1. **封面**：修改 `template.tex` 顶部的课程、实验编号与名称、姓名、学号、组员、日期等字段；如模板包含班级和名单序号，也需填写。
2. **正文**：用实际实验内容替换英文写作说明及方括号中的占位文字，按课程要求完成各节，重点写清结果、讨论、误差分析、结论和问题回答。
3. **图表与公式**：用自己的图片替换 `fig` 目录中的占位图；更改文件名时同步修改 `\includegraphics`。替换示例公式和表格，补全图题、表题、单位与误差说明。
4. **文献与附件**：替换示例参考文献并更新引用，删除未使用的示例；按课程要求附上预习报告和原始数据记录，具体方法见 TeX 文件中的注释。
5. **提交前检查**：重新编译并逐页查看 `template.pdf`，确认占位内容已替换，分页、图表、公式、引用和个人信息无误，并按课程要求命名及提交。

报告模板正文默认使用英文。基础实验模板已配置中文姓名支持；综合实验模板如需输入中文，请先配置合适的中文支持宏包和字体。各课程的具体格式与提交要求以任课教师当学期的要求为准。

## 注意事项

本仓库为个人整理的课程报告模板，并非学校或院系发布的官方模板。封面及格式参考了相应课程的要求与参考材料；实际使用时，请以任课教师当学期的要求为准，并按需调整。

## 许可证

本项目采用 [MIT 许可证](Licence)，允许使用、复制、修改、分发及商业使用。分发本项目的副本或实质性部分时，须保留原版权声明和许可声明。模板按现状提供，不附带任何担保，完整条款见许可证文件。
