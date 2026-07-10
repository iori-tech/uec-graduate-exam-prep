# uec-graduate-exam-prep

電気通信大学大学院・基盤理工学専攻の一般入試対策用リポジトリです。

## ディレクトリ構成

- `analysis/`：過去問の出題傾向、難易度、予想分野の分析
- `practice/`：分野別の練習問題・解答の LaTeX ソース
- `mock_exams/`：本番形式の予想模試・解答の LaTeX ソース
- `.github/workflows/build-pdf.yml`：LaTeX ソースをコンパイルし、PDF とログを Actions の成果物として保存するワークフロー

## PDF の扱い

作成途中の PDF は通常のコミットに含めません。LaTeX ソースを push すると GitHub Actions が PDF を生成し、Actions の Artifacts に保存します。完成版を公開するときのみ、必要に応じて PDF をリポジトリまたは Releases に追加します。

## 現在の教材

- `mock_exams/basic_math/mock01/main.tex`：基礎数学 2026年度予想模試 第1回（問題・解答・採点基準）

## ローカルでのコンパイル

日本語 TeX Live 環境で、リポジトリのルートから次を実行します。

```bash
mkdir -p build/local
uplatex -interaction=nonstopmode -halt-on-error -output-directory=build/local mock_exams/basic_math/mock01/main.tex
uplatex -interaction=nonstopmode -halt-on-error -output-directory=build/local mock_exams/basic_math/mock01/main.tex
dvipdfmx -o build/local/mock01.pdf build/local/main.dvi
```

## GitHub Actions の成果物

Actions の各実行ページに、次の成果物が保存されます。

- `compiled-pdfs`：生成に成功した PDF
- `latex-build-logs`：各 TeX ファイルのコンパイルログ
