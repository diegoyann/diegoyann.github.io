# Página de retorno OAuth do Mercado Livre

Esta página estática só lê `code` e `state` da URL de retorno, mostra os valores na aba para cópia manual e remove os parâmetros da barra de endereço. Não faz chamadas de rede, não salva os valores e não contém Client Secret, access token ou refresh token.

## Publicação gratuita no GitHub Pages

1. Crie um repositório público chamado exatamente `diegoyann.github.io`.
2. Copie o `index.html` para a raiz desse repositório.
3. Em **Settings → Pages**, publique a branch `main` pela pasta raiz.
4. Quando o GitHub indicar que a página está publicada, o endereço será `https://diegoyann.github.io/`.
5. Teste no navegador com `?code=TESTE&state=TESTE`; a página deve mostrar os dois valores e limpar a query da barra de endereço.
6. No DevCenter, cadastre a URL HTTPS publicada, sem `code`, `state` ou outros parâmetros. Confirme que o DevCenter a aceita antes de usar a autorização.
7. Informe exatamente essa mesma URL ao configurar o aplicativo local e iniciar o OAuth.

O site será público. O `code` e o `state` passam pela URL do GitHub Pages durante o retorno OAuth; o JavaScript desta página só os mantém na aba atual para cópia manual. O Client Secret e os tokens continuam exclusivamente no programa local. Não coloque credenciais neste repositório.

O projeto local conclui a autorização com `python marketplace_api.py finish-mercadolivre`, que pede `code` e `state` no terminal. Esta página não envia os valores automaticamente para `localhost` porque o programa atual não mantém um servidor de callback HTTP.

O DevCenter já rejeitou o exemplo `https://localhost.com/redirect` com a mensagem genérica “O endereço deve ser válido”. A aceitação do domínio `github.io` precisa ser confirmada na própria tela antes de prosseguir.
