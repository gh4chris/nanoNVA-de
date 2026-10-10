
# NanoVNA para principiantes: Medir y entender antenas correctamente

Un NanoVNA es una de las herramientas más útiles que puedes añadir a tu mesa de radioafición o de electrónica. Te ayuda a comprobar y ajustar antenas, encontrar frecuencias de resonancia, observar el SWR (ROE) en todo un rango de frecuencias, visualizar impedancias, medir filtros y detectar problemas en cables o componentes de RF.

El NanoVNA es pequeño, asequible y sorprendentemente potente. Aun así, no es un aparato que se conecta y cuya primera lectura muestra automáticamente toda la verdad. Para obtener resultados útiles, debes elegir el rango de frecuencias adecuado, calibrar en el punto correcto, usar la conexión de medición apropiada y entender lo que significan las curvas que se muestran.

Por eso, esta guía no muestra cada menú individual. Responde a la pregunta práctica más importante:

> **Veo esta curva. ¿Qué significa para mi antena y qué debo hacer a continuación?**

---

## ¿Qué es un NanoVNA?

![Figura 1: Vista general del dispositivo NanoVNA con conexiones y controles](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/f5ada94be0.png)

*Figura 1: Vista general del dispositivo NanoVNA con conexiones y controles*

VNA significa „Vector Network Analyzer", es decir, analizador de redes vectorial. Suena más complicado de lo que necesita ser para empezar.

Dicho de forma sencilla, el NanoVNA emite una señal de alta frecuencia muy pequeña y mide qué le sucede a esta señal. Al hacerlo, no solo registra la intensidad, sino también la fase de la señal. Con esta información, el aparato calcula, entre otras cosas, el SWR, la impedancia, la pérdida de retorno (Return Loss) y la representación en la carta de Smith.

Con un NanoVNA puedes, por ejemplo:

- comprobar la frecuencia de resonancia de una antena,
- ajustar un dipolo o una antena vertical,
- evaluar la adaptación de una antena a un sistema de 50 ohmios,
- encontrar varias resonancias de una antena multibanda,
- examinar filtros y atenuadores,
- comparar el estado antes y después de una adaptación,
- examinar cables, conectores y otros componentes de RF.

Debes mantener expectativas realistas. Un NanoVNA no es un laboratorio de alto rendimiento calibrado. Sin embargo, para la construcción de antenas, radioafición, radio CB, Meshtastic, proyectos SDR y muchos experimentos de electrónica, es una herramienta excelente.

Sus resultados solo son tan fiables como la configuración de medición. Conectores flojos, adaptadores innecesarios, cables inadecuados o una calibración incorrecta pueden destacar más que el propio objeto de prueba. Especialmente a frecuencias más altas, la cadena de conexiones debe ser corta, limpia e invariable.

---

## ¿Qué mide el NanoVNA?

![Figura 2: Flujo de señal desde el NanoVNA a través del cable coaxial hacia la antena y de vuelta](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/cd57317574.png)

*Figura 2: Flujo de señal desde el NanoVNA a través del cable coaxial hacia la antena y de vuelta*

Cuando el NanoVNA examina una antena, envía una señal a través del cable coaxial hacia la antena.

Una antena bien adaptada absorbe gran parte de la potencia suministrada. Una desadaptación provoca, en cambio, que parte de la señal se refleje de vuelta hacia el NanoVNA. El NanoVNA mide esta reflexión.

A partir de la misma medición básica, el aparato puede calcular diferentes vistas:

- SWR,
- LOGMAG o S11 en dB,
- Return Loss (pérdida de retorno),
- Resistencia R,
- Reactancia X,
- Impedancia compleja R + jX,
- Carta de Smith,
- Fase.

Estas indicaciones no se contradicen entre sí. Simplemente observan el mismo comportamiento eléctrico desde diferentes puntos de vista.

---

## Entender correctamente S11 y S21

![Figura 3: Comparación entre la medición de reflexión S11 y la medición de transmisión S21](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/c7cef7afb1.png)

*Figura 3: Comparación entre la medición de reflexión S11 y la medición de transmisión S21*

En muchos modelos de NanoVNA, la primera conexión se denomina Puerto 1, CH0 o S11. La segunda conexión lleva designaciones como Puerto 2, CH1 o S21, según el dispositivo.

