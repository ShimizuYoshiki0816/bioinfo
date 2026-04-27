# Windowsでも実行可能な遺伝育種研究のためのBioinfomatics環境の構築

###  著者：清水 誉生, 菊池 潔, 細谷 将

## はじめに
---
近年、ゲノム解析の飛躍的な発展に伴い、農業・畜産業・養殖業など幅広い分野でゲノム情報を活用した研究が展開されている。特に、一塩基多型（single nucleotide polymorphism, SNP）のハイスループットジェノタイピングは多くの生物で大規模な多型解析を可能とし、家系管理、ゲノム選抜育種（Genomic selection, GS）法の導入、およびそれに伴う選抜育種の飛躍的な効率化に貢献している。また、ゲノム選抜育種における育種価予測を行うためのBioinformatics解析ツールも数多く開発されている。一方で、これらの解析ツールの多くはLinux OS上での利用を前提として開発されており、(i)コマンドライン操作、(ii)バージョンや依存関係の統合、(ⅲ)インストールしたソフトの管理などがバイオインフォマティクス初心者にとって障壁となっている。

そこで本ページでは、Bioinformatics解析の導入・実行・管理を容易にすることを目的とした、ゲノム選抜育種向けのDocker解析環境を提供する。

## 目的
---
###  Dockerを使用し簡便かつ利便性の高い解析環境を構築し遺伝育種の普及性を向上させること


## 方法 
---
### 1. [WSL2のセットアップ](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-1.%20WSL2%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97.md)


### 2. [Dockerのインストール](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-2.%20Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.md)


## 3. [Dockerfileの作成からコンテナの起動までの操作方法](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-3.%20Dockerfile%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%8B%E3%82%89%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E8%B5%B7%E5%8B%95%E3%81%BE%E3%81%A7%E3%81%AE%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95.md)


## 4. [Dockerfile解説](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-4.%20Dockerfile%E8%A7%A3%E8%AA%AC.md)

### 今回作成したDockerfile

  [各ツールの最新版を扱えるDockerfile](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/Dockerfile.md)では、使用者が本ファイルを「 1. [WSL2のセットアップ](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-1.%20WSL2%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97.md)」「2. [Dockerのインストール](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-2.%20Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.md)」「3. [Dockerfileの作成からコンテナの起動までの操作方法](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/1-3.%20Dockerfile%E3%81%AE%E4%BD%9C%E6%88%90%E3%81%8B%E3%82%89%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E8%B5%B7%E5%8B%95%E3%81%BE%E3%81%A7%E3%81%AE%E6%93%8D%E4%BD%9C%E6%96%B9%E6%B3%95.md)」の手順で実行するだけで同様の解析環境を使用できる

 [Linらの再解析をした際に作成したDockerfile](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/Lin%20et%20al%20Dockerfile.md)は再解析用に作成したもので各ツールをLinの解析で使用されたバージョンにそろえてある

   なお、
## 5. [ゲノム解析1](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88/%E3%82%B2%E3%83%8E%E3%83%A0%E8%A7%A3%E6%9E%901)
### Trimomatic~GATK Haplotype Caller

## 6. [ゲノム解析2](https://github.com/ShimizuYoshiki0816/bioinfo/blob/main/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%88/%E3%82%B2%E3%83%8E%E3%83%A0%E8%A7%A3%E6%9E%902)
### GATK CombineGVCF~ PLINK


