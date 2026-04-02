
sinais:

em processos assincronos, fazer:

def processar_fatia_bolo_mais_sorvete:
	sinal.pause()
	with update_fatia:
		if fatia in fatia_bolo:
			try:
				entregar_fatia_cliente()
	sinal.continue() ->