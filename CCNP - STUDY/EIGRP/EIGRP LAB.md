
![[Pasted image 20241219183459.png]]


Dispositivos necesarios:
- 3 routers Cisco (puedes usar imágenes de IOS como c3725 o c7200)
- Switches (opcional, para conectar PCs si deseas probar conectividad end-to-end)

Topología sugerida:
- Conecta los 3 routers en una topología triangular usando interfaces seriales
- Agrega interfaces loopback en cada router para simular redes internas

Pasos del laboratorio:

1. Configura las direcciones IP en todas las interfaces (seriales y loopbacks)

2. Habilita EIGRP en los routers:
   - Configura el sistema autónomo EIGRP
   - Anuncia las redes conectadas

3. Verifica las adyacencias EIGRP entre los routers

4. Examina la tabla de topología EIGRP y la tabla de enrutamiento

5. Prueba la conectividad entre las redes loopback

Retos a afrontar:
- Comprender cómo EIGRP establece adyacencias
- Interpretar la información de la tabla de topología EIGRP
- Entender cómo EIGRP selecciona las mejores rutas

Áreas de enfoque:
- Configuración básica de EIGRP
- Verificación de operaciones EIGRP usando comandos como "show ip eigrp neighbors" y "show ip eigrp topology"
- Ajuste de la métrica EIGRP modificando el ancho de banda y el retardo en las interfaces
- Implementación de balanceo de carga EIGRP

Este laboratorio te permitirá aprender los fundamentos de EIGRP, incluyendo su configuración, verificación y troubleshooting básico.

[[Comandos para montar EIGRP]]








Citations:
[1] https://repository.udistrital.edu.co/server/api/core/bitstreams/c1ab600e-9b10-4bcb-8b1f-10ad4bc8e2cd/content
[2] https://www.imd.guru/redes/gns3/labs/eigrp-balanceando-carga.html
[3] https://www.imd.guru/redes/gns3/labs/eigrp-configuracion-ancho-de-banda-y-adyacencias.html
[4] https://www.youtube.com/watch?v=mn0t_eW0yHU
[5] https://www.youtube.com/watch?v=pDjMHNs-TZU
[6] https://www.docsity.com/es/docs/simulacion-eigrp-en-gns3/7011681/