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





Novo código
# Lista de 15 caminhões disponíveis e suas características
caminhoes = [
    {"nome": "Volvo FH 540", "tipo": "cavalo-mecânico", "combustivel": "diesel", "preco": 650000},
    {"nome": "Scania R 450", "tipo": "cavalo-mecânico", "combustivel": "diesel", "preco": 700000},
    {"nome": "Mercedes-Benz Actros 2651", "tipo": "cavalo-mecânico", "combustivel": "diesel", "preco": 720000},
    {"nome": "DAF XF 530", "tipo": "cavalo-mecânico", "combustivel": "diesel", "preco": 680000},
    {"nome": "Iveco Hi-Way 480", "tipo": "cavalo-mecânico", "combustivel": "diesel", "preco": 600000},

    {"nome": "Volkswagen Constellation 24.280", "tipo": "truck", "combustivel": "diesel", "preco": 420000},
    {"nome": "Mercedes-Benz Atego 2430", "tipo": "truck", "combustivel": "diesel", "preco": 400000},
    {"nome": "Ford Cargo 2429", "tipo": "truck", "combustivel": "diesel", "preco": 390000},
    {"nome": "Iveco Tector 240E30", "tipo": "truck", "combustivel": "diesel", "preco": 410000},
    {"nome": "Volvo VM 270", "tipo": "truck", "combustivel": "diesel", "preco": 430000},

    {"nome": "Volkswagen Delivery 11.180", "tipo": "leve", "combustivel": "diesel", "preco": 230000},
    {"nome": "Mercedes-Benz Accelo 1016", "tipo": "leve", "combustivel": "diesel", "preco": 250000},
    {"nome": "Hyundai HD80", "tipo": "leve", "combustivel": "diesel", "preco": 200000},
    {"nome": "Ford F-4000", "tipo": "leve", "combustivel": "diesel", "preco": 220000},
    {"nome": "Iveco Daily 70C17", "tipo": "leve", "combustivel": "diesel", "preco": 210000},
]

def recomendar_caminhoes(caminhoes, tipo, combustivel, preco_max):
    recomendados = [
        caminhao for caminhao in caminhoes
        if caminhao["tipo"] == tipo and caminhao["combustivel"] == combustivel and caminhao["preco"] <= preco_max
    ]
    return recomendados

def formatar_preco(valor):
    return f"R$ {valor:,.0f}".replace(",", ".")  # deixa tipo R$ 650.000

print("🚛 Bem-vindo ao sistema de escolha de caminhão novo!")
print("Responda algumas perguntas para receber uma sugestão:\n")

tipos_validos = ["cavalo-mecânico", "truck", "leve"]
combustiveis_validos = ["diesel"]

# Validação da entrada do tipo
while True:
    tipo = input("Qual tipo de caminhão você prefere? (cavalo-mecânico/truck/leve): ").strip().lower()
    if tipo in tipos_validos:
        break
    print("❌ Tipo inválido. Escolha entre: cavalo-mecânico, truck ou leve.")

# Validação da entrada do combustível
while True:
    combustivel = input("Qual tipo de combustível você prefere? (diesel): ").strip().lower()
    if combustivel in combustiveis_validos:
        break
    print("❌ Combustível inválido. Atualmente só trabalhamos com diesel.")

# Validação do preço
while True:
    try:
        preco_max = int(input("Qual o valor máximo que você quer pagar? (em reais): "))
        if preco_max > 0:
            break
        else:
            print("❌ Digite um valor maior que zero.")
    except ValueError:
        print("❌ Digite um número válido.")

# Buscar recomendações
print("\n🔎 Caminhões sugeridos para você:\n")
resultados = recomendar_caminhoes(caminhoes, tipo, combustivel, preco_max)

if resultados:
    for i, caminhao in enumerate(resultados, start=1):
        print(f"{i}. {caminhao['nome']}")
        print(f"   Tipo: {caminhao['tipo'].capitalize()} | Combustível: {caminhao['combustivel'].capitalize()} | Preço: {formatar_preco(caminhao['preco'])}\n")
else:
    print("⚠️ Nenhum caminhão encontrado com as suas preferências.")
