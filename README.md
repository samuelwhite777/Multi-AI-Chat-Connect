# Multi AI Chat Connect

Uma interface de chatbot web front-end, construída com HTML, TailwindCSS e JavaScript puro, que permite a conexão com múltiplos provedores de Modelos de Linguagem Grandes (LLMs) através de suas APIs.

## Funcionalidades

* **Interface de Chat Limpa:** UI simples e intuitiva para conversação.
* **Múltiplos Provedores de LLM:** Suporte para integração com:
    * Google (Gemini)
    * OpenAI (GPT)
    * DeepSeek
    * Anthropic (Claude)
    * Cohere
    * Microsoft Azure AI (via Azure OpenAI Service)
    * AWS (Bedrock - requer configuração de autenticação específica ou proxy)
    * Hugging Face (Inference API)
    * AI21 Labs
    * Mistral AI
* **Configuração no Cliente:** Seleção de provedor e inserção de chave de API diretamente na interface.
* **Armazenamento Local:** As chaves de API são salvas no `localStorage` do navegador para persistência entre sessões (apenas no navegador do usuário).
* **Design Responsivo:** Interface adaptável para diferentes tamanhos de tela.

## Como Usar

1.  **Clone o repositório (ou baixe os arquivos):**
    ```bash
    git clone [https://github.com/SEU-USUARIO/multi-ai-chat-connect.git](https://github.com/SEU-USUARIO/multi-ai-chat-connect.git)
    cd multi-ai-chat-connect
    ```
    (Substitua `SEU-USUARIO` pelo seu nome de usuário no GitHub e `multi-ai-chat-connect` pelo nome do seu repositório, se diferente).

2.  **Abra `index.html` no seu navegador:**
    Não há necessidade de build ou dependências complexas. Basta abrir o arquivo `index.html` (ou o nome que você deu ao arquivo HTML principal) diretamente.

3.  **Configure a API:**
    * Na página inicial, selecione o **Provedor da API** desejado no menu suspenso.
    * Insira sua **Chave da API** (ou token, e informações adicionais conforme o placeholder) no campo correspondente.
        * **Aviso Importante:** Você precisará obter chaves de API válidas diretamente dos respectivos provedores de LLM. As instruções e formatos de chave podem variar.
        * Para provedores como **Azure AI**, **AWS Bedrock**, e **Hugging Face**, pode ser necessário fornecer informações adicionais junto com a chave (ex: `CHAVE_API;ENDPOINT_COMPLETO` para Azure, `MODEL_ID;REGIAO_AWS;CHAVE_PROXY` para AWS Bedrock, `TOKEN_HF;MODEL_ID_COMPLETO` para Hugging Face). Siga as instruções no placeholder do campo da chave.
        * A integração com **AWS Bedrock** diretamente do cliente é complexa devido à autenticação AWS Signature V4. A implementação atual assume uma configuração simplificada (ex: um proxy que lida com a autenticação) ou que o usuário gerenciará a autenticação de outra forma. Para produção, um backend ou o AWS SDK é recomendado para Bedrock.
    * Clique em "Salvar e Continuar".

4.  **Comece a Conversar:**
    Após salvar a chave, a interface de chat será carregada, e você poderá interagir com o LLM selecionado.

## Tecnologias Utilizadas

* HTML5
* TailwindCSS (via CDN)
* JavaScript (Vanilla/Puro)

## Desenvolvimento

* **Estrutura do Código:**
    * O arquivo HTML principal (ex: `index.html`) contém toda a estrutura HTML, CSS (via Tailwind e `<style>`) e o código JavaScript.
    * O JavaScript está contido em uma única tag `<script>` no final do `body`.
* **Lógica da API:**
    * A função `sendMessageToLLM(prompt)` no JavaScript é o núcleo da integração com as APIs.
    * Cada provedor de API tem um `case` dedicado dentro desta função para formatar a requisição (URL, headers, payload) e processar a resposta.
    * **Nota para Desenvolvedores:** As implementações de API para os diversos provedores são baseadas em suas documentações no momento da criação. APIs de LLM evoluem rapidamente. É crucial verificar a documentação oficial de cada provedor para garantir que os endpoints, formatos de payload, e métodos de autenticação estejam atualizados antes de usar em produção ou se encontrar problemas.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests para melhorias, correção de bugs ou adição de novos provedores de LLM.

## Licença

Este projeto é distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes. (Você precisará criar um arquivo `LICENSE` no seu repositório, por exemplo, com o texto da licença MIT).
