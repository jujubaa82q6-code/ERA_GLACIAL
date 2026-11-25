# Laboratório das Mudanças de Estado

**Aqueça, resfrie e descubra a Química!**

Site educacional em React, TypeScript e Vite. O visual da Era Glacial foi mantido; o laboratório usa azul-claro, azul-escuro, branco, lilás e rosa suaves. As imagens de Sid e da turma foram fornecidas para o projeto escolar.

## Como abrir no VS Code

1. Instale o Node.js **24 LTS**, com npm.
2. Extraia o ZIP e abra a pasta `laboratorio-mudancas-de-estado` no VS Code.
3. Abra **Terminal → Novo Terminal** dentro dessa pasta.
4. Execute:

```bash
npm ci
npm run dev
```

5. Abra o endereço exibido no terminal, normalmente `http://localhost:5173`.
6. Para encerrar, pressione `Ctrl+C` no terminal.

A primeira instalação precisa de internet para baixar as dependências. Depois disso, o site funciona localmente sem conta, API ou conexão permanente. Todas as imagens e fontes usadas estão em `public/`. O link externo de leitura complementar é opcional.

## Comandos

```bash
npm run dev       # servidor local para desenvolvimento
npm run build     # confere TypeScript e gera a pasta dist
npm run preview   # serve a versão compilada; execute build antes
npm test          # testa temperaturas, transições e pontuação
```

Não abra `index.html` com duplo clique: o projeto usa módulos e deve ser servido pelo Vite. A publicação privada hospedada pode exigir a conta do proprietário, mas a versão local não tem login.

## Estrutura de pastas

- `index.html`: documento inicial e título da página.
- `package.json`: dependências e comandos.
- `package-lock.json`: versões exatas das dependências.
- `tsconfig.json`: configuração do TypeScript.
- `src/main.tsx`: montagem da página, navegação e seleção de experiências.
- `src/Expedition.tsx`: abertura cinematográfica, destinos e seção final com a turma.
- `src/components/Simulator.tsx`: temperatura, botões, explicações, som e guia do Sid.
- `src/components/Particles.tsx`: recipiente e animação leve em Canvas.
- `src/components/Learn.tsx`: seis transformações, energia e curiosidades.
- `src/components/Quiz.tsx`: interface do quiz, alternativas e resultado.
- `src/lib/simulation.ts`: regras puras de temperatura, direção e transições.
- `src/data/expeditions.ts`: nomes dos cinco destinos da página inicial.
- `src/data/learning.ts`: conteúdo educativo e curiosidades.
- `src/data/questions.ts`: 12 perguntas e regras de pontuação.
- `src/style.css`: estilos básicos do projeto.
- `src/redesign.css`: identidade visual preservada da Era Glacial.
- `src/laboratory.css`: laboratório, aprendizado, quiz e ajustes responsivos.
- `src/fonts.css`: fontes locais, quando disponíveis, e alternativas do sistema.
- `public/`: imagens locais e fontes.
- `tests/simulation.test.mjs`: dez testes automatizados.
- `TESTES.md`: roteiro de verificação manual e registro do que foi executado.
- `FONTES.md`: referências e limites do modelo.

## Como funciona

### Temperatura e mudanças de estado

A variável `temperature` guarda um número inteiro entre −20 e 120. O slider altera esse número imediatamente. Aquecer e Resfriar alteram 1 °C a cada 350 ms, apenas como velocidade didática. Pausar interrompe essa alteração, e Reiniciar volta a −20 °C.

`getPhase` classifica a amostra. `crossedTransitions` compara a temperatura anterior e a nova para identificar fusão, ebulição, condensação e solidificação. Se o slider atravessar os dois pontos de uma vez, os nomes aparecem na ordem correta.

O modelo é por **temperatura imposta**, não por cálculo de energia. Não mede calor, tempo físico de transformação, pressão variável nem a fração de cada fase. Exatamente em 0 °C e 100 °C, o texto fala em possível coexistência: o desenho misto é ilustrativo e não garante mudança em andamento. Sublimação e deposição são abordadas em Aprenda, sem alegar que o slider a 1 atm simula esses processos.

### Partículas

São 56 bolinhas desenhadas por `requestAnimationFrame`, sem bibliotecas gráficas adicionais. No sólido, elas vibram junto de posições organizadas; no líquido, se movem na região inferior; no gás, ocupam uma área maior e se movem mais rapidamente. As posições convergem gradualmente para o novo estado. Não é dinâmica molecular real. O botão Pausar partículas permite observar uma imagem congelada. Ele não pausa o controle de temperatura, que tem seu próprio botão.

### Quiz

Um `useReducer` controla pergunta, seleção, confirmação e pontuação. Só a primeira confirmação conta. A resposta fica bloqueada até avançar, e o reinício zera todo o estado. As questões e justificativas ficam num arquivo separado, fácil de editar.

### Som e acessibilidade

O som é opcional, desligado inicialmente e sintetizado no navegador com Web Audio. Há navegação por âncoras, controles nativos de teclado, alternativas de quiz em grupos de rádio, foco visível e aviso de correção textual. O resultado e a pergunta seguinte recebem foco. Redução de movimento desliga efeitos decorativos; a animação científica pode ser pausada manualmente.

### Responsividade

O laboratório passa de duas colunas para uma em telas menores que 760 px. Os cards educativos e as curiosidades se reorganizam, e o menu fica em uma segunda linha no celular.

## Verificações realizadas

- Dez testes automatizados das regras de temperatura e quiz passaram.
- TypeScript e build de produção passaram.
- O ambiente não disponibilizou o navegador de testes permitido: botões, aparência, áudio e layout responsivo precisam da conferência manual descrita em `TESTES.md`. Não foi alegado um teste visual que não ocorreu.

## Roteiro rápido para apresentar

1. Comece em −20 °C: a água está sólida e as partículas vibram.
2. Clique em Aquecer e pare em 0 °C: explique fusão e possível coexistência.
3. Mostre 25 °C: partículas próximas e móveis no líquido.
4. Selecione 100 °C: explique a referência de ebulição a 1 atm.
5. Vá a 110 °C e resfrie: compare condensação e solidificação.
6. Explore as seis transformações e responda ao quiz com a turma.
"# ERA_GLACIAL" 
"# ERA_GLACIAL" 