### S11: ¿Qué regresa?

Para una medición de antena, normalmente usas el Puerto 1.

S11 describe la reflexión en la entrada. Con ello se puede investigar:

- cuánto refleja una antena,
- cuán alto es el SWR,
- dónde se encuentra una resonancia,
- qué impedancia está presente,
- si el objeto de prueba se comporta de forma capacitiva o inductiva.

S11 no es una conexión física en sí mismo, sino la designación de la magnitud de medición. En la práctica, aun así puedes recordar:

> **Antena al Puerto 1, luego mostrar S11.**

### S21: ¿Qué lo atraviesa?

Para una medición de transmisión, el objeto de prueba se conecta entre el Puerto 1 y el Puerto 2.

S21 describe cuánta señal llega del primer puerto al segundo. Con ello se pueden examinar, por ejemplo:

- filtros paso bajo, paso alto y paso banda,
- atenuadores,
- cables coaxiales,
- circuitos de bloqueo (traps),
- ciertas construcciones de baluns y choques de modo común.

Para empezar, se aplica:

> **Las antenas generalmente se miden con S11. Los filtros y las vías de transmisión, generalmente con S21.**

---

## Elegir sensatamente el rango de frecuencias

Antes de calibrar, ajustas el rango de frecuencias que realmente deseas examinar después.

Para una antena de 40 metros, por ejemplo, podrías elegir para una primera visión general un rango alrededor de la banda de 40 metros. Para una antena de 868 MHz, eliges un rango correspondientemente adecuado alrededor de la frecuencia de operación deseada.

Un rango de frecuencias extremadamente amplio parece claro, pero tiene desventajas:

- las resonancias estrechas pueden pasarse por alto,
- los detalles individuales se representan peor,
- los puntos de medición disponibles se distribuyen en un rango mayor.

Un flujo de trabajo probado consta de dos pasos:

1. Primero medir un rango algo más amplio para la visión general.
2. Después ajustar el rango interesante de forma más estrecha y calibrar de nuevo.

La calibración pertenece al rango de frecuencias elegido. Si cambias significativamente las frecuencias de inicio y de parada, debes calibrar de nuevo.

---

## Calibración: el paso más importante

![Figura 4: Calibración OSL y SOLT como un proceso claro](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/8689768173.png)

*Figura 4: Calibración OSL y SOLT como un proceso claro*

Una calibración le muestra al NanoVNA cómo se comportan el aparato de medición, las conexiones y la cadena de medición utilizada hasta el plano de referencia.

Sin una calibración adecuada, el NanoVNA no puede distinguir limpiamente entre el comportamiento del objeto de prueba y los errores sistemáticos de la configuración de medición.

### Para antenas: Open, Short y Load

Para una medición de antena puramente S11, normalmente basta una calibración de un puerto con:

1. **Open:** terminación abierta,
2. **Short:** cortocircuito,
3. **Load:** terminación de 50 ohmios lo más precisa posible.

Este procedimiento también se denomina calibración OSL.

El procedimiento simplificado es:

1. Ajustar el rango de frecuencias deseado.
2. Restablecer la calibración anterior.
3. Conectar Open en el futuro plano de referencia y medir.
4. Conectar Short y medir.
5. Conectar la carga de 50 ohmios y medir.
6. Finalizar y guardar la calibración.
7. Comprobar que la corrección está activa.

### Para mediciones de transmisión: además Thru

Si deseas medir S21, necesitas adicionalmente una transmisión definida entre los dos puertos. Este paso se llama **Thru**.

Open, Short, Load y Thru se denominan conjuntamente calibración SOLT. Thru generalmente no es necesario para una medición simple de antena S11, pero según el modelo de NanoVNA y el firmware puede ser parte del proceso de calibración ofrecido. La estructura de menús difiere entre dispositivos y versiones de firmware.

### Después de la calibración, no cambiar nada más

Un principio importante es:

> **Todo lo que cambia entre la calibración y la medición puede invalidar la calibración.**

Si insertas posteriormente un adaptador, otro cable o un conector adicional, debes calibrar de nuevo.

Los conectores también deben estar firmes durante la medición. No deben moverse, pero tampoco deben apretarse con fuerza.

