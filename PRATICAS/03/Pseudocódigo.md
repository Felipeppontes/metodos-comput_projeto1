Pseudocódigo - Utilizando o Portugol:

#-----Problema 1-----#:
função num_algarismo(algarismo)
    // Um numero inteiro positivo entre 100 e 999
    se algarismo < 100 ou algarismo > 999 então
        Escreva("O número deve estar entre 100 e 999")
        retorne num_algarismo(LeiaInteiro("Digite um número inteiro entre 100 e 999:"))
    fim se
    
    unidades <- algarismo % 10
    dezenas <- (algarismo // 10) % 10
    centenas <- algarismo // 100
    
    retorne unidades, dezenas, centenas
fim função

algarismo <- LeiaInteiro("Digite um número inteiro entre 100 e 999:")
unidades, dezenas, centenas <- num_algarismo(algarismo)

Escreva("Unidade:", unidades)
Escreva("Dezena:", dezenas)
Escreva("Centena:", centenas)

Escreva("")

#-----Problema 2-----#:
função laranjas(quant)
    // Quantidade de laranjas desejadas ao usuário
    duzias <- quant // 12
    // Se for duzia avulsas == 0, caso contrario, o resto deverá ser considerado avulsa
    avulsas <- quant % 12

    valor_duzias <- duzias * 8.35
    // Considerado o preço de R$8,35 para cada dúzia, logo R$0,70 para cada laranja avulsa
    valor_avulsas <- avulsas * 0.70

    valor_total <- valor_duzias + valor_avulsas

    retorne duzias, avulsas, valor_total
fim função

q_laranjas <- LeiaInteiro("Quantas laranjas?")

// Calcula a quantidade de laranjas e o valor total
duzias, avulsas, valor_total <- laranjas(q_laranjas)
Escreva("Quantidade de dúzias:", duzias)
Escreva("Quantidade avulsas:", avulsas)
Escreva("Valor total (R$):", arredondar(valor_total, 2))

#-----Problema 3-----#:
função calcular_numeros_perfeitos(inicio, fim)
    numeros_perfeitos <- []
    
    para num de inicio até fim faça
        divisores <- []
        para i de 1 até num faça
            se num % i == 0 então
                divisores.adicionar(i)
            fim se
        fim para
        se somar(divisores) == num então
            numeros_perfeitos.adicionar(num)
        fim se
    fim para
    
    retorne numeros_perfeitos
fim função

inicio <- LeiaInteiro("Digite o número de início do intervalo (mínimo: 2): ")
fim <- LeiaInteiro("Digite o número de fim do intervalo (máximo: 103): ")

enquanto inicio < 2 ou fim > 103 faça
    Escreva("Intervalo inválido. Digite novamente.")
    inicio <- LeiaInteiro("Digite o número de início do intervalo (mínimo: 2): ")
    fim <- LeiaInteiro("Digite o número de fim do intervalo (máximo: 103): ")
fim enquanto

numeros_perfeitos <- calcular_numeros_perfeitos(inicio, fim)

Escreva("Números perfeitos encontrados no intervalo [", inicio, "-", fim, "]:")
se tamanho(numeros_perfeitos) > 0 então
    para cada numero em numeros_perfeitos faça
        Escreva(numero)
    fim para
senão
    Escreva("Nenhum número perfeito encontrado no intervalo.")
fim se

Escreva("")

#-----Problema 4-----#:
função calcular_media(valores)
    soma <- somar(valores)
    media <- soma / tamanho(valores)
    retorne arredondar(media, 3)
fim função

valores <- []
valor <- 0

enquanto valor >= 0 faça
    valor <- LeiaReal("Digite um valor (digite um número negativo para sair): ")
    se valor >= 0 então
        valores.adicionar(valor)
    fim se
fim enquanto

media <- calcular_media(valores)

Escreva("Média:", formatar(media, "0.000"))

se media > 5 então
    Escreva("A média", formatar(media, "0.000"), "está acima do limiar estabelecido.")
fim se
