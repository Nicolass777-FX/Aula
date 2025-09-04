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



    Novo código
   # Lista de 20 carros esportivos
carros = [
    {"nome": "Ferrari 488 GTB", "marca": "Ferrari", "potencia": 670, "combustivel": "gasolina", "preco": 2500000},
    {"nome": "Lamborghini Huracán Evo", "marca": "Lamborghini", "potencia": 640, "combustivel": "gasolina", "preco": 2700000},
    {"nome": "Porsche 911 Turbo S", "marca": "Porsche", "potencia": 650, "combustivel": "gasolina", "preco": 1600000},
    {"nome": "McLaren 720S", "marca": "McLaren", "potencia": 720, "combustivel": "gasolina", "preco": 3000000},
    {"nome": "Aston Martin Vantage", "marca": "Aston Martin", "potencia": 510, "combustivel": "gasolina", "preco": 1200000},

    {"nome": "Chevrolet Corvette Stingray", "marca": "Chevrolet", "potencia": 495, "combustivel": "gasolina", "preco": 800000},
    {"nome": "Nissan GT-R Nismo", "marca": "Nissan", "potencia": 600, "combustivel": "gasolina", "preco": 1500000},
    {"nome": "Audi R8 V10 Performance", "marca": "Audi", "potencia": 620, "combustivel": "gasolina", "preco": 1300000},
    {"nome": "BMW M4 Competition", "marca": "BMW", "potencia": 510, "combustivel": "gasolina", "preco": 700000},
    {"nome": "Mercedes-AMG GT R", "marca": "Mercedes-Benz", "potencia": 585, "combustivel": "gasolina", "preco": 1400000},

    {"nome": "Toyota Supra GR", "marca": "Toyota", "potencia": 387, "combustivel": "gasolina", "preco": 450000},
    {"nome": "Ford Mustang Mach 1", "marca": "Ford", "potencia": 483, "combustivel": "gasolina", "preco": 500000},
    {"nome": "Jaguar F-Type R", "marca": "Jaguar", "potencia": 575, "combustivel": "gasolina", "preco": 1100000},
    {"nome": "Maserati MC20", "marca": "Maserati", "potencia": 630, "combustivel": "gasolina", "preco": 2200000},
    {"nome": "Lotus Evora GT", "marca": "Lotus", "potencia": 416, "combustivel": "gasolina", "preco": 900000},

    {"nome": "Alfa Romeo Giulia Quadrifoglio", "marca": "Alfa Romeo", "potencia": 510, "combustivel": "gasolina", "preco": 700000},
    {"nome": "Dodge Challenger SRT Hellcat", "marca": "Dodge", "potencia": 717, "combustivel": "gasolina", "preco": 950000},
    {"nome": "Tesla Roadster", "marca": "Tesla", "potencia": 1000, "combustivel": "elétrico", "preco": 1800000},
    {"nome": "Koenigsegg Jesko", "marca": "Koenigsegg", "potencia": 1280, "combustivel": "gasolina", "preco": 12000000},
    {"nome": "Pagani Huayra", "marca": "Pagani", "potencia": 730, "combustivel": "gasolina", "preco": 14000000},
]

# Função para recomendar carros dentro do orçamento
def recomendar_carros(lista, preco_max):
    return [carro for carro in lista if carro["preco"] <= preco_max]

# Função para formatar preço em R$
def formatar_preco(valor):
    return f"R$ {valor:,.0f}".replace(",", ".")

# Programa principal
def main():
    print("🏎️ Bem-vindo ao sistema de recomendação de carros esportivos!\n")

    try:
        preco_max = int(input("💰 Qual o valor máximo que você quer gastar? (em reais): "))
        recomendados = recomendar_carros(carros, preco_max)

        print("\n🔎 Carros dentro do seu orçamento:\n")

        if recomendados:
            for i, carro in enumerate(recomendados, start=1):
                print(f"{i}. {carro['nome']} ({carro['marca']})")
                print(f"   Potência: {carro['potencia']} cv | Combustível: {carro['combustivel'].capitalize()} | Preço: {formatar_preco(carro['preco'])}")
                print("   " + "-"*60)
        else:
            print("⚠️ Nenhum carro encontrado nesse valor.")

    except ValueError:
        print("❌ Digite um número válido.")

# Executar programa
if __name__ == "__main__":
    main()