---

## Entender el plano de referencia

![Figura 5: Comparación entre la calibración en el aparato y al final del cable de medición](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/31166bb5d8.png)

*Figura 5: Comparación entre la calibración en el aparato y al final del cable de medición*

El plano de referencia es el punto a partir del cual debe valer tu resultado de medición.

Si calibras directamente en el puerto del NanoVNA y luego conectas un cable de medición y varios adaptadores, el cable y los adaptadores forman parte de la configuración medida. Pueden modificar la impedancia mostrada e introducir pérdidas adicionales o desadaptaciones.

Si, por el contrario, calibras con la cadena de medición completa y colocas Open, Short y Load al final de esta, desplazas el plano de referencia al final de esa cadena de medición.

Para el ajuste preciso de una antena, el plano de referencia ideal está lo más cerca posible del punto de alimentación de la antena.

En la práctica, este punto no siempre es fácilmente accesible. Entonces hay dos opciones:

- acercar el NanoVNA lo máximo posible a la antena,
- o usar una cadena de medición fija y conocida y medir siempre bajo las mismas condiciones.

Si mides en el extremo inferior de un cable coaxial largo, no ves únicamente la antena. El cable transforma la impedancia, introduce atenuación y puede hacer que el resultado de medición parezca más suave o más favorable de lo que realmente es la adaptación directamente en el punto de alimentación.

---

## Medir la primera antena

![Figura 6: Pantalla del NanoVNA con rango de frecuencias, traza, marcador y punto de resonancia](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/1e60b1a9cb.png)

*Figura 6: Pantalla del NanoVNA con rango de frecuencias, traza, marcador y punto de resonancia*

Después de la calibración, retiras el estándar de calibración y conectas la antena sin alterar el resto de la cadena de medición.

Elige primero una representación fácilmente comprensible. Para la primera visión general son adecuados:

- SWR,
- S11 LOGMAG,
- Carta de Smith.

Activa un marcador y muévelo a lo largo de la curva. El marcador te muestra la frecuencia y el valor de medición en el punto seleccionado.

No busques simplemente el punto más bajo de toda la pantalla. Comprueba más bien:

- ¿Está el mínimo en el rango de frecuencias deseado?
- ¿Cuán alto es el SWR en tu frecuencia de operación?
- ¿Cuán profundo es el S11 LOGMAG?
- ¿Qué impedancia muestra el marcador?
- ¿Está la reactancia X cerca de cero?

Solo la combinación de esta información da una imagen útil.

---

## Entender correctamente el SWR

![Figura 7: Curvas de SWR con evaluación escalonada](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/fb7f355b71.png)

*Figura 7: Curvas de SWR con evaluación escalonada*

SWR significa „Standing Wave Ratio" (relación de onda estacionaria).

El SWR describe el grado de desadaptación entre la carga conectada y el sistema de referencia del aparato de medición, normalmente 50 ohmios.

Un SWR de 1:1 es el caso ideal teórico. En la práctica, un valor extremadamente bajo no siempre es necesario.

Como orientación general:

- **1,0 a 1,2:** excelente,
- **1,2 a 1,5:** muy bueno,
- **1,5 a 2,0:** bueno para muchas aplicaciones,
- **2,0 a 3,0:** posiblemente aún utilizable, según el equipo de radio y la aplicación,
- **más de 3,0:** examinar con detalle.

Esta clasificación no es una autorización universal. Qué valores son admisibles depende también del transmisor, del rango de frecuencias deseado y de la aplicación.

Además, es importante:

> **Un buen SWR solo demuestra una buena adaptación. No demuestra automáticamente que una antena irradie de manera efectiva la potencia suministrada.**

Una resistencia de carga, por ejemplo, puede estar perfectamente adaptada, pero aun así no es una buena antena de radio. Las pérdidas del cable también pueden mejorar artificialmente el SWR en el aparato de medición.

El SWR es, por tanto, un buen punto de partida, pero no el diagnóstico completo.

---

## LOGMAG: la reflexión en dB

![Figura 8: La misma medición de antena como representación de SWR y S11 LOGMAG](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/227c266879.png)

*Figura 8: La misma medición de antena como representación de SWR y S11 LOGMAG*

