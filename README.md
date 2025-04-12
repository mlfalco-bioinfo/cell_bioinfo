---# Cell Bioinfo (Unicentro) - I Curso de Aperfeiçoamento

### Acesse seu GitHub Codespace pelo link abaixo:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mlfalco-bioinfo/cell_bioinfo)


## Tutorial de Comandos Básicos do Bash Aplicados à Genômica

### Download do material de aula

```bash
wget https://github.com/mlfalco-bioinfo/Intro_Bioinfo/archive/refs/heads/main.zip
```

### Estrutura de Diretórios e Arquivos

Os exercícios serão baseados na seguinte estrutura de diretórios:
```
Documents/SEBIO2024/Intro_Bioinfo/
├── bioinfo_exercicies
│   ├── dna
│   │   ├── dna.fasta
│   │   ├── dnaX.fasta
│   │   └── rna.fasta
│   ├── dnaY.fasta
│   ├── protein
│   │   ├── protein.fasta
│   │   ├── proteinX.fasta
│   │   └── proteinY.fasta
│   └── rna
├── chrom
├── chromossome.txt
├── fastq
│   ├── 76_S2_L001_R1_001.fastq.gz
│   ├── AM_S5_L001_R1_001.fastq.gz
│   ├── AM_S5_L001_R2_001.fastq
│   ├── P1B-16S_S6_L001_R1_001.fastq.gz
│   └── P1B-16S_S6_L001_R2_001.fastq.gz
├── genes.vcf
├── scripts
│   └── first.sh
└── Trimmomatic
    └── TruSeq3-PE.fa

```

## Exercícios

### 0. Anatomia do Comando

```
command [-flag(s)] [-option(s) [value]] [argument(s)]
```

### 1. Navegação no Sistema de Arquivos

#### 1.1. Exibir uma Mensagem no Terminal
Use o comando `echo` para exibir a mensagem "Bem-vindo ao tutorial de bash aplicado à bioinformática":

```
echo "Bem-vindo ao tutorial de bash aplicado à bioinformática"
```

#### 1.2. Mostrar o Diretório Atual
O comando `pwd` mostra o caminho do diretório atual:

```
pwd
```

#### 1.3. Navegar Entre Diretórios
Use o comando `cd` para navegar para o diretório `bioinfo_exercicies/dna`:

```
cd bioinfo_exercicies/dna
```

Use `cd ..` para voltar ao diretório pai (`bioinfo_exercicies`):

```
cd ..
```

### 2. Listagem de Arquivos

#### 2.1. Listar o Conteúdo de um Diretório
Liste o conteúdo do diretório `bioinfo_exercicies` usando o comando `ls`:

```
ls bioinfo_exercicies
```

Liste o conteúdo com detalhes, incluindo arquivos ocultos e tamanhos legíveis:

```
ls -lah bioinfo_exercicies
```
#### Comando para instalação do NANO
```bash
sudo apt update
sudo apt install nano
```
#### Comando para instalação do UNZIP
```bash
sudo apt install unzip
```

### 3. Download de Arquivos

#### 3.1. Baixar um Arquivo Usando `wget`

Baixe o arquivo com nossos arquivos e diretórios:

```
wget -P $HOME https://drive.google.com/file/d/1IAzjy_4KWpNBK6y2_S-y6IAgeW684neH/view?usp=sharing
```
Agora, é necessário descomprimir o arquivo `Intro_Bionfo.zip` com os diretórios/arquivos:

```
unzip Intro_Bioinfo.zip .
```


### 4. Estrutura de Diretórios

#### 4.1. Visualizar a Estrutura de Diretórios
Use o comando `tree` para visualizar a estrutura de diretórios:

```
tree bioinfo_exercicies
```

#### 4.2. Criar um Novo Diretório
Crie um diretório chamado `genoma`:

```
mkdir genoma
```

### 5. Manipulação de Arquivos

#### 5.1. Copiar Arquivos
Copie o arquivo `chromossome.txt` para o diretório `chrom`:

```
cp bioinfo_exercicies/chromossome.txt chrom/
```

#### 5.2. Mover Arquivos
Movimente o arquivo `genes.vcf` para o diretório `genoma`:

```
mv genes.vcf genoma/
```

#### 5.3. Remover Arquivos
Remova o arquivo `genoma/genes.vcf`:

```
rm genoma/genes.vcf
```

### 6. Visualização de Conteúdo de Arquivos

#### 6.1. Exibir as Primeiras e Últimas Linhas de um Arquivo
Exiba as primeiras 10 linhas do arquivo `dna.fasta`:

```
head bioinfo_exercicies/dna/dna.fasta
```

Exiba as últimas 10 linhas do arquivo `protein.fasta`:

```
tail bioinfo_exercicies/protein/protein.fasta
```

#### 6.2. Concatenar e Exibir Conteúdo de Arquivos
Use `cat` (`zcat`e `zless`) para exibir o conteúdo do arquivo `rna.fasta`:

```
cat bioinfo_exercicies/rna/rna.fasta
```

#### 6.3. Criar um Arquivo Vazio
Use `touch` para criar um novo arquivo chamado `genome.txt` no diretório `genoma`:

```
touch genoma/genome.txt
```

### 7. Uso de `grep`, `pipe` e `nano`

#### 7.1. Procurar Padrões em Arquivos com `grep` e Usar `pipe`
Use o comando `grep` para procurar pela sequência "ATGC" no arquivo `dna.fasta`:

