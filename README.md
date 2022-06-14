# Nuclei Templates Brazuca
Repositório criado com intuito de reunir templates da ferramenta Nuclei dentro do contexto Brasil.

> Nuclei é um scanner de vulnerabilidade rápido e personalizável. A ferramenta Nuclei é uma ferramenta baseada na linguagem Golang usada para enviar requests através de vários alvos com base em modelos de núcleos que levam a zero falsos positivos ou resultados irrelevantes e fornece varredura rápida em vários hosts. [ [mais](https://github.com/projectdiscovery/nuclei) ]


<p style="text-align:center" align="center">
<img src="asset/logo.png" width="50%" /><br>
</p>

Este conjundo de templates são categorizado inialmente em 3 tipos.

- **Conulta**
    - Usa algum serviço para coletar informações.
- **Dorking**
    - Efetua pesquisas usando motores de busca.
- **Extractor**
    - Utiliza de expressão regular para extrair informações de determinada URL.


## Dorking
Efetuar pesquisa usando motores de busca. uso de técnicas Google Hacking.
- **Google**
```bash
nuclei --var DORK='{{DORK}}' -t ./nuclei-templates-brazuca/dorking/dorking-{{NOME-MOTOR-DE-BUSCA}}.yaml  -vv
```
![Google](/asset/img-google.jpeg)

- Estrutura / Outras opções
```bash
dorking/
├── dorking-ask.yaml
├── dorking-auone.yaml
└── dorking-google.yaml
```
- **Pesquisa com todos motores**
```bash
nuclei --var DORK='{{DORK}}' -t ./nuclei-templates-brazuca/dorking/.*  -vv
```

## Consulta
É possível usar diversas APIS para consultar dados.

- **celular**: 
    - Consulta dados de id OPERADORA do celular via API telein.com.br
```bash
nuclei --var CELULAR={{NUMERO-CELULAR}} -t ./nuclei-templates-brazuca/consulta/celular/operadora/ -vv
```
- **cep**
    - Conuslta de CEP via API viacep.com.br
```bash
nuclei --var CEP={{CEP}} -t ./nuclei-templates-brazuca/consulta/cep/viacep/cep-viacep.yaml -vv
```
- **endereço**
    - Conuslta de endereço via API viacep.com.br
```bash
nuclei --var UF={{UF}} --var CIDADE='{{NOME-CIDADE}}' --var END='{{NOME-RUA}}' -t ./nuclei-templates-brazuca/consulta/cep/viacep/endereco-viacep.yaml -vv
```
- **creditcard**
    - Usando API lookup.binlist.net para validar BIN 
```bash
nuclei --var BIN={{BIN}} -t ./nuclei-templates-brazuca/consulta/creditcard/bin/binlist/bin-binlist.yaml -vv
```
- **empresas**
    - Consultando informações sobre CNPJ usando o site receitaws.com.br
```bash
nuclei --var CNPJ={{CNPJ}} -t ./nuclei-templates-brazuca/consulta/empresas/cnpj/receitaws/cnpj-receitaws.yaml -vv
```
- **host**
    - Obetendo informações sobre IP via serviço ipwhois.app
```bash
nuclei -var IP={{IP}} -t ./nuclei-templates-brazuca/consulta/host/ip/ipwhois/ip-ipwhois.yaml -vv
```
- **veiculos**
    -  Consulta dados de PLACA via API tabelafipebrasil.com
```bash
nuclei --var PLACA={{PLACA}} -t ./nuclei-templates-brazuca/consulta/veiculos/placa/tabelafipebrasil/placa-tabelafipebrasil.yaml -vv
```

## Extração de valores
As informações coletadas são extraidas usando expressão regular.

**Por tipo**
- Extraindo dados executando por tipo de extrator.
```bash
nuclei -u '{{URL_SOURCE}}' -t ./nuclei-templates-brazuca/extractor/{{TIPO}}/{{NOME-EXTRATOR}}.yaml -vv
```
**Todos tipos**
- Excutando todos extratores
```bash
nuclei -u '{{URL_SOURCE}}' -t ./nuclei-templates-brazuca/extractor/.* -vv
```

- Tipo de extratores
    - bitcoin
    - cep
    - cnh
    - cnpj
    - cpf
    - creditcard
    - email
    - emoji
    - ip
    - mac address
    - rg
    - telefone
    - url
    - uuid

## Estrutura
```bash
nuclei-templates-brazuca/
├── asset
│   └── img-google.jpeg
├── consulta
│   ├── celular
│   │   └── operadora
│   │       └── operadora-telein.yaml
│   ├── cep
│   │   └── viacep
│   │       ├── cep-viacep.yaml
│   │       └── endereco-viacep.yaml
│   ├── creditcard
│   │   └── bin
│   │       └── binlist
│   │           └── bin-binlist.yaml
│   ├── empresas
│   │   └── cnpj
│   │       └── receitaws
│   │           └── cnpj-receitaws.yaml
│   ├── host
│   │   ├── ip
│   │   │   └── ipwhois
│   │   │       └── ip-ipwhois.yaml
│   │   └── whois
│   └── veiculos
│       └── placa
│           └── keplaca
│               └── placa-keplaca.yaml
├── dorking
│   ├── dorking-ask.yaml
│   ├── dorking-auone.yaml
│   └── dorking-google.yaml
├── extractor
│   ├── bitcoin
│   │   └── extractor-bitcoin.yaml
│   ├── cep
│   │   └── extractor-cep.yaml
│   ├── cnh
│   │   └── extractor-cnh.yaml
│   ├── cnpj
│   │   └── extractor-cnpj.yaml
│   ├── cpf
│   │   └── extractor-cpf.yaml
│   ├── creditcard
│   │   └── extractor-creditcard.yaml
│   ├── email
│   │   └── extractor-email.yaml
│   ├── emoji
│   │   └── extractor-emoji.yaml
│   ├── info.txt
│   ├── ip
│   │   ├── extractor-ipv4.yaml
│   │   └── extractor-ipv6.yaml
│   ├── mac address
│   │   └── extractor-mac.yaml
│   ├── rg
│   │   └── extractor-rg.yaml
│   ├── telefone
│   │   └── extractor-telefone.yaml
│   ├── url
│   │   └── extractor-url.yaml
│   └── uuid
│       └── extractor-uuid.yaml
└── README.md

35 directories, 28 files
```