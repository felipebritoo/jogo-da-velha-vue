Documentação: Projeto Vue - Jogo da Velha
Descrição
Este documento descreve a criação de um projeto Vue para um jogo da velha, incluindo a configuração inicial, desenvolvimento do jogo, alterações no código e versionamento com Git. O projeto utiliza Vite como ferramenta de build e CSS puro para estilização, replicando as funcionalidades do projeto React anterior.
Etapas Realizadas
1. Configuração do Projeto

Ferramentas: Node.js, Vite.
Comandos:npm create vite@latest jogo-da-velha-vue -- --template vue
cd jogo-da-velha-vue
npm install


Arquivos criados:
src/App.vue: Componente raiz com título.
src/components/Board.vue: Componente do tabuleiro e lógica do jogo.
index.html: Página HTML com fonte Poppins.



2. Desenvolvimento do Jogo

Implementado o jogo da velha com:
Tabuleiro 3x3 com botões interativos.
Lógica para alternar entre jogadores (X e O).
Verificação de vencedor ou empate.
Botão para reiniciar o jogo.
Placar para rastrear vitórias.
Modal para anunciar vitória ou empate.
Destaque da linha vencedora com animação.


Estrutura de componentes:
Board.vue: Contém o tabuleiro, lógica e estilos.
App.vue: Componente raiz com título.



3. Alterações Iniciais

Adição do contador de partidas:
Estado gamesPlayed para rastrear o número de partidas jogadas.
Exibição do contador abaixo do placar.
Incremento do contador ao final de cada partida (vitória ou empate).


Arquivos modificados:
src/components/Board.vue: Adicionado estado e exibição do contador de partidas.



4. Versionamento com Git

Commits:
Inicial: Configuração do projeto Vue para jogo da velha
Adicionado contador de partidas jogadas


Repositório GitHub:
Criado repositório jogo-da-velha-vue.
Link: https://github.com/SEU_USUARIO/jogo-da-velha-vue



5. Capturas de Tela

Tela inicial do jogo:Descrição: Mostra o tabuleiro vazio com o status "Próximo jogador: X".
Jogo em andamento com placar e contador:Descrição: Exibe o placar e o contador de partidas após uma vitória.

6. Próximos Passos

Deploy do projeto na Vercel (a ser realizado).
Criação do projeto Angular.
Importação e modificação de um template.
Documentação final com todos os repositórios e links de deploy.

Observações

O projeto foi estruturado para ser funcional e visualmente consistente com o projeto React.
O repositório GitHub será atualizado com o deploy e outras alterações futuras.

