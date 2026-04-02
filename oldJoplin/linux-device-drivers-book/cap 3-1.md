ls -l em /dev/ onde ficam os dispositivos especiais do systema:

![4ac3fa30ef3cdd0f80c65c14e1b9f885.png](../_resources/4ac3fa30ef3cdd0f80c65c14e1b9f885-1.png)

b para bloco e c para char

Their major numbers are 1, 4, 7, and 10, while the minors are 1, 3, 5, 64, 65, and 129.

mas acho que foi trocado

o numero maior é usado para identificar o driver associado ao dispositivo.

o menor é usado para referenciar qual dispositivo está sendo usado. O kernel faz isso automaticamente criando links ou vc pode usar os numeros menores.