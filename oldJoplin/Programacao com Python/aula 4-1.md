aula 4

#hora = int(input())

#minuto = int(input())

#hora_convertida = hora * 60

#tempo = hora_convertida + minuto

#print("hora=\\n", hora, "minuto=\\n", minuto, "tempo=\\n", tempo)

#minutos = 80

#minutos_hora = minutos

#tempo = int(minutos/60)

#min = minutos - tempo * 60

#print(tempo,":" min)

minutos = 80

min = minutos%60

hora = int(minutos/60)

print(hora, min)