# Dockerfile

## このDockerfileは各ツールの最新版を扱うことができます

```
FROM broadinstitute/gatk:latest　

#Install additional tools
RUN apt-get update && apt-get install -y \
    bwa \
    samtools \
    bcftools \
    vcftools \
    wget \
    unzip \
    openjdk-11-jdk \
    git \
    parallel \
    zlib1g-dev                


#  Download and set up Trimmomatic
RUN wget -O Trimmomatic-0.39.zip http://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/Trimmomatic-0.39.zip && \
    unzip Trimmomatic-0.39.zip && \
    mv Trimmomatic-0.39/trimmomatic-0.39.jar /usr/local/bin/trimmomatic.jar && \
    cp -r Trimmomatic-0.39/adapters /usr/local/share/trimmomatic && \
    rm -rf Trimmomatic-0.39 Trimmomatic-0.39.zip

# Execution script
RUN printf '#!/bin/bash\njava -jar /usr/local/bin/trimmomatic.jar "$@"\n' > /usr/local/bin/trimmomatic && \
    chmod +x /usr/local/bin/trimmomatic



# Set up the latest PLINK（v1.9）
RUN wget -O plink.zip https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && \
    unzip plink.zip && \
    mv plink /usr/local/bin/plink && \
    chmod +x /usr/local/bin/plink && \
    rm -rf plink.zip


# Set up LinkImpute

# commons-cli
RUN mkdir -p /opt/jarbuild \
 && wget -O /opt/jarbuild/commons-cli-1.4.jar \
    https://repo1.maven.org/maven2/commons-cli/commons-cli/1.4/commons-cli-1.4.jar

# unpack commons-cli
RUN cd /opt/jarbuild \
 && jar xf commons-cli-1.4.jar

# build LinkImpute
RUN git clone https://github.com/danielmoney/LinkImpute.git /opt/LinkImpute \
 && cd /opt/LinkImpute/src \
 \
 # compile
 && mkdir -p build \
 && find . -name "*.java" > sources.txt \
 && javac -cp /opt/jarbuild/commons-cli-1.4.jar \
           -d build @sources.txt \
 \
 # manifest
 && echo "Main-Class: Executable.LinkImpute" > manifest.txt \
 \
 # fat jar (LinkImpute + commons-cli)
 && jar cvfm /usr/local/bin/LinkImpute.jar manifest.txt \
      -C build . \
      -C /opt/jarbuild org \
 \
 && rm -rf /opt/LinkImpute /opt/jarbuild


# Install Python libraries
RUN pip3 install --upgrade pip && \
    pip3 install pandas numpy scikit-learn matplotlib keras tensorflow

#Install R base and R packages
RUN apt-get update && apt-get install -y r-base && \
    Rscript -e "install.packages(c('rrBLUP', 'devtools'), repos='https://cloud.r-project.org')" && \
    Rscript -e "install.packages('sommer', repos='https://cloud.r-project.org')" && \
    Rscript -e "install.packages('BGLR', repos='https://cloud.r-project.org')"

# Configure Japanese locale
RUN apt-get update && apt-get install -y locales && \
    sed -i -e 's/# \(ja_JP.UTF-8\)/\1/' /etc/locale.gen && \
    locale-gen

ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8
```
