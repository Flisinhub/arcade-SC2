# Special Forces Elite 5 (SFE5) — StarCraft II Arcade

Implementación técnica, fiel y modernizada del legendario mapa personalizado **Special Forces Elite 5 (SFE5)** para el Arcade de **StarCraft II**, desarrollado directamente en Galaxy Script nativo con arquitectura modular y validación de compilación ANSI C89.

---

## 🌟 Características Principales

### 🦸 12 Héroes Canónicos (+ 3 Héroes Secretos Satíricos del 1%)
- **Jim Raynor / Marine Élite (Terran)**: DPS Balístico Sostenido, disparo continuo monobjetivo.
- **Gui Montag / Firebat (Terran)**: Supresor Frontal de Área, mitigación física biológica y daño cónico.
- **Sarah Kerrigan / Nova (Terran)**: Asesino Táctico / Élite, camuflaje, disparo de precisión y eliminación prioritaria.
- **Edmund Duke / Siege Tank (Terran)**: Artillería de Choque, bombardeo estático con daño de dispersión masivo.
- **T-280 SCV / Swann (Terran)**: Constructor e Ingeniero, despliegue de torretas defensivas y reparación.
- **Blackhammer / Goliath (Terran)**: Antiaéreo y Asalto Mecánico, ráfagas duales terrestres y misiles pesados.
- **Tassadar / Alto Templario (Protoss)**: Caster Psiónico de Choque, manipulación de tormentas y dispersión masiva.
- **Shadow Walker / Aniquilador (Protoss)**: Perforador Anti-Blindaje, haces colimados y durabilidad por escudo plasmático.
- **Revenant / Arconte Oscuro (Protoss)**: Control de Masas y Disrupción, manipulación energética y confusión.
- **Torrasque / Ultralisco (Zerg)**: Tanque Colosal de Ruptura, absorción de impactos frontales e hendidura masiva.
- **Nyami / Hidralisco (Zerg)**: Artillero Versátil Rápido, espinas corrosivas continuas aire/tierra.
- **Alexei Stukov / Infestado (Mixta)**: Generador de Presión Biológica, despliegue continuo de carne de cañón.
- **Héroes Secretos Satíricos (1% Random Pick)**:
  - **Dr. Evil**: Cerebro Maligno Supremo (Tauren Space Marine Legendario con láser orbital).
  - **Donald Trump**: Magnate Constructor de Muros (Thor Titán Dorado con cañones de máximo impacto).
  - **Alex Jones**: Megáfono de Combate Sónico (Marauder de proyectiles sónicos).

---

### 📊 Sistema Tripartito de Atributos Determinista
$$\Delta \text{HP} = \text{Fuerza} \times 25$$
$$\Delta \text{AD} = \text{Fuerza} \times 1.5$$
$$\Delta \text{AS} = \text{Destreza} \times 0.02$$
$$\Delta \text{Energy} = \text{Inteligencia} \times 10$$

- **Fuerza (F)**: Incrementa simultáneamente la vida máxima (HP) y el daño base (AD).
- **Destreza (D)**: Incrementa la cadencia/velocidad de ataque y la regeneración de vida y escudos plasmáticos.
- **Inteligencia (I)**: Incrementa la capacidad energética máxima, la regeneración de maná y el cono de visión.
- **HUD Interactivo**: Asignación de puntos en pantalla con botones `[+]` y acceso a la **Tienda Tecnológica**.

---

### ⚔️ 6 Niveles Canónicos de Dificultad
| Dificultad | Multiplicador de Ingreso ($M_{inc}$) | Escalado de Stats Hostiles ($M_{stat}$) | Intervalo de Upgrades Enemigos ($T_{up}$) | Intervalo de Oleadas |
|---|---|---|---|---|
| **Casual** | $\times 1.50$ | $\times 0.50$ | Cada 120 segundos | 35s |
| **Normal** | $\times 1.00$ | $\times 1.00$ | Cada 60 segundos | 30s |
| **Hard** | $\times 0.75$ | $\times 2.00$ | Cada 40 segundos | 25s |
| **Brutal** | $\times 0.50$ | $\times 3.00$ | Cada 30 segundos | 22s |
| **Pro** | $\times 0.25$ | $\times 4.00$ | Cada 20 segundos | 18s |
| **TORMENT** | $\times 0.10$ | $\ge \times 5.00$ | Cada 15 segundos | 15s |

