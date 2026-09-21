# 📱 Projeto Flutter — Consumo de APIs

## 📌 Sobre o projeto

Este projeto foi desenvolvido utilizando **Flutter** e a linguagem **Dart**, com o objetivo de praticar o consumo de **APIs externas** em aplicativos mobile.

A aplicação realiza requisições HTTP para diferentes serviços, recebe os dados no formato **JSON**, interpreta essas informações e apresenta os resultados na interface do aplicativo.

O projeto possui funcionalidades para:

- 📍 Consulta de CEP;
- 🏢 Consulta de CNPJ;
- 💵 Consulta da cotação do Dólar.

---

## 🎯 Objetivo

O principal objetivo do projeto é compreender como um aplicativo Flutter pode se comunicar com serviços externos por meio de APIs.

Durante o desenvolvimento foram utilizados conceitos como:

- Requisições HTTP;
- Consumo de APIs REST;
- Formato JSON;
- Conversão de JSON para dados utilizáveis no Dart;
- `Future`;
- Programação assíncrona;
- `async` e `await`;
- `setState`;
- `TextEditingController`;
- Navegação entre telas;
- Exibição dos dados retornados pelas APIs.

---

# 🔌 APIs utilizadas

O projeto utiliza três APIs diferentes.

## 📍 API de CEP — ViaCEP

A consulta de CEP utiliza a API do **ViaCEP**.

Endpoint utilizado:

```text
https://viacep.com.br/ws/{CEP}/json/
```

A partir do CEP informado pelo usuário, a API retorna informações sobre o endereço.

### Informações utilizadas

- Logradouro;
- Bairro;
- Localidade;
- UF.

### Exemplo

Ao informar:

```text
01001000
```

a aplicação realiza uma requisição para a API e apresenta os dados do endereço retornado.

---

## 🏢 API de CNPJ — OpenCNPJ

A consulta de CNPJ utiliza a API do **OpenCNPJ**.

Endpoint utilizado:

```text
https://api.opencnpj.org/{CNPJ}
```

O usuário informa um CNPJ e a aplicação realiza uma requisição HTTP para obter informações da empresa.

### Informações utilizadas

- Razão social;
- Nome fantasia;
- Situação cadastral.

Os dados recebidos pela API são convertidos de JSON e apresentados na tela.

---

## 💵 API de Dólar — AwesomeAPI

A consulta da cotação do dólar utiliza a **AwesomeAPI**.

Endpoint utilizado:

```text
https://economia.awesomeapi.com.br/last/USD-BRL
```

A API retorna informações sobre a cotação do dólar em relação ao real.

### Informações utilizadas

- Nome da moeda/paridade;
- Maior valor (`high`) retornado pela API.

---

# 🛠️ Tecnologias utilizadas

- **Flutter**
- **Dart**
- **Material Design**
- **HTTP**
- **JSON**
- **APIs REST**
- **ViaCEP**
- **OpenCNPJ**
- **AwesomeAPI**

---

# 📦 Dependências

Para realizar as requisições HTTP, o projeto utiliza o pacote:

```yaml
http
```

A dependência pode ser adicionada ao `pubspec.yaml`:

```yaml
dependencies:
  flutter:
    sdk: flutter

  http: ^1.5.0
```

Depois de adicionar a dependência, execute:

```bash
flutter pub get
```

---

# 🔄 Funcionamento das requisições

O aplicativo utiliza o pacote `http` para realizar requisições `GET`.

Exemplo utilizado no projeto:

```dart
final resposta = await http.get(url);
```

Depois que a API retorna os dados, o conteúdo da resposta é convertido de JSON:

```dart
final dados = jsonDecode(resposta.body);
```

Por fim, as informações são apresentadas na interface utilizando `setState()`.

Exemplo:

```dart
setState(() {
  endereco =
      '${dados['logradouro']}\n'
      '${dados['bairro']}\n'
      '${dados['localidade']} - ${dados['uf']}';
});
```

---

# 📱 Funcionalidades

## 📍 Consulta de CEP

O usuário informa um CEP em um campo de texto e seleciona o botão **Consultar**.

A aplicação:

1. Recebe o CEP;
2. Monta a URL da API;
3. Realiza uma requisição HTTP;
4. Recebe o JSON;
5. Converte os dados;
6. Exibe o endereço na tela.

Fluxo:

```text
CEP
 ↓
ViaCEP
 ↓
JSON
 ↓
Conversão dos dados
 ↓
Endereço apresentado na tela
```

