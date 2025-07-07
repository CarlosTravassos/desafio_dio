# desafio_dio
Repositório referente ao desafio de criação de um sistema bancário

menu = """\n
================ MENU ================
[d]\tDepositar
[s]\tSacar
[e]\tExtrato
[q]\tSair
=> """
    


saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3


while True:

    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Não foi possível realizar o depósito! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Não foi possível realizar o saque! Saldo insuficiente.")

        elif excedeu_saques:
            print("Não foi possível realizar o saque! Limite excedido.")

        elif excedeu_limite:
            print("Não foi possível realizar o saque! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            
            extrato += f"Saque: R$ {valor: .f}\n"

            numero_saques += 1

        else:
            print("Não foi possível continuar com a operação! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================EXTRATO================")
        print("Não foram realizadas movimentações." if not extrato else  extrato)
        print(f"\nSaldo: R$ {saldo: .2f}")
        print("========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
