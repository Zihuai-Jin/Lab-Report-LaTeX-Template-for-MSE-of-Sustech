# 模板核对记录

核对日期：2026-11-16。

依据用户确认，采用原工作区的 **Lab Report template.doc**，而非相邻目录中的 DOCX。通过 `textutil` 提取其文本及转换后的段落格式，核对章节、封面字段、字号、颜色、对齐方式与页面设置；对最终 LaTeX PDF 的六页分别渲染并检查。

## 与参考文件的对应

| 参考要求 | 模板处理 | 核对结果 |
| --- | --- | --- |
| 学校、院系 | 封面顶部左对齐，15 pt 加粗 | 已包含 |
| 课程名称 | 居中、蓝色 `#0070C0`、18 pt 加粗 | 已包含 |
| Lab Report | 居中、28 pt 加粗 | 已包含 |
| 实验编号及名称 | 居中、22 pt 加粗，改为可填写字段 | 已包含 |
| 姓名、学号、组员、实验日期、提交日期 | 右对齐信息区，15 pt 加粗；清空真实信息 | 五项齐全 |
| Objectives | 第 1 节，目的填写说明及列表 | 一致 |
| Principles | 第 2 节，原理说明及可替换公式 | 一致 |
| Experimental (Materials and Apparatus) | 第 3 节，材料和仪器两个小节 | 一致 |
| Experimental procedure | 第 4 节，步骤填写说明及列表 | 一致 |
| Results and discussion | 第 5 节，强调重要性，含图表、计算和误差分析说明 | 一致 |
| Conclusion | 第 6 节，强调重要性，说明应总结哪些内容 | 一致 |
| Questions | 第 7 节，强调重要性，提供问题与答案字段 | 一致 |
| References (if you have) | Questions 之后的非编号参考文献，含可替换条目及引用示例 | 一致；删除方法见 README |
| 报告末尾附 datasheet | 最后一页为 Original datasheet 附录 | 已包含 |
| 页面设置 | US Letter；左右 1.25 英寸，上下 1 英寸 | 与读取到的 DOC 页面设置一致 |

封面用可编辑 LaTeX 文本重建。字号、颜色和对齐方式按参考文件设置；段间留白按新占位文本调整，不声明与 Word 页面逐像素一致。正文采用 12 pt Times New Roman，并在缺少该字体时回退到 TeX Gyre Termes。

## 实际验证

- 仅复制 `template.tex` 和 `fig/` 到独立临时目录，使用 TeX Live 2026 的 `latexmk -norc -xelatex -interaction=nonstopmode -halt-on-error template.tex` 完整编译，退出码为 0。
- 最终日志无 LaTeX 警告、缺字、未定义引用、Overfull 或 Underfull 信息；PDF 生成阶段无重复页面锚点警告。
- 预览共 6 页：封面 1 页、正文及参考文献 4 页、数据表附录 1 页。已逐页检查，无裁切、重叠或缺失图片；Fig D 保持在结果与讨论之后、结论之前。
- 图像目录恰含四张真正的 JPEG：`fig_A.jpg`、`fig_B.jpg`、`fig_C.jpg`、`fig_D.jpg`，均为 1600 × 1000 像素。主文件仅引用这四张图，不依赖父目录的图片或 PDF。
- 章节名称和顺序与上表一致；图、表、公式及文献引用均已解析。
- 对模板源码与提取的 PDF 文本扫描，未发现原姓名、学号、组员、实验日期及原聚合物实验专用内容。示例图均为文字占位图，不包含测量数据。
- 原始 `7.tex` 与参考 DOC 的 SHA-1 在处理前后保持一致。
- `article_tmp` 中仅保留模板、预览、四张 JPG、说明、核对记录及 `.gitignore`；编译缓存与页面检查图保存在临时目录。

该核对确认的是可复用模板的结构、依赖和显示结果。实际填写后仍须重新检查内容、分页、原始数据附件及课程当次要求。
