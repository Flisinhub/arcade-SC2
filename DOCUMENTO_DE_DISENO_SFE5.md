# Arquitectura de Diseño e Implementación Técnica de Special Forces Elite 5 en StarCraft II

## 1. Fundamentos del Género, Bucle Operativo y Topología de Combate

**Special Forces Elite 5 (SFE5)** constituye una de las expresiones más depuradas del subgénero de defensa de base y asedio cooperativo (*Hero Defense / Fortress Siege*) dentro del ecosistema de mapas personalizados de Blizzard. Concebido originariamente en la escena de mapas UMS (*Use Map Settings*) de StarCraft: Brood War y trasladado progresivamente a las capacidades computacionales del motor Galaxy en StarCraft II, el diseño prescinde de la recolección pasiva tradicional en favor de un combate táctico continuo centrado en escuadrones. 

La premisa estructural ubica a los jugadores en una esquina fortificada del terreno junto a un edificio central neurálgico —habitualmente un Centro de Mando o equivalente institucional— cuya preservación representa la condición *sine qua non* de supervivencia; su colapso estructural desencadena la derrota automática de la partida.

### Bucle Central de Juego (Core Loop)
Se organiza como un péndulo constante entre la contención perimetral y la incursión ofensiva metódica:
1. **Contención Perimetral**: Los héroes repelen oleadas hostiles ininterrumpidas para acumular capital financiero primario y blindar las entradas naturales a su asentamiento.
2. **Incursión Ofensiva**: Con estabilidad táctica mínima, las unidades ofensivas abandonan el perímetro para asediar y demoler los bastiones enemigos distribuidos por el mapa.
3. **Escalada Reactiva**: La destrucción de bastiones erradica puntos de generación locales pero activa de manera reactiva la emergencia de jefes de zona y contraataques programados hacia el núcleo.

### Topología del Terreno y Rutas de Combate
- **Secuencia de Limpieza**: Reductos de Infestados en las inmediaciones -> Reservas de cría y colmenas Zerg intermedias -> Ciudadelas fortificadas Protoss -> Laboratorios de tecnología Híbrida del juego tardío.
- **Evitación de Combate Fratricida**: Los corredores deben evitar que las facciones enemigas (Zerg y Protoss) colisionen entre sí en desfiladeros, lo que provocaría que se destruyan sin otorgar recompensa económica a los jugadores humanos.

---

## 2. Taxonomía de Clases, Arquetipos y Sistema Tripartito de Atributos

| Héroe / Identidad | Facción | Rol Operativo | Mecánica Distintiva y Especialización de Combate |
|---|---|---|---|
| **Jim Raynor / Marine Élite** | Terran | DPS Balístico Sostenido | Disparo continuo a objetivo único, escalado lineal de daño y versatilidad frente a blindaje ligero. |
| **Gui Montag / Firebat** | Terran | Supresor Frontal de Área | Mitigación física biológica y proyección de daño cónico a corta distancia contra enjambres. |
| **Sarah Kerrigan / Nova** | Terran | Asesino Táctico / Élite | Protocolos de camuflaje, disparo de precisión de largo alcance y eliminación prioritaria de amenazas clave. |
| **Edmund Duke / Siege Tank** | Terran | Artillería de Choque | Bombardeo estático de gran radio con daño disperso (*splash*) masivo y vulnerabilidad en corto alcance. |
| **T-280 SCV / Swann** | Terran | Constructor e Ingeniero | Despliegue de torretas defensivas especializadas, reparación de estructuras y sellado de cuellos de botella. |
| **Blackhammer / Goliath** | Terran | Antiaéreo y Asalto Mecánico | Ráfagas duales simultáneas de apoyo balístico terrestre y supresión de misiles antiaéreos de alto impacto. |
| **Tassadar / Alto Templario** | Protoss | Caster Psiónico de Choque | Manipulación de tormentas psiónicas, dispersión de olas masivas y gestión intensiva de energía. |
| **Shadow Walker / Aniquilador** | Protoss | Perforador Anti-Blindaje | Proyección de haces colimados, durabilidad por escudo plasmático y disrupción de estructuras pesadas. |
| **Revenant / Arconte Oscuro** | Protoss | Control de Masas y Disrupción | Manipulación energética, confusión de objetivos prioritarios y amortiguación de daño de choque. |
| **Torrasque / Ultralisco** | Zerg | Tanque Colosal de Ruptura | Masa corporal masiva para absorción de impactos frontales, inmunidad al aturdimiento y hendidura cuerpo a cuerpo. |
| **Nyami / Hidralisco** | Zerg | Artillero Versátil Rápido | Proyección sostenida de espinas corrosivas con rápida adaptabilidad frente a vectores aéreos y terrestres. |
| **Alexei Stukov / Infestado** | Mixta | Generador de Presión Biológica | Despliegue continuo de carne de cañón biológica y desgaste por absorción de fuego enemigo. |