```
grep "ATGC" bioinfo_exercicies/dna/dna.fasta
```

Combine o comando `grep` com `pipe` (`|`) para contar o número de ocorrências da sequência "ATGC":

```
grep "ATGC" bioinfo_exercicies/dna/dna.fasta | wc -l
```

**EASTER EGGS**

Utilize o comando `grep`com a palavra "LINUX" pesquisando o arquivo `rna.fasta`

#### 7.2. Editar Arquivos Usando `nano`
Abra o arquivo `first.sh` no editor de texto `nano`:

```
nano scripts/first.sh
```


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




## Vamos seguir os comandos abaixo para iniciar os downloads de arquivos diretamente no NCBI

```bash
wget --output-document sratoolkit.tar.gz https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz
```

### Descompactar os arquivos

```bash
tar -vxzf sratoolkit.tar.gz
```

### Exportar a variável $PATH

```bash
export PATH=$PWD/sratoolkit.3.2.1-ubuntu64/bin:$PATH
```

### Testar a instalação

```bash
which fastq-dump
```

### Agora vamos testar a TOOLKIT

```bash
fastq-dump --stdout -X 2 SRR390728
```


-------------------------------------------------------------------------------------------------------------------------------------------------------------


### Usando o SRATOOLKIT

#### Comando *prefetch*

```bash
prefetch SRR390728
```

#### Descompactando os arquivos FASTQ
```bash
fastq-dump --split-3 SRR390728/
```


#### Instalação do EntrezDirect

```bash
sh -c "$(curl -fsSL https://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/setup.sh)"
```

#### Adicionar no $PATH

```bash
export PATH=$PATH:$HOME/edirect
```

#### Reload do SHELL

```bash
source ~/.bashrc
```

#### Teste de Instalação do EntrezDirect
```bash
esearch -db pubmed -query "cancer" | efetch -format abstract | head
```

------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Instalação das ferramentas de Controle de Qualidade
### **FASTQC e MultiQC**


### FASTQC
#### Instalação de dependências

#### Atualização dos pacotes 
```bash
sudo apt update
```

#### Instalação do Java
```bash
sudo apt install default-jre
```

#### Instalação do FASTQC
```bash
sudo apt install fastqc
```

#### Testando a Instalação do FASTQC

```bash
fastqc --version
```

### MultiQC

#### Instalação do PIP

```bash
sudo apt install python3-pip
```

#### Instalação do MultiQC

```python
pip install multiqc
```

‐-------‐--------------------------------

# Uso do Trimmomatic para Dados Illumina Paired-End

O Trimmomatic é uma ferramenta amplamente utilizada para a filtragem e limpeza de leituras de sequenciamento de dados Illumina. Aqui está um exemplo de uso para dados **paired-end**.

## Pré-requisitos
- Trimmomatic instalado
- Java instalado
- Arquivos `.fastq.gz` dos pares de leitura (R1 e R2)

## Comando básico
```bash
java -jar trimmomatic-0.39.jar PE \
  -threads 4 \
  -phred33 \
  amostra_R1.fastq.gz amostra_R2.fastq.gz \
  amostra_R1_paired.fastq.gz amostra_R1_unpaired.fastq.gz \
  amostra_R2_paired.fastq.gz amostra_R2_unpaired.fastq.gz \
  ILLUMINACLIP:adapters.fa:2:30:10 \
  LEADING:3 \
  TRAILING:3 \
  SLIDINGWINDOW:4:15 \
  MINLEN:36
```

## Explicando os parâmetros
- `PE`: modo paired-end
- `-threads 4`: usa 4 threads para processamento paralelo
- `-phred33`: codificação de qualidade (verifique se seus dados usam phred33 ou phred64)
- `amostra_R1.fastq.gz` e `amostra_R2.fastq.gz`: arquivos de entrada
- Arquivos de saída:
  - `*_paired.fastq.gz`: leituras mantidas com pares válidos
  - `*_unpaired.fastq.gz`: leituras cujo par foi descartado
- `ILLUMINACLIP:adapters.fa:2:30:10`: remove adaptadores com base no arquivo `adapters.fa`
- `LEADING:3`: remove bases com qualidade <3 no início
- `TRAILING:3`: remove bases com qualidade <3 no fim
- `SLIDINGWINDOW:4:15`: faz uma média de qualidade em uma janela de 4 bases, cortando quando <15
- `MINLEN:36`: descarta leituras com menos de 36 bases após o trimming

## Arquivo de adaptadores
Você pode usar um arquivo de adaptadores como o `TruSeq3-PE.fa`, incluído no pacote do Trimmomatic ou baixar [aqui](https://github.com/timflutre/trimmomatic/blob/master/adapters/TruSeq3-PE.fa).

## Exemplo com gzip no output
```bash
java -jar trimmomatic-0.39.jar PE \
  -threads 4 \
  -phred33 \
  -trimlog trimlog.txt \
  amostra_R1.fastq.gz amostra_R2.fastq.gz \
  amostra_R1_paired.fastq.gz amostra_R1_unpaired.fastq.gz \
  amostra_R2_paired.fastq.gz amostra_R2_unpaired.fastq.gz \
  ILLUMINACLIP:TruSeq3-PE.fa:2:30:10 \
  SLIDINGWINDOW:4:20 \
  MINLEN:50
```

## Referência
Bolger, A. M., Lohse, M., & Usadel, B. (2014). *Trimmomatic: A flexible read trimming tool for Illumina NGS data*. Bioinformatics, 30(15), 2114–2120.

---