---

## 🏢 Consulta de CNPJ

O usuário informa um CNPJ e seleciona **Consultar**.

A aplicação consulta a API do OpenCNPJ e apresenta:

```text
Razão Social
Nome Fantasia
Situação Cadastral
```

Fluxo:

```text
CNPJ
 ↓
OpenCNPJ
 ↓
JSON
 ↓
Dados da empresa
 ↓
Informações apresentadas na tela
```

---

## 💵 Consulta do Dólar

Na tela de dólar, o usuário seleciona o botão **Consultar**.

A aplicação consulta a cotação:

```text
USD → BRL
```

A API retorna os dados da cotação e a aplicação apresenta as informações recebidas.

Fluxo:

```text
Consultar
    ↓
AwesomeAPI
    ↓
JSON
    ↓
Cotação USD/BRL
    ↓
Resultado na tela
```

---

# 📂 Estrutura do projeto

Uma organização sugerida para o projeto é:

```text
lib/
│
├── main.dart
│
├── screens/
│   ├── cep.dart
│   ├── cnpj.dart
│   └── dolar.dart
│
└── ...
│
├── pubspec.yaml
└── README.md
```

### `main.dart`

Responsável por iniciar o aplicativo e configurar a estrutura principal da aplicação.

### `cep.dart`

Contém a tela responsável pela consulta de CEP utilizando a API ViaCEP.

### `cnpj.dart`

Contém a tela responsável pela consulta de CNPJ utilizando a API OpenCNPJ.

### `dolar.dart`

Contém a tela responsável pela consulta da cotação do dólar utilizando a AwesomeAPI.

---

# 🧩 Exemplo de consumo de API

O projeto utiliza o seguinte padrão:

```dart
Future<void> consultar() async {
  final url = Uri.parse(
    'URL_DA_API',
  );

  final resposta = await http.get(url);

  final dados = jsonDecode(resposta.body);

  setState(() {
    // Atualização das informações
  });
}
```

Esse processo permite que o aplicativo envie uma solicitação para uma API externa e utilize os dados recebidos para atualizar a interface.

---

# ▶️ Como executar o projeto

## 1. Clonar o repositório

```bash
git clone URL_DO_SEU_REPOSITORIO
```

## 2. Entrar na pasta

```bash
cd nome-do-projeto
```

## 3. Instalar as dependências

```bash
flutter pub get
```

## 4. Verificar o Flutter

```bash
flutter doctor
```

## 5. Executar o aplicativo

```bash
flutter run
```

---

# 🌐 Conexão com a internet

Como o aplicativo realiza requisições para APIs externas, é necessário possuir **conexão com a internet** para utilizar as funcionalidades de consulta.

Sem conexão, as APIs não poderão retornar os dados solicitados.

---

# ⚠️ Tratamento de erros

As consultas dependem de serviços externos. Portanto, podem ocorrer situações como:

- Falta de conexão com a internet;
- API temporariamente indisponível;
- CEP inexistente ou inválido;
- CNPJ inválido;
- Dados não encontrados;
- Alterações ou indisponibilidade dos serviços externos.

Em uma versão futura, o aplicativo poderá apresentar mensagens específicas para cada uma dessas situações.

---

# 📚 Conceitos aprendidos

Este projeto permitiu praticar:

### Flutter

- `Scaffold`;
- `AppBar`;
- `TextField`;
- `ElevatedButton`;
- `Column`;
- `Padding`;
- `Icon`;
- `Text`;
- Navegação entre telas.

### Dart

- Classes;
- Métodos;
- Variáveis;
- `Future`;
- `async`;
- `await`;
- Strings;
- Interpolação de strings;
- `setState`.

### APIs

- HTTP GET;
- Requisições externas;
- JSON;
- `jsonDecode`;
- Consumo de dados externos;
- Exibição de informações recebidas de APIs.

---

# 🔗 Serviços utilizados

- **ViaCEP** — consulta de endereços por CEP.
- **OpenCNPJ** — consulta de informações de CNPJ.
- **AwesomeAPI** — consulta de cotações.

---

# 👩‍💻 Autora

**Thais Costa Patto de Souza**

Projeto acadêmico desenvolvido para a disciplina de **Desenvolvimento para Dispositivos Móveis**.

---

# 📄 Licença

Este projeto foi desenvolvido para fins **acadêmicos e educacionais**.
