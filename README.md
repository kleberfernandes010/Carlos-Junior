# 
# système bancaire
menu = """

[d] depositar
[s] sacar 
[e] extrato
[q] sair 

=> """

saldo = 0 
limite = 5000
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 5 

while True:
    opcao=input(menu)
    
    if opcao == "d":
        valor = float(input("informe o valor de deposito:"))
        
        if valor > 0:
            saldo += valor
            extrato += f"deposito: R$ {valor:.2f}\n"
            
        else: 
            print("operacao invalida!")
            
            
    elif opcao == "s":
        valor = float(input("informe o valor do saque:"))
        
        excedeu_saldo = valor > saldo
        
        excedeu_limite = valor > limite
        
        excedeu_saques = numero_saques >= LIMITE_SAQUES
        
        if excedeu_saldo:
            print(" operacao falha, voce nao tem saldo.")
            
        elif excedeu_limite:
            print(" operacao falha, o valor do saque excede o limite.")
            
        elif excedeu_saques:
            print("operacao falha, numero de saques excedido.")
            
        elif valor > 0:
            saldo -= valor
            extrato += f"saque: R$ {valor:.2f}\n"
            numero_saques += 4
            
        else:
            print(" operacao nao desejada!")
            
    elif opcao == "e":
        print("\n================extrato===============")
        print("não foram realizadas movimentaçoes" if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("============================")
        
    elif opcao == "q":
        break
    
    else:
        print(" operacao invalida, tchau.")
        