LOGMAG significa representación logarítmica del módulo. En una medición S11, LOGMAG muestra el módulo del factor de reflexión en decibelios.

Los valores típicos de S11 LOGMAG son negativos:

- **0 dB:** reflexión completa,
- **-6 dB:** reflexión notable,
- **-10 dB:** frecuentemente un punto de partida utilizable,
- **-15 dB:** buena adaptación,
- **-20 dB:** muy buena adaptación,
- **-30 dB:** adaptación excelente, siempre que la medición y la calibración respalden de forma fiable esta precisión.

Cuanto más negativo es el valor de S11 LOGMAG, menor es la reflexión medida.

### LOGMAG y Return Loss están estrechamente relacionados

Aquí es importante una distinción conceptual clara:

- **S11 LOGMAG** se representa habitualmente como valor negativo en dB, por ejemplo **-20 dB**.
- **Return Loss** (pérdida de retorno) se indica como valor positivo, en el mismo ejemplo, es decir, **20 dB**.

Ambas magnitudes describen la misma reflexión con el signo opuesto.

LOGMAG no reemplaza al SWR. Simplemente representa la misma información de reflexión en una escala logarítmica. La ventaja está en la representación: pequeñas diferencias entre buenas adaptaciones suelen compararse mejor en dB que en una escala de SWR.

Por ejemplo, aproximadamente corresponden:

- 10 dB de Return Loss a un SWR de 1,92,
- 15 dB de Return Loss a un SWR de 1,43,
- 20 dB de Return Loss a un SWR de 1,22.

Por eso LOGMAG es especialmente útil cuando deseas comparar puntos de resonancia, resonancias secundarias o pequeñas diferencias entre el antes y el después.

---

## Resistencia y reactancia

![Figura 10: Resistencia y reactancia en la zona capacitiva, resonante e inductiva](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/90f3b22d16.png)

*Figura 10: Resistencia y reactancia en la zona capacitiva, resonante e inductiva*

La impedancia de una antena consta de dos componentes:

> **Z = R + jX**

donde:

- **R** es la componente óhmica,
- **X** es la componente reactiva.

En un sistema de 50 ohmios, una impedancia cercana a **50 + j0 ohmios** está muy bien adaptada.

### Resistencia R

Un valor de 50 ohmios es ideal en el punto objetivo para un sistema de 50 ohmios. Sin embargo, una resistencia diferente no significa automáticamente que la antena sea inutilizable. La adaptación puede, en su caso, mejorarse con una red o un transformador adecuados.

### Reactancia X

La reactancia indica si la impedancia en la frecuencia considerada es capacitiva o inductiva:

- **X < 0:** capacitiva,
- **X = 0:** puramente óhmica, es decir, resonante,
- **X > 0:** inductiva.

La afirmación „X negativa significa que la antena es demasiado corta" o „X positiva significa que la antena es demasiado larga" solo es útil como orientación simplificada para ciertas antenas simples cerca de su resonancia deseada. Con antenas multibanda, antenas cargadas, redes de adaptación y transformaciones de línea, esta regla puede llevar a confusión.

El procedimiento más seguro es:

1. Determinar la frecuencia de resonancia.
2. Compararla con la frecuencia de operación deseada.
3. Solo a partir de ello deducir si un radiador simple debe hacerse más largo o más corto.

---

## La carta de Smith sin miedo

![Figura 11: Carta de Smith simplificada para principiantes](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/5083222b9c.png)

*Figura 11: Carta de Smith simplificada para principiantes*

La carta de Smith combina la resistencia y la reactancia en una única representación.

Para empezar, bastan cuatro reglas:

- **Centro:** 50 ohmios y sin reactancia, es decir, 50 + j0 ohmios,
- **por encima de la línea horizontal central:** inductivo,
- **por debajo de la línea central:** capacitivo,
- **cuanto más cerca del punto central:** mejor la adaptación a 50 ohmios.

A lo largo de la línea horizontal central, X es igual a cero. A la izquierda del punto central, la resistencia óhmica está por debajo de 50 ohmios; a la derecha, por encima de 50 ohmios.

