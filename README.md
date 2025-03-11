#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

// Estrutura para representar um país
typedef struct {
    char estado[50];
    char codigoCarta[10];
    char nomeCidade[50];
    int populacao;
    float areaKm2;
    float pib;
    int pontosTuristicos;
} Pais;

// Função para criar um país
Pais criarPais(char* estado, char* codigoCarta, char* nomeCidade, int populacao, float areaKm2, float pib, int pontosTuristicos) {
    Pais pais;
    strcpy(pais.estado, estado);
    strcpy(pais.codigoCarta, codigoCarta);
    strcpy(pais.nomeCidade, nomeCidade);
    pais.populacao = populacao;
    pais.areaKm2 = areaKm2;
    pais.pib = pib;
    pais.pontosTuristicos = pontosTuristicos;
    return pais;
}

// Função para imprimir um país
void imprimirPais(Pais pais) {
    printf("Estado: %s\n", pais.estado);
    printf("Código da carta: %s\n", pais.codigoCarta);
    printf("Nome da cidade: %s\n", pais.nomeCidade);
    printf("População: %d\n", pais.populacao);
    printf("Área em km²: %.2f\n", pais.areaKm2);
    printf("PIB: %.2f\n", pais.pib);
    printf("Pontos turísticos: %d\n", pais.pontosTuristicos);
}

// Função para comparar dois países
int compararPaises(Pais pais1, Pais pais2, char* atributo) {
    if (strcmp(atributo, "populacao") == 0) {
        if (pais1.populacao > pais2.populacao) return 1;
        else if (pais1.populacao < pais2.populacao) return -1;
        else return 0;
    } else if (strcmp(atributo, "areaKm2") == 0) {
        if (pais1.areaKm2 > pais2.areaKm2) return 1;
        else if (pais1.areaKm2 < pais2.areaKm2) return -1;
        else return 0;
    } else if (strcmp(atributo, "pib") == 0) {
        if (pais1.pib > pais2.pib) return 1;
        else if (pais1.pib < pais2.pib) return -1;
        else return 0;
    } else if (strcmp(atributo, "pontosTuristicos") == 0) {
        if (pais1.pontosTuristicos > pais2.pontosTuristicos) return 1;
        else if (pais1.pontosTuristicos < pais2.pontosTuristicos) return -1;
        else return 0;
    } else {
        printf("Atributo inválido!\n");
        return 0;
    }
}

int main() {
    // Definir os países
    Pais paisJogador = criarPais("São Paulo", "SP", "São Paulo", 212000000, 248.2, 2600000000, 50);
    Pais paisComputador = criarPais("Rio de Janeiro", "RJ", "Rio de Janeiro", 167000000, 43.7, 2200000000, 40);

    printf("País do jogador: \n");
    imprimirPais(paisJogador);
    printf("País do computador: \n");
    imprimirPais(paisComputador);

    char atributo[20];
    printf("Escolha um atributo (populacao, areaKm2, pib, pontosTuristicos): ");
    scanf("%s", atributo);

    int resultado = compararPaises(paisJogador, paisComputador, atributo);
    if (resultado == 1) {
        printf("Jogador venceu essa rodada!\n");
    } else if (resultado == -1) {
        printf("Computador venceu essa rodada!\n");
    } else {
        printf("Empate!\n");
    }

    return 0;
}
