# Aula


def recomendar_sala(participantes, tipo_reuniao):
    # Validação da entrada
    if participantes < 0:
        return "Número de participantes inválido!"
    
    # Se for executiva, sempre é sala grande
    if tipo_reuniao.lower() == "executiva":
        return "Sala Grande"
    
    # Se for normal, segue as faixas de quantidade
    if participantes <= 5:
        return "Sala Pequena"
    elif participantes <= 15:
        return "Sala Média"
    else:
        return "Sala Grande"


# Interface com o usuário
try:
    participantes = int(input("Digite o número de participantes: "))
    tipo_reuniao = input("Digite o tipo de reunião (normal ou executiva): ")

    sala_recomendada = recomendar_sala(participantes, tipo_reuniao)
    print("Sala recomendada:", sala_recomendada)

except ValueError:
    print("Entrada inválida! Digite um número inteiro para participantes.")