La carta de Smith también muestra algo que el SWR por sí solo no revela: dos puntos de medición pueden tener el mismo SWR pero poseer impedancias completamente diferentes. La carta de Smith te muestra en qué dirección te alejas del punto central.

Para las primeras mediciones no necesitas calcular círculos. Simplemente observa dónde está el marcador y cómo se mueve cuando realizas un cambio en la antena.

---

## Encontrar la resonancia y evaluar el ancho de banda

![Figura 9: Resonancia demasiado baja, en el objetivo y demasiado alta](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b4a385e38d.png)

*Figura 9: Resonancia demasiado baja, en el objetivo y demasiado alta*

Existe una resonancia donde la reactancia X pasa por cero. En una antena simple y de bajas pérdidas, allí suele haber también un mínimo de SWR o un mínimo claro en la traza de S11 LOGMAG.

Sin embargo, estos puntos no siempre coinciden exactamente. Una antena puede ser resonante con X = 0 y aun así tener una resistencia claramente superior o inferior a 50 ohmios. Entonces la antena es resonante, pero no está óptimamente adaptada.

Por eso, comprueba siempre en el marcador en conjunto:

- Frecuencia,
- SWR,
- S11 LOGMAG,
- R,
- X,
- Posición en la carta de Smith.

### El ancho de banda no es solo una impresión de la curva

El ancho de banda designa el rango de frecuencias en el que se cumple un criterio definido. Esto puede ser, por ejemplo:

- SWR menor que 2:1,
- Return Loss mayor que 10 dB,
- S11 LOGMAG menor que -10 dB.

Coloca dos marcadores en los dos puntos límite. La diferencia de frecuencia entre estos marcadores es el ancho de banda según el criterio elegido.

Una curva estrecha no es automáticamente mala y una curva ancha no es automáticamente buena. El ancho de banda necesario depende de la aplicación. Además, las pérdidas pueden ensanchar una curva sin que la antena sea mejor.

---

## Ajustar un dipolo

![Figura 12: Dipolo antes y después del ajuste cuidadoso](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/2e604b30c7.png)

*Figura 12: Dipolo antes y después del ajuste cuidadoso*

Para un dipolo simple alimentado en el centro, se aplica como regla práctica:

- Si la resonancia está **por debajo** de la frecuencia deseada, el dipolo suele ser demasiado largo.
- Si la resonancia está **por encima** de la frecuencia deseada, el dipolo suele ser demasiado corto.

Supongamos que el dipolo debe funcionar a 7,1 MHz, pero la resonancia está a 6,8 MHz. Entonces el dipolo es demasiado largo.

Acorta ambos brazos de manera uniforme y solo en pequeños pasos. Después mides de nuevo.

Importante:

> **Cortar es definitivo. Doblar o replegar es más seguro para el primer ajuste.**

El procedimiento práctico es:

1. Construir la antena a la altura y en el entorno previstos posteriormente.
2. Medir la resonancia.
3. Modificar ambos lados de manera uniforme y cuidadosa.
4. Volver a colocar la antena en su posición original.
5. Medir de nuevo.
6. Comparar las curvas de antes y después.

No toques la antena durante la medición. También las manos, las escaleras, las piezas metálicas y los edificios cercanos pueden alterar el resultado.

---

## Antenas EndFed y multibanda

Una EndFed suele tener varias resonancias utilizables. Un barrido amplio puede mostrarte primero dónde están estas resonancias. Después examinas cada banda deseada en un rango de frecuencias más estrecho.

Ten en cuenta que un cambio en un solo punto puede afectar a varias bandas. Por eso, con una antena multibanda debes comprobar todos los rangos de frecuencias deseados después de cada cambio.

En una EndFed influyen, además, entre otros:

- el transformador,
- la longitud del radiador,
- la forma de construcción,
- la altura,
- el contrapeso,
- la línea de alimentación,
- posibles corrientes de modo común

en el resultado de medición. Un solo mínimo de SWR no basta, por tanto, para una evaluación completa.

---

## Antenas verticales

En las antenas verticales, los radiales u otra forma de contrapeso forman parte del sistema completo.

Cambios en:

- el número,
- la longitud,
- el ángulo,
- la altura,
- la distancia al suelo,
- el entorno

pueden modificar la resonancia y la impedancia.