---

### 🛡️ Asedio Perimetral y Fortaleza Central Aliada
- **25 Oleadas Escalonadas**: Invasores Zerg, Protoss y Terran que marchan hacia el núcleo.
- **Aura Médica y Médicos de Campaña**: La Fortaleza Planetaria dispone de médicos asignados y aura sanadora activa (+35 HP/s) para restaurar a los héroes.
- **3 Reductos Hostiles Destructibles**: Colmena Zerg Norte, Fortaleza Protoss Este y Complejo Infestado Oeste. Al destruirlos otorgan +1000 minerales al equipo y activan contraataques de jefes.

---

### 🔮 5 Jefes Secretos y Eventos Territoriales de Invocación
1. **Destroyer of Worlds**: Cuadrante NW (restos de Nave Nodriza). Mantener exactamente 1 unidad terrestre durante 120s continuos.
2. **Híbridos Ancestrales**: Cuadrante SE (Artefacto Xel'Naga). Mantener exactamente 1 unidad de infantería terrestre durante 120s.
3. **ChainDog**: Centro del mapa (Monumento Estatua). Mantener 1 unidad terrestre aislada durante 120s continuos.
4. **Hell Gate**: Sector NE (Gran Nydus fortificado). Concentrar simultáneamente a todos los héroes vivos del equipo durante 10s.
5. **Diablo Megaboss**: Sector SW en dificultad **Torment**. Derrotarlo otorga el desbloqueo permanente del héroe Diablo en partidas futuras.

---

### 💾 Persistencia Cifrada (.SC2Bank)
- Protección anti-trampas mediante checksum con sal criptográfica interna (`c_SECURITY_SALT`).
- Guarda nivel de cuenta, partidas ganadas por dificultad, jefes eliminados y logros desbloqueados.

---

## 📁 Estructura del Repositorio

```
ARCADE SC2/
├── SpecialForcesElite.SC2Map/       # Carpeta de componentes del mapa SC2
│   ├── ComponentList.SC2Components  # Componentes del mapa
│   ├── DocumentInfo                 # Dependencias oficiales de campaña
│   ├── MapScript.galaxy             # Script maestro consolidado y verificado (3000+ líneas)
│   ├── Scripts/                     # Arquitectura modular
│   │   ├── AlliedBase.galaxy        # Fortaleza Planetaria, médicos y condiciones de fin
│   │   ├── Attributes.galaxy        # Fórmulas matemáticas deterministas F/D/I
│   │   ├── BossAI.galaxy            # IA de jefes y 5 rituales territoriales de 120s
│   │   ├── Constants.galaxy         # Catálogo de héroes, dificultades y constantes
│   │   ├── GameLoop.galaxy          # Diplomacia, selector de dificultad y orquestación
│   │   ├── HeroSelection.galaxy     # Diálogo de selección 3x4 + 1% héroe satírico
│   │   ├── HUD.galaxy               # Panel de atributos [+], barra superior y tienda
│   │   ├── Persistence.galaxy       # Banco protegido con suma de verificación
│   │   └── WaveSpawner.galaxy       # 25 oleadas, nidos y curva de entropía (T_up)
│   ├── enUS.SC2Data/                # Localización en inglés
│   └── esES.SC2Data/                # Localización en español
├── DOCUMENTO_DE_DISENO_SFE5.md      # Especificación maestra de diseño
└── README.md
```

---

## 🚀 Cómo Probar en StarCraft II

1. Abre el **Editor de StarCraft II** (`SC2Editor.exe`).
2. Ve a **Archivo > Abrir Documento...** (`Ctrl + O`).
3. Selecciona la carpeta `SpecialForcesElite.SC2Map`.
4. Pulsa **Probar Documento** (`Ctrl + F9`) para compilar e iniciar directamente la partida.

---

## 📜 Créditos y Autoría
- Basado en el legendario mapa UMS *Special Forces Elite 5*.
- Implementación y arquitectura completa por [Flisinhub](https://github.com/Flisinhub).
