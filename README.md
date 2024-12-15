

# 📖 **Documentação da Aplicação - Executar Código JavaScript** 🚀

<a href="https://www.mentemaker.com.br/javascript-ide/" target="_blank" style="font-size: 24px; font-weight: bold;">
 🧑‍💻Execute seu código javaScript
</a>
<br>

<a href="https://www.youtube.com/watch?v=BdR_NEI2oTM&list=PLpo2vYALH9e58UzWhvozuMAaK7vVS4_lP&index=23" target="_blank">
  <img src="https://img.youtube.com/vi/BdR_NEI2oTM/0.jpg" alt="Curso de JavaScript" width="200" style="object-fit: cover; border-radius: 8px;">
  <p><strong>🌐 Curso de JavaScript</strong></p>
</a>

## 📝 **Visão Geral**

A aplicação **Executar Código JavaScript** permite aos usuários inserir e executar código JavaScript diretamente em um navegador, sem precisar de um ambiente de desenvolvimento externo. Ao escrever o código e clicar no botão **Executar**, o resultado é imediatamente mostrado, com suporte para exibição de erros e saídas do `console.log`. 🚀

Além disso, a aplicação oferece a opção de alternar entre **modo claro** e **modo escuro**, proporcionando uma experiência visual personalizada. 🌞🌙

---

## 🔧 **Funcionalidades**

1. **Escreva o Código JavaScript** ✍️:
   - Insira o código JavaScript na área de texto. Pode ser qualquer código que deseja testar ou depurar.
   
2. **Execute o Código** ▶️:
   - Ao clicar no botão **Executar**, o código será executado e o resultado será mostrado logo abaixo da área de entrada. Se houver algum erro, ele será capturado e mostrado de forma clara.
   
3. **Modo Claro e Escuro** 🌙🌞:
   - Clique no botão **Alterar Tema** para alternar entre o **modo claro** e o **modo escuro**, tornando a interface mais confortável de acordo com a preferência do usuário.

---

## 🚀 **Como Usar**

### 1. **Escrever Código**

Na área de texto, insira qualquer código JavaScript. Aqui está um exemplo de código que você pode testar:

```javascript
console.log("Olá, Mundo! 🌍");
```

### 2. **Executar o Código**

Após escrever seu código, clique no botão **Executar**. O código será executado e o resultado será exibido abaixo da área de texto. Se houver qualquer erro, ele será mostrado em vermelho. 🔴

### 3. **Alterar Tema**

Para alternar entre o modo claro e o modo escuro, clique no botão **Alterar Tema**. Isso alterará o estilo da página para se ajustar melhor ao seu ambiente de trabalho ou preferências visuais.

---

## 🖥️ **Interface da Aplicação**

A interface é simples e objetiva, composta por:

1. **Área de Texto**: Onde você digita o código JavaScript.
2. **Botão "Executar"**: Ao clicar, o código inserido será executado.
3. **Área de Resultado**: Exibe a saída do código ou o erro caso aconteça.
4. **Botão "Alterar Tema"**: Permite alternar entre o modo claro e o modo escuro.

---

## 🎨 **Exemplo Visual**

Aqui está um exemplo de como a interface da aplicação será visualizada após a execução de um código simples:

### Código:

```javascript
console.log("Executando código!");
```

### Resultado:

```
Executando código!
```

Se ocorrer um erro, ele será exibido de maneira destacada para fácil leitura e correção.

---

## 🧑‍💻 **Exemplo de Código**

Abaixo está um exemplo de código que pode ser inserido para testes:

```javascript
let saudacao = "Olá, usuário! 😃";
console.log(saudacao);
```

Ao clicar em **Executar**, o resultado será exibido da seguinte maneira:

```
Olá, usuário! 😃
```

---

## ⚠️ **Exibição de Erros**

Se houver um erro no código, como uma sintaxe incorreta, ele será mostrado de forma destacada na área de resultado. Exemplo de erro:

```javascript
console.log("Erro de sintaxe"
```

Resultado de erro exibido:

```
Uncaught SyntaxError: Unexpected end of input
```

---

## ⚙️ **Detalhamento do Código JavaScript**

### 1. **Função `toggleTheme()`**

A função **`toggleTheme()`** alterna entre os modos **claro** e **escuro**. Isso é feito modificando as classes CSS do corpo, do container e dos botões. O código:

```javascript
function toggleTheme() {
  const body = document.body;
  const container = document.getElementById('container');
  const textarea = document.getElementById('code');
  const buttons = document.querySelectorAll('button');
  const resultado = document.getElementById('resultado');

  body.classList.toggle('dark-mode');
  container.classList.toggle('dark-mode');
  textarea.classList.toggle('dark-mode');
  buttons.forEach(btn => btn.classList.toggle('dark-mode'));
  resultado.classList.toggle('dark-mode');
}
```

- **Alterna** as classes `dark-mode` para o corpo, container, área de texto, botões e resultado.
- **Proporciona** a mudança visual entre o modo claro e o modo escuro.

### 2. **Função `executarCodigo()`**

A função **`executarCodigo()`** captura o código inserido na área de texto e tenta executá-lo com **`eval()`**. Ela também captura e exibe qualquer saída gerada por **`console.log()`**.

```javascript
function executarCodigo() {
  var codigo = document.getElementById('code').value;
  var consoleLog = console.log; // Salva a referência original para console.log
  
  // Redefine console.log para capturar a saída
  var capturarSaida = [];
  console.log = function() {
    var mensagem = Array.prototype.slice.call(arguments).join(' ');
    capturarSaida.push(mensagem);
  };
  
  try {
    var resultado = eval(codigo); // Executa o código inserido
    
    var saidaCapturada = capturarSaida.join('<br>');
    
    if (saidaCapturada) {
      document.getElementById('resultado').innerHTML = saidaCapturada;
    } else if (resultado === undefined) {
      document.getElementById('resultado').innerHTML = "<pre>Nenhum resultado retornado</pre>";
    } else {
      document.getElementById('resultado').innerHTML = "<pre>" + resultado + "</pre>";
    }
  } catch (error) {
    document.getElementById('resultado').innerHTML = "<pre class='error'>" + error + "</pre>";
  }
  
  console.log = consoleLog; // Restaura o console.log original
}
```

- **Captura** qualquer mensagem de `console.log()` e a exibe abaixo.
- **Exibe** o resultado do código ou erros de forma clara para depuração.

---

## 💡 **Recursos Adicionais**

- **Uso de `eval()`**: A função `eval()` executa o código JavaScript passado como string. **Cuidado**: O uso de `eval()` pode ser perigoso se não for controlado adequadamente. Evite usá-lo em ambientes de produção sem precauções.
- **Temas Personalizáveis**: Alterne entre os temas claro e escuro para ajustar a interface conforme suas preferências.

---

## 🎉 **Conclusão**

Essa aplicação simples proporciona uma experiência prática e interativa para executar código JavaScript diretamente no navegador, sem necessidade de configurações adicionais! 😄

---

## 📞 **Entre em Contato**

Se precisar de ajuda ou tiver sugestões, fique à vontade para entrar em contato! 💬

---

✨ **Feliz codificação!** ✨
