El comando **`no auto-summary`** en EIGRP*EIGRP* desactiva la **resumen automático de rutas (automatic summarization)**. Este resumen automático es una característica que, por defecto, anuncia las redes en sus **límites de clase** (classful boundaries), lo cual puede causar problemas en redes modernas que usan subredes (CIDR, redes sin clase).

---

### ¿Qué hace el resumen automático?

Si **no usas** `no auto-summary`, EIGRP **resume automáticamente las subredes** en las interfaces fronterizas y anuncia únicamente la red de clase completa (classful). Esto puede causar problemas si hay subredes discontinuas o si necesitas anunciar subredes específicas.

#### Ejemplo sin `no auto-summary`:

Supongamos que tienes estas redes configuradas en un router:

- **192.168.1.0/24**
- **192.168.2.0/24**

Si la interfaz del router está conectada a una red diferente (por ejemplo, 10.0.0.0/8) y **no usas `no auto-summary`**, EIGRP **resume automáticamente** estas redes y las anunciará como **192.168.0.0/16** (el límite de clase para las redes 192.168.0.0).

Esto puede confundir a otros routers y causar problemas de conectividad, ya que las subredes específicas (192.168.1.0 y 192.168.2.0) no se anunciarán correctamente.

---

### ¿Qué pasa con `no auto-summary`?

Cuando activas el comando `no auto-summary`, EIGRP anuncia **todas las subredes específicas** tal y como están configuradas, sin resumirlas automáticamente a su red de clase.

#### Ejemplo con `no auto-summary`:

- Redes configuradas en el router:
    - **192.168.1.0/24**
    - **192.168.2.0/24**

Con `no auto-summary`, EIGRP anunciará:

- 192.168.1.0/24
- 192.168.2.0/24

Así, los routers vecinos sabrán exactamente qué subredes están disponibles y no habrá confusión por un resumen erróneo.

---

### ¿Cuándo usar `no auto-summary`?

- **Siempre que uses subredes (CIDR)**: En redes modernas, casi siempre utilizas subredes, por lo que **es buena práctica usar `no auto-summary`**.
- **Cuando tienes subredes discontinuas**: Si las subredes de una misma red no están directamente conectadas, el resumen automático puede ocultar rutas importantes. `no auto-summary` evita este problema.

#### Subredes discontinuas:

Si tienes subredes como estas:

- **192.168.1.0/24** en R1
- **192.168.2.0/24** en R3 (y R2 conecta ambos)

Sin `no auto-summary`, el resumen automático podría anunciar solo 192.168.0.0/16, ocultando las subredes específicas y causando pérdida de conectividad.

---

### Configuración del comando:

En el proceso de configuración de EIGRP:

bash

Copiar código

`router eigrp 100  no auto-summary`

---

En resumen, **`no auto-summary`** asegura que EIGRP anuncie subredes específicas en lugar de hacer un resumen automático a nivel de clase. Esto es esencial para la precisión y estabilidad en redes modernas. 😊