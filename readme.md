A1
1:Entradas (inputs)
Botão de iniciar
Tipo: digital
Função: iniciar o ciclo do processo
Potenciômetro 1 (tempo)
Tipo: analógico (0–1023)
Função: definir o tempo de execução (1 a 10 segundos)
Potenciômetro 2 (intensidade)
Tipo: analógico (0–1023)
Função: definir o nível de intensidade (baixo, médio, alto)


Saídas (outputs)
LED vermelho
Indica sistema parado / pronto
LED amarelo
Indica processo em execução
LED verde
Indica processo finalizado
3 LEDs de intensidade
Representam o nível de intensidade:
1 LED → baixa
2 LEDs → média
3 LEDs → alta


2:Componentes do Sistema e Função
Microcontrolador (ex: Arduino)
Responsável por ler entradas e controlar saídas
Botão
Interface do operador para iniciar o ciclo
Potenciômetros (2x)
Ajuste manual de parâmetros (tempo e intensidade)
LEDs (6 no total)
3 de status (vermelho, amarelo, verde)
3 de intensidade
Resistores
Proteção dos LEDs e leitura adequada dos potenciômetros


3:Regras de Funcionamento
Estado inicial (parado)
LED vermelho ligado
LED amarelo e verde desligados
Ao pressionar o botão
Ler valor do potenciômetro de tempo
Converter para intervalo de 1 a 10 segundos
Ler valor do potenciômetro de intensidade
Definir nível (baixo, médio, alto)
Armazenar esses valores (não mudar durante o ciclo)
Durante execução
LED vermelho → desligado
LED amarelo → ligado
LEDs de intensidade → indicam nível escolhido
Tempo corre conforme definido
Durante execução (alterações ignoradas)
Mudanças nos potenciômetros NÃO afetam o ciclo atual
Ao terminar o tempo
LED amarelo → desligado
LED verde → ligado
LEDs de intensidade → desligados (ou mantidos, dependendo do projeto)
Após um curto período (opcional), voltar ao estado inicial
Retorno ao estado inicial
LED vermelho ligado novamente
Sistema pronto para novo ciclo


4:1. Detectar botão pressionado
if (botao == pressionado && sistema_parado) {
    iniciar_processo();
}
2. Definir tempo a partir do potenciômetro
tempo = map(valorPotTempo, 0, 1023, 1, 10);
3. Definir intensidade
if (valorPotInt < 341) {
    intensidade = BAIXA;
}
else if (valorPotInt < 682) {
    intensidade = MEDIA;
}
else {
    intensidade = ALTA;
}
4. Controlar LEDs de intensidade
if (intensidade == BAIXA) {
    acende 1 LED;
}
else if (intensidade == MEDIA) {
    acende 2 LEDs;
}
else {
    acende 3 LEDs;
}
5. Controle de estados
if (estado == PARADO) {
    liga LED vermelho;
}
else if (estado == EXECUTANDO) {
    liga LED amarelo;
}
else if (estado == FINALIZADO) {
    liga LED verde;
}
6. Finalização por tempo
if (tempo_decorrido >= tempo_definido) {
    finalizar_processo();
}