### Héroes Secretos Satíricos (1% Random Pick)
Al optar por la selección aleatoria (*Random Pick*), existe un 1% de probabilidad de activar personajes satíricos de la escena UMS clásica:
- **Dr. Evil**
- **Donald Trump**
- **Alex Jones**  
*(Poseen estadísticas sobredimensionadas y habilidades atípicas que alteran el balance convencional).*

### Fórmulas Matemáticas de Atributos
$$\Delta \text{HP} = \text{Fuerza} \times 25$$
$$\Delta \text{AD} = \text{Fuerza} \times 1.5$$
$$\Delta \text{AS} = \text{Destreza} \times 0.02$$
$$\Delta \text{Energy} = \text{Inteligencia} \times 10$$

- **Fuerza**: Incrementa simultáneamente la vida máxima (HP) y el daño de ataque base (AD).
- **Destreza**: Reduce los intervalos de ataque base del arma (mayor cadencia/velocidad) y acelera la regeneración por segundo de salud y escudos plasmáticos.
- **Inteligencia**: Amplía el radio de visión sobre la niebla de guerra, eleva la reserva máxima de energía y acelera la recuperación de maná.

---

## 3. Dinámica Económica y Escalamiento de Dificultad

### Sistema de Recompensas por Baja (Bounty System)
- Exclusivamente por golpe de gracia (*last hit*).
- Sin recolección de trabajadores o asimiladores.
- **Penalización por Fuego Cruzado Hostil**: Las bajas entre facciones enemigas no otorgan créditos al equipo humano.

### Tabla de Multiplicadores de Dificultad

| Dificultad Votada | Multiplicador de Ingreso ($M_{inc}$) | Escalado de Stats Hostiles ($M_{stat}$) | Intervalo de Upgrades Enemigos ($T_{up}$) |
|---|---|---|---|
| **Casual** | $\times 1.50$ | $\times 0.50$ | Cada 120 segundos |
| **Normal** | $\times 1.00$ | $\times 1.00$ | Cada 60 segundos |
| **Hard** | $\times 0.75$ | $\times 2.00$ | Cada 40 segundos |
| **Brutal** | $\times 0.50$ | $\times 3.00$ | Cada 30 segundos |
| **Pro** | $\times 0.25$ | $\times 4.00$ | Cada 20 segundos |
| **Torment / Impossible** | $\times 0.10$ | $\ge \times 5.00$ | Cada 15 segundos |

> En dificultades extremas como **Torment**, la IA adquiere incrementos acumulativos a su armadura y daño cada 15 segundos ($T_{up}$). La dilatación táctica resulta letal.

---

## 4. Jefes Secretos y Eventos Especiales de Invocación

| Jefe Secreto / Evento | Localización Territorial | Protocolo de Invocación | Singularidad Operativa |
|---|---|---|---|
| **Destroyer of Worlds** | Cuadrante superior izquierdo (restos de Nave Nodriza). | Estacionar exactamente **1 unidad terrestre durante 120 segundos continuos**. | La presencia de unidades adicionales o aéreas reinicia el contador. Bombardeos de daño masivo en área. |
| **Híbridos Ancestrales** | Proximidades del Artefacto Xel'Naga. | Mantener **1 única unidad de infantería terrestre durante 120 segundos**. | Despliegue concurrente de Híbridos Dominadores y Destructores con drenaje psiónico y aturdimiento masivo. |
| **ChainDog** | Monumento de la Estatua Central. | Mantener **1 unidad terrestre aislada sin desplazarse fuera del área durante 120 segundos**. | Movilidad extrema y letalidad a corta distancia que exige control de masas inmediato. |
| **Hell Gate** | Gran Nydus fortificado en sector noreste. | Concentrar simultáneamente a los **6 héroes del equipo** en el perímetro inmediato. | Incursión masiva de unidades de élite; su superación queda codificada en el archivo persistente del banco. |
| **Diablo** | Estación de servicio y combustible. | Posicionar unidades en el enclave en dificultad **Torment** y resistir la fase de contención. | Al ser derrotado en la máxima dificultad, se desbloquea como opción seleccionable permanente en partidas posteriores. |

---

## 5. Implementación Técnica en el Motor de StarCraft II

1. **Editor de Datos (Data Editor)**:
   - Escalado de atributos modelado mediante `Behavior: Buff` acumulativo para evitar sobrecarga del intérprete de script.
   - Armas de dispersión con `Effect: Create Persistent` y `Effect: Damage` con `Search: Areas`.
   - Auras de escuadrón mediante `Behavior: Buff` con `Effect: Search Area` y validadores de afinidad.

2. **Editor de Disparadores y Galaxy Script**:
   - Bucle de recompensas por baja vinculado a los factores $M_{inc}$ de dificultad.
   - Algoritmo de chequeo temporal de 120s para áreas de invocación secreta.
   - Bucle de escalamiento de mejoras periódicas hostiles ($T_{up}$).

3. **Subsistema de Persistencia Bancaria (.SC2Bank)**:
   - Cifrado con firma hash / checksum y salt interno para prevenir edición no autorizada de archivos locales.
   - Almacenamiento de desbloqueos especiales (héroes secretos, Diablo en Torment, logros de Hell Gate).