Mide la antena, si es posible, en su situación de instalación posterior. Una antena vertical sobre la mesa de trabajo puede comportarse de manera muy diferente que en su lugar de montaje definitivo.

---

## Comprobar cables coaxiales, conectores y filtros

Para la atenuación de transmisión pura de un cable o filtro, usas S21. El objeto de prueba se conecta entre el Puerto 1 y el Puerto 2.

Para ello necesitas una calibración de dos puertos adecuada con un Thru definido.

### Filtros

En un filtro, el S21 LOGMAG muestra:

- la banda de paso,
- la banda de rechazo,
- la atenuación de inserción,
- las transiciones y frecuencias de corte,
- en su caso, bandas laterales no deseadas.

### Cables coaxiales

En un cable, con una medición S21 adecuada puedes observar la atenuación de transmisión en función de la frecuencia. Sin embargo, un simple barrido S21 no indica automáticamente en qué punto está dañado un cable. Para su localización se requieren procedimientos adicionales como una representación en el dominio del tiempo y un factor de velocidad conocido.

### Conectores y adaptadores

Si la curva cambia en cuanto tocas ligeramente un conector, a menudo hay un problema mecánico detrás:

- contacto flojo,
- conector hembra dañado,
- conexión sucia,
- adaptador inadecuado,
- carga mecánica del puerto del NanoVNA.

Mantén la cadena de adaptadores tan corta y constante como sea posible.

---

## Interpretar correctamente los resultados de medición

Una sola curva bonita todavía no es un diagnóstico completo.

### Buena resonancia, pero mal SWR

Una antena puede ser resonante porque X está cerca de cero, pero aun así tener una resistencia que se desvía claramente de 50 ohmios.

Entonces la antena es resonante, pero no está bien adaptada al sistema de 50 ohmios.

### Buen SWR, pero mala antena

Un SWR bajo también puede deberse a pérdidas. Un cable con muchas pérdidas o una construcción inadecuada pueden atenuar la energía reflejada y así mejorar la indicación en el aparato de medición.

El aparato de medición ve entonces una buena adaptación, pero no necesariamente una irradiación efectiva.

### Varios mínimos

Varios mínimos pueden indicar diferentes resonancias. En antenas multibanda, esto suele ser deseable. Pero también puede deberse a la construcción, las líneas, el entorno o resonancias no deseadas.

Por eso, no observes solo la profundidad de un mínimo, sino también:

- su frecuencia,
- la impedancia en el marcador,
- la posición en la carta de Smith,
- la repetibilidad de la medición.

---

## Los errores más frecuentes

![Figura 13: Errores típicos de medición con el NanoVNA, su causa y solución](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/4c7a6129cc.png)

*Figura 13: Errores típicos de medición con el NanoVNA, su causa y solución*

### No calibrar o calibrar mal

**Reconocible por:** valores inusuales, curva inestable o impedancia inverosímil.

**Solución:** definir el rango de frecuencias, restablecer la calibración y calibrar de nuevo en el plano de referencia correcto.

### Rango de frecuencias demasiado grande

**Reconocible por:** una curva muy gruesa y mínimos que se pasan fácilmente por alto.

**Solución:** hacer primero un barrido general, luego ajustar el rango deseado de forma más estrecha y calibrar de nuevo.

### Cadena de medición modificada después de la calibración

**Reconocible por:** resultados alterados después de cambiar un adaptador o un cable.

**Solución:** montar completamente la cadena de medición y calibrar después.

### Antena medida en un entorno inadecuado

**Reconocible por:** cambios notables al mover la antena o al acercarse personas.

**Solución:** medir la antena, si es posible, en su posición de operación posterior y con distancia a los objetos perturbadores.

### Solo mirar el SWR

**Reconocible por:** buen SWR, pero impedancia poco clara o inesperada.

**Solución:** observar además el S11 LOGMAG, R, X y la carta de Smith.

### Mover el conector o la antena durante la medición

**Reconocible por:** una curva que salta o fluctúa fuertemente.

**Solución:** fijar la configuración de medición, evitar tracción en las conexiones y no tocar nada durante el barrido.

---

## Receta práctica: comprobar una antena en pocos pasos

