# Erros para Estudar

## 1. `text-align: center` sem largura no container
**Erro:** O parágrafo `.description` não centralizava o texto com quebra de linha.
**Causa:** O container pai não tinha largura definida, então o elemento encolhia para o tamanho do conteúdo e não havia espaço para centralizar.
**Solução:** Definir `width` ou `max-width` no container pai.

---

## 2. `align-items` / `flex-grow` sem `display: flex`
**Erro:** Propriedades flex aplicadas em elementos que não eram flex containers.
**Causa:** `align-items`, `justify-content`, `gap` e `flex-grow` só funcionam em elementos com `display: flex` ou `display: grid`.
**Solução:** Sempre declarar `display: flex` antes de usar propriedades flex.

---

## 3. `flex-grow` em filhos de container não-flex
**Erro:** `flex-grow: 1` aplicado nos `span`s dentro de `.title`, mas `.title` estava com `display: flex` comentado.
**Causa:** `flex-grow` só afeta filhos diretos de um flex container ativo.
**Solução:** Verificar se o pai é um flex container antes de usar `flex-grow`.

---

## 4. Seletor CSS não bate com o HTML
**Erro:** `li.github-tag` no CSS, mas no HTML o `<li>` não tinha classe nenhuma.
**Causa:** Escrever o CSS antes de definir as classes no HTML, ou esquecer de adicionar a classe.
**Solução:** Sempre conferir se o seletor CSS corresponde exatamente ao que está no HTML.

---

## 5. `background-repeat` em `background-color`
**Erro:** `background-repeat: repeat-x, repeat-y` aplicado junto com `background-color`.
**Causa:** `background-repeat` só funciona com `background-image`. Em cores sólidas não tem efeito.
**Solução:** Remover `background-repeat` quando não há imagem de fundo.

---

## 6. `background-color` no container errado
**Erro:** Cor de fundo aplicada no `ul` inteiro em vez de em cada `li`.
**Causa:** O design pedia pílulas individuais, mas o estilo foi aplicado na lista toda.
**Solução:** Identificar qual elemento representa visualmente a pílula e aplicar o estilo nele.

---

## 7. `<svg src="...">` não existe
**Erro:** Tentar usar `<svg src="caminho.svg">` para carregar um SVG externo.
**Causa:** O atributo `src` pertence à tag `<img>`, não à `<svg>`.
**Solução:** Usar `<img src="...svg">` para carregar como imagem, ou colar o conteúdo SVG inline.

---

## 8. `<use xlink:href="externo.svg">` não funciona
**Erro:** Tentar referenciar um arquivo SVG externo com `<use xlink:href="arquivo.svg">`.
**Causa:** Browsers bloqueiam o carregamento de SVGs externos por restrições de segurança (CORS).
**Solução:** Usar SVG inline (colar o código no HTML) para ter controle de cor via CSS.

---

## 9. `<path>` solto fora do `<svg>`
**Erro:** Tag `<path>` colocada diretamente dentro de uma `<div>` sem a tag `<svg>` envolvendo.
**Causa:** O `<path>` é um elemento interno do SVG e precisa estar dentro de `<svg>` para renderizar.
**Solução:** Sempre envolver os elementos SVG (`path`, `circle`, etc.) dentro de `<svg>`.

---

## 10. `fill` hardcoded sobrescreve `currentColor`
**Erro:** `fill="#FFFFFF"` no `<path>` impedia que a cor do CSS fosse aplicada.
**Causa:** Um valor fixo de `fill` no elemento tem prioridade sobre `currentColor`.
**Solução:** Trocar `fill="#cor"` por `fill="currentColor"` nos paths para poder controlar a cor via CSS.

---

## 11. `padding-block` desalinhando itens
**Erro:** `padding-block: 16px 8px` no `li` deslocava o conteúdo verticalmente.
**Causa:** Padding vertical em um elemento com altura fixa empurra o conteúdo para baixo.
**Solução:** Usar `align-items: center` no flex container para centralizar verticalmente, sem padding-block.

---

## 12. `li.image` em vez de `img`
**Erro:** Seletor `li.image` para estilizar a imagem dentro do `li`.
**Causa:** A imagem no HTML é uma tag `<img>`, não um `<li>` com classe `image`.
**Solução:** Usar o seletor `img` dentro do `li`.

---

## 13. Tag `</div>` extra no HTML
**Erro:** Um `</div>` sobrando no final do body causava estrutura inválida.
**Causa:** Perder o controle de abertura e fechamento de tags aninhadas.
**Solução:** Usar a indentação correta e o recurso de highlight de tags do VS Code para conferir os pares.

---

## Resumo dos conceitos principais
| Conceito | Regra |
|---|---|
| `text-align: center` | O container precisa de largura para centralizar texto com quebra |
| Propriedades flex | Só funcionam com `display: flex` no pai |
| `flex-grow` | Só afeta filhos diretos de flex container |
| Seletores CSS | Devem bater exatamente com as classes/tags do HTML |
| SVG inline | Único método que permite colorir via CSS `color`/`fill` |
| `fill="currentColor"` | Necessário nos `<path>` para herdar a cor do CSS |
| `background-repeat` | Só funciona com `background-image` |
