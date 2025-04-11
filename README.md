# Cell Bioinfo (Unicentro) - I Curso de Aperfeiçoamento

### Acesse seu GitHub Codespace pelo link abaixo:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mlfalco-bioinfo/cell_bioinfo)


### Vamos seguir os comandos abaixo para iniciar os downloads de arquivos diretamente no NCBI

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
