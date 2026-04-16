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
-  Dockerを使用し簡便かつ利便性の高い解析環境を構築し遺伝育種の普及性を向上させること


# 方法 
---
## 1. [WSL2のセットアップ](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-1.%20WSL2%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97.md)


## 2. [Dockerのインストール](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-2.%20Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.md)


## 3. [Dockerfileの作成からコンテナの起動までの操作方法](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-3.%20Dockerfile%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%8B%E3%82%89%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E8%B5%B7%E5%8B%95%E3%81%BE%E3%81%A7%E3%81%AE%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95.md)


## 4. [Dockerfile解説](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-4.%20Dockerfile%E8%A7%A3%E8%AA%AC.md)


# ゲノムデータの取得
---
本研究では、Linらの研究で使用されたトラフグ（_Takifugu rubripes_）のアンプリコンシーケンスのデータを使用している。これらはDDBJにアーカイブされており二次利用が可能となっている。

Linuxで下記のコマンドを実行することで入手可能
```
seq 0 239 | xargs -n 1 -P 8 -I {} bash -c '
  drx=$(printf "DRX%06d" $((223812 + {})))
  drr=$(printf "DRR%06d" $((233598 + {})))
  wget https://ddbj.nig.ac.jp/public/ddbj_database/dra/fastq/DRA010/DRA010341/${drx}/${drr}_1.fastq.bz2
'
```
```
seq 0 239 | xargs -n 1 -P 8 -I {} bash -c '
  drx=$(printf "DRX%06d" $((223812 + {})))
  drr=$(printf "DRR%06d" $((233598 + {})))
  wget https://ddbj.nig.ac.jp/public/ddbj_database/dra/fastq/DRA010/DRA010341/${drx}/${drr}_2.fastq.bz2
'
```

続いてリファレンスゲノムのダウンロードは下記のコマンドを実行する
```
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/180/615/GCF_000180615.1_FUGU5/GCF_000180615.1_FUGU5_genomic.fna.gz
```