1. Define el rango de frecuencias deseado.
2. Monta la cadena de medición completa.
3. Calibra en el plano de referencia previsto.
4. Conecta la antena al Puerto 1.
5. Muestra primero S11 LOGMAG o SWR.
6. Coloca el marcador en el mínimo interesante.
7. Lee la frecuencia, el SWR y el S11 en dB.
8. Comprueba R y X en el mismo marcador.
9. Observa la posición en la carta de Smith.
10. Modifica la antena solo en pequeños pasos.
11. Mide de nuevo después de cada cambio.
12. Compara las curvas bajo las mismas condiciones.

---

## Referencia rápida

![Figura 15: Chuleta imprimible del NanoVNA](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/70eea94b4c.png)

*Figura 15: Chuleta imprimible del NanoVNA*

### Calibración para una medición de antena

**Ajustar rango de frecuencias → Reset → Open → Short → Load → Done → Save**

### Paso adicional para S21

**Realizar Thru y usar una calibración de dos puertos adecuada.**

### S11 LOGMAG y Return Loss

| S11 LOGMAG | Return Loss | Clasificación |
|---:|---:|---|
| -6 dB | 6 dB | adaptación débil |
| -10 dB | 10 dB | generalmente utilizable |
| -15 dB | 15 dB | buena |
| -20 dB | 20 dB | muy buena |
| -30 dB | 30 dB | excelente, si se puede medir de forma fiable |

### Correspondencia aproximada con el SWR

| SWR | Return Loss |
|---:|---:|
| 3,0 | 6,0 dB |
| 2,0 | 9,5 dB |
| 1,5 | 14,0 dB |
| 1,2 | 20,8 dB |
| 1,1 | 26,4 dB |

### ¿Qué indicación para qué?

| Tarea | Indicación útil |
|---|---|
| Visión general rápida | SWR |
| Comparar la reflexión en dB | S11 LOGMAG |
| Confirmar la resonancia | X y S11 |
| Evaluar la impedancia | R + jX |
| Reconocer la dirección de adaptación | Carta de Smith |
| Medir filtros | S21 LOGMAG |
| Medir la atenuación de cables | S21 LOGMAG |
| Determinar el ancho de banda | Dos marcadores y un límite definido |

---

## El flujo de trabajo óptimo con el NanoVNA

![Figura 14: Flujo de trabajo recomendado del NanoVNA desde la calibración hasta la medición de control](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b8e89fa70c.png)

*Figura 14: Flujo de trabajo recomendado del NanoVNA desde la calibración hasta la medición de control*

1. Definir el rango de frecuencias deseado.
2. Montar completamente la cadena de medición.
3. Calibrar en el plano de referencia correcto.
4. Conectar el objeto de prueba sin modificar la cadena de medición.
5. Obtener una visión general con SWR o S11 LOGMAG.
6. Colocar el marcador en el punto interesante.
7. Observar frecuencia, R, X y la carta de Smith en conjunto.
8. Hacer solo un cambio a la vez.
9. Medir de nuevo bajo las mismas condiciones.
10. Comparar el resultado antes y después.

Con este procedimiento evitas los errores más frecuentes de los principiantes. Sobre todo, aprendes a no solo mirar las curvas, sino a deducir de ellas una acción siguiente sensata.

El NanoVNA no hace el pensamiento por ti. Pero hace visible lo que realmente sucede en la antena, los cables y los componentes de RF. Precisamente ahí radica su mayor utilidad.

---

## Fuentes e información adicional

- [Guía práctica del NanoVNA para mediciones reales – NextTechWorld](https://nexttechworld.com/de/amateurfunk/nanovna-praxisguide/)
- [NanoVNA Setup Guide: Calibration, SWR, Smith Chart and Antenna Testing – SDRStore](https://www.sdrstore.eu/nanovna-setup-guide-calibration-swr-smith-chart-antenna-testing/?sl=de)
- [Medir el SWR con el NanoVNA – VESAB (PDF)](https://www.vesab.de/wpvesab/wp-content/uploads/SWR_messen_V01_2022_10_13.pdf)
- [NanoVNA – Un vistazo bajo la falda de la antena – Björns Techblog](https://www.bjoerns-techblog.de/2019/11/nanovna-der-antenne-unter-den-rock-geschaut/)

---
