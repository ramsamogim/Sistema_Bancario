# Sistema_Bancario
Menu = """
----------------------- Menu ------------------------

[D] : Depositar
[S] : Saque
[E] : Extrato
[O] : Sair

-----------------------------------------------------
"""
saldo = 0
limite = 500
extrato = ""
n_saques = 0
LIMITE_SAQUES = 3

while True:
    opcao = input(Menu)

    if opcao == "D":
        valor = float(input("iNFORME O VALOR DO DEPÓSITO: "))

        if valor > 0:
            print(f"Deposito realizado!!! R$ {valor:.2f}\n")
            saldo += valor
            extrato += f" Depósito realizado: {valor:.2f}\n"

        else:
            print(" Operação não realizada, o valor depositado está errado")
    elif opcao == "S":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = n_saques == LIMITE_SAQUES

        if excedeu_saldo:
            print("impossível de sacar esse valor, saldo insuficiente.")

        elif excedeu_limite:
            print(
                "O valor do saque excedeu o limite de saque, faça o saque de um valor menor.")

        elif excedeu_saques:
            print("Operação não permitida, Número máximo de saques excedido!!!")

        elif valor > 0:
            print(f"Saque realizado com sucesso, Saque de R$ {valor:.2f}\n")
            saldo -= valor  # igual a saldo -= valor
            # extrato = extrato + f"Saque:  R$ {valor:2f}\n
            extrato += f"Saque:  R$  {valor:.2f}\n"
            n_saques += 1  # n_saques = n_saques + 1

        else:
            print("O valor informado está errado, tente novamente.")

    elif opcao == "E":
        print("\n -------------- Extrato ---------------") # aqui o sistema irá mostrar que não teve movimentações, quando realmente não as teve. E ele exibirá o extrato quando houver movimentações que foram concatenadas no extrato anteriormente.
        print(" Não foram realizados movimentações." if not extrato else extrato)
        print(f"\n Saldo:  R$  {saldo:.2f}")
        print("-----------------------------------------")

    elif opcao == "O":
        break
    else:
        print("Operação inválida, por favor selecione uma opção novamente")
