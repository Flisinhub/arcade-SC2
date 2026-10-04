# Special Forces Elite 5 (SFE5) — StarCraft II Arcade

Recreación fiel y modernizada del legendario mapa personalizado **Special Forces Elite 5 (SFE5)** para el Arcade de **StarCraft II**, implementado directamente en Galaxy Script nativo y arquitectura modular de componentes.

---

## 🌟 Características Principales

### 🦸 16 Héroes Canónicos (+1 Héroe Secreto)
- **Tanques / Fuerza**: Firebat Pesado, Merodeador Acorazado, Zealot Centurión, Thor Titán.
- **Tiradores / Destreza**: Marine de Élite, Ghost Francotirador, Segador de Asalto, Espectro de Asedio.
- **Soporte / Utilidad**: Médico de Campaña, Cuervo Táctico, Centinela de Escudos.
- **Especialistas / Psiónicos**: Templario Tétrico, Alto Templario, Arconte de Vacío, Acechador Cibernético, Inmortal Prototipo.
- **Héroe Oculto (1% Probabilidad en Selección Aleatoria)**: *Tauren Space Marine Legendario*.

### 📊 Sistema de Atributos Determinista (F / D / I)
- **Fuerza (F)**: Aumenta la vida máxima (`+25 HP`), armadura pasiva y regeneración.
- **Destreza (D)**: Incrementa la velocidad de ataque, probabilidad de impacto crítico y cadencia.
- **Inteligencia (I)**: Incrementa la reserva de energía (`+15 Energía`), regeneración de maná y daño de habilidades.
- Interfaz en pantalla (HUD) interactiva con asignación de puntos mediante botones `[+ F]`, `[+ D]`, `[+ I]`.

### ⚔️ 7 Niveles de Dificultad
1. **Casual**: Recursos iniciales altos, enemigos relajados.
2. **Normal**: La experiencia táctica estándar.
3. **Difícil**: Mayor densidad de invasión y daño hostil aumentado (+25%).
4. **Brutal**: Estadísticas enemigas (+60%), recompensas de minerales ajustadas.
5. **Pro**: Para veteranos coordinados (+100% atributos hostiles).
6. **Imposible**: Presión implacable (+160% atributos hostiles, 50 minerales base).
7. **TORMENT**: Dificultad máxima para escuadrones de élite (+250% daño/salud, sin minerales iniciales).

### 🛡️ Asedio Perimetral y Puestos Avanzados
- **25 Oleadas Escalonadas**: Zerg, Terran y Protoss con composición y atributos que escalan según la dificultad seleccionada.
- **3 Puestos Avanzados Destructibles**: Puestos Norte, Este y Oeste con bonificación masiva de minerales al ser defendidos.
- **Núcleo Aliado (Fortaleza Planetaria)**: Con defensas perimetrales y sistema de alertas de integridad.

### 💀 3 Encuentros de Jefes por Fases
1. **Híbrido Maar**: Invoca clones y desata ondas de choque gravitacionales.
2. **Destructor de Mundos**: Coloso abisal con descargas de plasma zonal.
3. **Diablo**: El enfrentamiento final con fases múltiples de esbirros de élite.

### 💾 Persistencia Segura (Bancos de SC2)
- Cifrado con checksum y verificación de firma para prevenir manipulación.
- Registro de partidas jugadas, victorias, muertes y nivel histórico del jugador.

---

## 📁 Estructura del Proyecto

```
ARCADE SC2/
├── SpecialForcesElite.SC2Map/       # Directorio de componentes SC2
│   ├── ComponentList.SC2Components  # Definición de activos y módulos del mapa
│   ├── DocumentInfo                 # Dependencias (Campaign Mods: Liberty, Swarm, Void)
│   ├── MapScript.galaxy             # Script principal compilado por el motor
│   ├── Scripts/                     # Código modular en Galaxy Script
│   │   ├── AlliedBase.galaxy        # Lógica de la Fortaleza Planetaria y victoria/derrota
│   │   ├── Attributes.galaxy        # Fórmulas matemáticas F/D/I y hooks de daño
│   │   ├── BossAI.galaxy            # IA multifase de Maar, Destructor y Diablo
│   │   ├── Constants.galaxy         # Tablas de datos, héroes y multiplicadores
│   │   ├── GameLoop.galaxy          # Inicialización, selección de dificultad y diplomacia
│   │   ├── HeroSelection.galaxy     # Diálogo de selección de héroes (16 + Secreto)
│   │   ├── HUD.galaxy               # Tarjeta de estadísticas, barra superior y tienda
│   │   ├── Persistence.galaxy       # Carga y guardado cifrado en SC2 Bank
│   │   └── WaveSpawner.galaxy       # 25 oleadas de invasión y puestos avanzados
│   ├── enUS.SC2Data/                # Localización en inglés
│   └── esES.SC2Data/                # Localización en español
├── SpecialForcesElite5.SC2Map       # Archivo empaquetado del mapa
└── Recreación Special Forces Elite 5.pdf # Documento de especificación de diseño
```

---

## 🚀 Cómo Abrir y Probar en el Editor de StarCraft II

1. Abre el **Editor de StarCraft II** (`SC2Editor.exe`).
2. Ve a **Archivo > Abrir Documento...** (`Ctrl + O`).
3. Selecciona la carpeta de componentes `SpecialForcesElite.SC2Map` o el archivo `SpecialForcesElite5.SC2Map`.
4. Pulsa **Probar Documento** (`Ctrl + F9`) para compilar y ejecutar directamente en el cliente de StarCraft II.

---

## 📜 Créditos y Licencia
- Basado en el concepto original de *Special Forces Elite 5*.
- Adaptado y modernizado para StarCraft II por [Flisinhub](https://github.com/Flisinhub).
