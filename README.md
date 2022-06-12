# nuclei-templates-brazuca
Repositório criado com intuito de reunir templates da ferramenta Nuclei dentro do contexto Brasil
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

## Exemplos

### Dorking
Efetuar pesquisa usando motores de busca. uso de técnicas Google Hacking.
- Google
```bash
nuclei --var DORK=site:br -t ./nuclei-templates-brazuca/dorking/dorking-google.yaml  -vv
```
![Google](/asset/img-google.jpeg)

- Estrutura / Outras opções
```bash
dorking/
├── dorking-ask.yaml
├── dorking-auone.yaml
└── dorking-google.yaml
```
- Pesquisa com todos motores
```bash
nuclei --var DORK=site:br -t ./nuclei-templates-brazuca/dorking/.*  -vv
```

### Consulta
É possível usar diversas APIS para consultar dados.

- celular: Consulta dados de id OPERADORA do celular via API telein.com.br
```bash
nuclei --var CELULAR=0000000000 -t ./nuclei-templates-brazuca/consulta/celular/operadora/ -vv
```
- cep
```bash
nuclei --var CEP=01153000 -t ./nuclei-templates-brazuca/consulta/cep/viacep/cep-viacep.yaml -vv
```
- endereço
```bash
nuclei --var UF=SP --var CIDADE='São paulo' --var END='São bento' -t ./nuclei-templates-brazuca/consulta/cep/viacep/endereco-viacep.yaml -vv
```
- creditcard
```bash
nuclei --var BIN=0000000000 -t ./nuclei-templates-brazuca/consulta/creditcard/bin/binlist/bin-binlist.yaml -vv
```
- empresas
```bash
nuclei --var CNPJ=0000000000 -t ./nuclei-templates-brazuca/consulta/empresas/cnpj/receitaws/cnpj-receitaws.yaml -vv
```
- host
```bash
....
```
- veiculos
```bash
nuclei --var PLACA=000000 -t ./nuclei-templates-brazuca/consulta/veiculos/placa/keplaca/placa-keplaca.yaml -vv
```

## Extração de valores
```bash
nuclei -u 'https://www.wifi-soft.com/company/aerror.log' -t ./nuclei-templates-brazuca/extractor/.* -vv
```
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

