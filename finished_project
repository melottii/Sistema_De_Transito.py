import pickle


def user(motoristas):   #1 Cadastro dos novos motoristas.
    driver = input('Escreva sua CNH: ')
    if driver in motoristas:
        print ('ERRO. CNH já cadastrado.')
    else:
        date = input('Nome do motorista: '), ((input('Data de nascimento\n Dia:')), input(' Mês:'), input(' Ano:'))
        motoristas[driver] = date
        return (motoristas)


def new_vehicle(veiculos):  #2 Cadastro dos novos veículos.
    vehicle_data = input('Placa do carro (Exemplo: XXX 0000): ')
    if len(vehicle_data) == 8:
        if vehicle_data not in veiculos:
            driver, type, color = input('Escreva sua CNH: '), input('Qual carro? '), input('Cor do carro: ')
            veiculos[f'{vehicle_data}'] = driver, type, color
            return (veiculos)
    else:
        print ('ERRO. Placa inválida, o tamanho do texto inserido não condiz com a quantidade de algarismos das placas.')


def vehicle(motoristas, veiculos):  #3 Alteração de dono dos veículos.
    vehicle_data = input('Placa do carro (Exemplo: XXX 0000): ')
    if len(vehicle_data) == 8:
        driver = input('Escreva sua CNH: ')
        if vehicle_data in veiculos:
            type, color = veiculos[f'{vehicle_data}'][1], veiculos[f'{vehicle_data}'][2]
            if driver in motoristas:
                veiculos[vehicle_data] = driver, type, color
                return (veiculos)
            else:
                print ('Erro. Motorista não cadastrado.')
        else:
            print ('Erro. Veículo não cadastrado.')
    else:
        print ('ERRO. Placa inválida, o tamanho do texto inserido não condiz com a quantidade de algarismos das placas.')


def infraction(infracoes, naturezas, veiculos): #4 Cadastro de novas infrações.
    plate_number = input('Placa do veículo (COM ESPAÇO): ')
    if plate_number in veiculos:
        date = int(input('Dia:')), int(input('Mês:')), int(input('Ano:'))
        ticket_seriousness = int(input('1 (Infração leve) \n2 (Infração média) \n3 (Infração Grave) \n'
        '4 (Infração Gravíssima) \nQual a gravidade da sua infração? '))
        if ticket_seriousness >= 1 and ticket_seriousness <=4:
            if ticket_seriousness == 1:
                ticket_seriousness = 'Leve'
                naturezas['Leve'] += 1
            elif ticket_seriousness == 2:
                ticket_seriousness = 'Media'
                naturezas['Media'] += 1
            elif ticket_seriousness == 3:
                ticket_seriousness = 'Grave'
                naturezas['Grave'] += 1
            else:
                ticket_seriousness = 'Gravissima'
                naturezas['Gravissima'] += 1
            note = ((len(infracoes)+1), date, plate_number, ticket_seriousness)
            infracoes.append(note)
            return (infracoes)
    else:
        print ('Veículo ainda não foi cadastrado no sistema.')


def menu(motoristas, veiculos, infracoes, naturezas):   #Menu principal
    selection = int(input('\nMAIN MENU\nDeseja fazer qual operação?\n1 = Salvar um novo motorista \n2 = Salvar um novo'
     ' veículo \n3 = Alterar proprietário de um veículo \n4 = Cadastrar uma nova infração \n5 = Sair\nOperação: '))
    while selection >= 1 and selection <=4:
        if selection == 1:
            user(motoristas)
        elif selection == 2:
            new_vehicle(veiculos)
        elif selection == 3:
            vehicle(motoristas, veiculos)
        elif selection == 4:
            infraction(infracoes, naturezas, veiculos)
        selection = int(input('Deseja fazer outra operação?\n1 = Salvar um novo motorista \n2 = Salvar um novo veículo \n'
        '3 = Alterar proprietário de um veículo \n4 = Cadastrar uma nova infração \n5 = Sair\nOperação: '))
    return (motoristas, veiculos, infracoes, naturezas)


def main(): #Manipulação das informações .bin (visualização e alteração).
    with open ('multas.bin', 'rb') as file:
        motoristas, veiculos, infracoes, naturezas = pickle.load(file), pickle.load(file), pickle.load(file), pickle.load(file)
    menu(motoristas, veiculos, infracoes, naturezas)
    with open('multas.bin', 'wb') as file:
        pickle.dump(motoristas, file), pickle.dump(veiculos, file), pickle.dump(infracoes, file), pickle.dump(naturezas, file)
        

main()
