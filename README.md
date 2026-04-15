# Windowsでも実行可能な遺伝育種研究のための
# Bioinfomatics環境の構築

  ##  著者：清水誉生., 菊池潔., 細谷将.,

# 緒言
---
 近年、ゲノム解析の飛躍的な発展に伴い作物や畜産、養殖など幅広い分野でゲノム情報を活用した研究が展開されている。とくに一塩基多型（single nucleotide polymorphism, SNP）のハイスループットジェノタイピングは多くの生物で大規模な多型解析を可能とし、家系管理や、ゲノム選抜育種（Genomic selection, GS）法の普及とその導入による選抜育種の飛躍的な効率化に貢献している。また、ゲノム選抜育種で育種価予測を行うためのBioinformatics用の解析ツールも数多く開発されている。一方で、これらの解析ツールの多くはLinux OS上での利用を前提として開発されており、
- コマンドライン操作

- バージョンや依存関係の統合

- 「どこに何をインストールしたか」「使用したバージョンは何か」といった管理作業
 
 などがバイオインフォマティクス初心者には障壁となり、普及の妨げになっている。

 このような背景を踏まえBioinformatics解析の導入、実行、管理を容易にするため、Dockerを利用したゲノム選抜育種向けの解析環境をの構築を提案した。

# 目的
---
- 1. Dockerを使用し簡便かつ利便性の高い解析環境を構築し遺伝育種の普及性を向上させること
- 2. 作成した解析環境の動作確認ならびにDocker環境とDockerを介さないローカル環境との間で処理性能を比較し、ゲノム選抜育種の解析パイプラインとしての有用性を評価すること

# 方法 1
---
## 1. WSL2のセットアップ
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-1.%20WSL2%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97.md

## 2. Dockerのインストール
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-2.%20Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.md

## 3. Dockerfileの作成からコンテナの起動までの操作方法
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-3.%20Dockerfile%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%8B%E3%82%89%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E8%B5%B7%E5%8B%95%E3%81%BE%E3%81%A7%E3%81%AE%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95.md

## 4. Dockerfile解説
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-4.%20Dockerfile%E8%A7%A3%E8%AA%AC.md

# 方法 2
---
## 1.動作確認
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/2-1%E5%8B%95%E4%BD%9C%E7%A2%BA%E8%AA%8D.md
## 2.処理性能の比較
https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/2-2%E5%87%A6%E7%90%86%E6%80%A7%E8%83%BD%E3%81%AE%E6%AF%94%E8%BC%83.md

