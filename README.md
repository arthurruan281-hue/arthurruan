import random


 EXTRACT (Extração)


usuarios = [
    {"nome": "Ana", "conta": "1234", "cartao": "9999"},
    {"nome": "Bruno", "conta": "5678", "cartao": "8888"},
    {"nome": "Carlos", "conta": "9012", "cartao": "7777"},
    {"nome": "Daniela", "conta": "3456", "cartao": "6666"},
]


 TRANSFORM (Transformação)


mensagens = [
    "Lembre-se de economizar todos os meses.",
    "Investir é pensar no seu futuro.",
    "Organize suas finanças e evite dívidas.",
    "Pequenos gastos diários fazem grande diferença."
]

def gerar_mensagem(usuario):
    mensagem = random.choice(mensagens)
    return f"Olá {usuario['nome']}, {mensagem}"

dados_transformados = []

for usuario in usuarios:
    mensagem = gerar_mensagem(usuario)
    novo_registro = {
        "nome": usuario["nome"],
        "conta": usuario["conta"],
        "cartao": usuario["cartao"],
        "mensagem": mensagem
    }
    dados_transformados.append(novo_registro)


 LOAD (Carregamento)


with open("saida_usuarios.txt", "w", encoding="utf-8") as arquivo:
    for usuario in dados_transformados:
        linha = f"{usuario['nome']} | {usuario['conta']} | {usuario['cartao']} | {usuario['mensagem']}\n"
        arquivo.write(linha)

print("Pipeline ETL executado com sucesso!")
