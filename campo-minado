"""
Created on Thu Apr 12 20:35:18 2018
@author: Matheus Santana
"""
from os import system, name
from random import randint
from time import sleep

def cria_campo():
    campo = []
    for i in range(0,5):
        for j in range(0,5):
            tipoCampo = randint(0, 2)
            if tipoCampo == 0:
                campo.append((i, j, 'Booom'))
            else:
                campo.append((i, j, 'Uffaa'))
    return campo

def show_campo(campoMinadoUsado, pontuacaoMaxima):
    pontuacao = 0
    for x, y, estado in campoMinadoUsado:
        if estado == 'Uffaa':
            pontuacao += 10
    print('==============================================')
    print('                CAMPO MINADO                   ')
    print('==============================================')
    print('Pontuação: %.02d                 Recorde: %.2d' % (pontuacao, pontuacaoMaxima))
    print('==============================================\n')
    for i in range(0, 5):
        line = ['  ']
        for j in range(0, 5):
            if (i, j, 'Uffaa') in campoMinadoUsado:
                line.append('|     |')
            elif (i, j, 'Booom') in campoMinadoUsado:
                line.append('|Booom|')
            else:
                line.append('| ' + str(i) + ',' + str(j) + ' |')
        if line != None:
            print(*line)
    return pontuacao

campoMinado = cria_campo()
campoMinadoUsado = []
pontuacao = 0
pontuacaoMaxima = 0
perdeu = False
while perdeu == False:
    system('cls' if name == 'nt' else 'clear')
    pontuacao = show_campo(campoMinadoUsado, pontuacaoMaxima)
    
    i = -1
    while i < 0 or i > 4:
        try:
            i = int(input('\nInforme a linha: '))
        except:
            i = 5
        if i < 0 or i > 4:
            print('Linha informada inválida.')
    
    j = -1
    while j < 0 or j > 4:
        try:
            j = int(input('Informe a coluna: '))
        except:
            j = 5
        if j < 0 or j > 4:
            print('Coluna informada inválida.')
    
    for x, y, estado in campoMinado:
        if i == x and j == y:
            campoMinadoUsado.append((i, j, estado))
            break
    
    for x, y, estado in campoMinadoUsado:
        if estado == 'Booom':
            system('cls' if name == 'nt' else 'clear')
            pontuacao = show_campo(campoMinadoUsado, pontuacaoMaxima)
            print('\nVocê Perdeu !!!')
            
            while True:
                continuaJogo = input('Deseja tentar novamente? (S/N)')
                if continuaJogo == 'S' or continuaJogo == 's':
                    campoMinado = cria_campo()
                    campoMinadoUsado = []
                    if pontuacaoMaxima < pontuacao:
                        pontuacaoMaxima = pontuacao
                    pontuacao = 0
                    break
                elif continuaJogo == 'N' or continuaJogo == 'n':
                    perdeu = True
                    sleep(3)
                    break
                else:
                    print('Opção inválida !!!')
