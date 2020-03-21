global Agenda, sequencia, ValoresAgenda
ValoresAgenda = []
Agenda = {}
sequencia = []

'''Este vai ser o menu principal onde mostra todas as opções'''


def MenuPrincipal(Agenda, ValoresAgenda, sequencia):
    print('''    1 - Introduzir novo cliente
    2 - Associar um contacto de um cliente
    3 - Associar um DNA de um cliente
    4 - Testar gene de um DNA
    5 - Excluir um contacto de um cliente
    6 - Consultar Agenda
    7 - Gravar dados para um ficheiro
    8 - Ler dados de um ficheiro
    0 - Sair do programa''')

    escolha = int(input("Escolha uma opção: "))
    
    if escolha == 1:
        opcao1(Agenda, ValoresAgenda, sequencia)

    elif escolha == 2:
        opcao2(Agenda, ValoresAgenda, sequencia)

    elif escolha == 3:
        opcao3(Agenda, ValoresAgenda, sequencia)

    elif escolha == 4:
        opcao4(Agenda, ValoresAgenda, sequencia)

    elif escolha == 5:
        opcao5(Agenda, ValoresAgenda, sequencia)

    elif escolha == 6:
        opcao6(Agenda, ValoresAgenda, sequencia)

    elif escolha == 7:
        opcao7(Agenda, ValoresAgenda,sequencia)

    elif escolha == 8:
        opcao8(Agenda,ValoresAgenda,sequencia)

    else:
        print("Insira uma opção válida!")


'''Esta função vai ser a opção 1 ou seja vai criar um novo cliente e adicionar um contacto'''


def opcao1(Agenda, ValoresAgenda, sequencia):
    
    contactos = []

    nome = input("Insira o nome do Cliente: ")

    Agenda[nome] = contactos

    contacto = int(input("Insira o contacto do Cliente: "))

    contactos.append(contacto)

    t = True

    while t:

        contacto = int(input("Insira o contacto do Cliente: "))

        if contacto != 0:

            contactos.append(contacto)

            Agenda[nome] = contactos

        else:

            t = False

    ValoresAgenda.append(contactos)

    print(Agenda)

    MenuPrincipal(Agenda, ValoresAgenda, sequencia)


'''Esta função vai ser a opção 2 ou seja vai acrescentar um contacto a um cliente que ja exista'''


def opcao2(Agenda, ValoresAgenda, sequencia):
    
    contactos = []

    if Agenda == {}:

        opcao1(Agenda, contactos, ValoresAgenda)

    else:
        nome = input("Insira o nome do cliente para adicionar: ")

        if Agenda[nome]:

            contacto = int(input("Insira o contacto do Cliente: "))

            contactos.append(contacto)
            
            t = True

            while t:

                contacto = int(input("Insira o contacto do Cliente: "))

                if contacto != 0:

                    contactos.append(contacto)

                    Agenda[nome] = contactos

                else:

                    t = False

            ValoresAgenda.append(contactos)

            Agenda[nome] = ValoresAgenda

    print(Agenda)

    MenuPrincipal(Agenda, ValoresAgenda, sequencia)


'''Esta opção vai ser inserir uma sequencia de DNA a um cliente'''


def opcao3(Agenda, ValoresAgenda, sequencia):
    
    ValoresAgenda = []

    sequencia = []

    aminoacidos = ['A', 'T', 'G', 'C']

    if Agenda == {}:

        opcao1(Agenda, ValoresAgenda, sequencia)

    else:

        nome = input("Insira o nome do cliente para adicionar a sequência de DNA: ")

        if nome in Agenda.keys():

            ValoresAgenda = Agenda.get(nome)

            sequencia = input("Insira a sequência de DNA: ").upper()

            sequencia = [i for i in sequencia]

            for i in range(len(sequencia)):

                if sequencia[i] in aminoacidos:

                    pass

                else:

                    print("A sequência de DNA não é valida", "\n")

                    opcao3(Agenda, ValoresAgenda, sequencia)

            sequencia = "".join(sequencia)

            ValoresAgenda = ValoresAgenda.append(sequencia)

            

        else:

            print("Cliente não encontrado")

            MenuPrincipal(Agenda, ValoresAgenda, sequencia)

    print(Agenda)

    MenuPrincipal(Agenda, ValoresAgenda, sequencia)


'''Esta opção vai testar a sequencia e ver se tem o gene XPT'''


def opcao4(Agenda, ValoresAgenda, sequencia):
    if Agenda == {}:

        opcao1(Agenda,ValoresAgenda,sequencia)

    else:

        nome = input("Insira o nome do cliente para teste do seu DNA: ")

        if nome in Agenda.keys():

            sequencia = Agenda.get(nome)

            if sequencia[0:3] == "ATG" and len(sequencia) % 3 == 0:

                if sequencia[-3:] == "TAG" or "TAA" or "TGA":
                    print("O gene é XPT")

            else:
                print("O gene nao é XPT")
                
    MenuPrincipal(Agenda,ValoresAgenda,sequencia)


'''Esta opção vai apagar os contactos do cliente'''


def opcao5(Agenda,ValoresAgenda,sequencia):
    nome = input("Insira o nome do cliente: ")

    if nome in Agenda.keys():
        Agenda.pop(nome)

    MenuPrincipal(Agenda,ValoresAgenda,sequencia)


'''Esta opção vai consultar a agenda'''


def opcao6(Agenda, ValoresAgenda, sequencia):
    
    print(Agenda)

    MenuPrincipal(Agenda,ValoresAgenda,sequencia)

    
    
def opcao7(Agenda, ValoresAgenda, sequencia):
    
    Agenda = Agenda

    f = open("Agenda.txt","w")

    f.write(str(Agenda))

    f.close()
    
    MenuPrincipal(Agenda,ValoresAgenda,sequencia)
    
    
def opcao8(Agenda, ValoresAgenda, sequencia):
  try:
    with open('Agenda.txt') as f:
        for nome in Agenda:
          print(nome, file=f)
     
  except:
    texto = None

    print (texto) 
    MenuPrincipal(Agenda,ValoresAgenda,sequencia)
    
    
    
if __name__ == '__main__':
    MenuPrincipal(Agenda,ValoresAgenda,sequencia)
    
#Bernardo Augusto 2814 BINF11

