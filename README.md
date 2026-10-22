# Parcial 1 – Parte 2 · Esfera con Normal Map y Point Light

Proyecto de Unity para el **Primer Parcial – Segunda Parte (50 %)** del curso **Desarrollo de Videojuegos** – Universidad del Valle.

**Autor:** Kevin Andres Aristizabal Ipia

---

## Enunciado

> En Unity agregar una esfera, agregar un material con un mapa normal que tenga su nombre (puede crearlo con GIMP como lo vimos en clase), junto a la esfera un *point light* de cualquier color; la esfera debe ser de color rojo.
> Subir el link del GitHub de su proyecto, debe tener 4 commits:
> 1. creando esfera
> 2. texturizando esfera
> 3. agregando luz
> 4. coloreando esfera de rojo

## Requisitos de la entrega

| # | Requisito | Detalle |
|---|-----------|---------|
| 1 | Esfera | `GameObject > 3D Object > Sphere` en `Assets/Scenes/SampleScene.unity` |
| 2 | Material con normal map | Normal map con el nombre **"Kevin"**, asignado al slot *Normal Map* del material (URP/Lit) |
| 3 | Point Light | Luz de tipo *Point* ubicada junto a la esfera, de cualquier color |
| 4 | Color rojo | *Base Map* del material de la esfera en rojo |

## Historial de commits esperado

```
1. creando esfera
2. texturizando esfera
3. agregando luz
4. coloreando esfera de rojo
```

> El commit inicial (`Initial check-in`) corresponde a la creación del proyecto.

## Versiones y compatibilidad

| Herramienta | Versión |
|-------------|---------|
| **Unity Editor** | **6000.6.6f1** (Unity 6.6) |
| Render Pipeline | Universal Render Pipeline (URP) 17.6.0 |
| Input System | 1.20.0 |
| **Blender (compatible)** | **4.2 LTS o 4.5 LTS** (recomendado). Ver nota abajo |
| GIMP (para el normal map) | 2.10 / 3.x |

### Nota sobre Blender

Unity no trae un importador nativo de `.blend`: cuando hay un archivo `.blend` en `Assets/`, Unity **llama al Blender instalado en el equipo** para convertirlo a FBX en segundo plano. Por eso:

- Blender debe estar **instalado** en cada máquina que abra el proyecto.
- Se recomienda una versión **LTS** de Blender (4.2 LTS o 4.5 LTS), que tienen soporte largo y un exportador FBX estable.
- Para evitar depender de Blender, la opción más segura es **exportar desde Blender a `.fbx`** (`File > Export > FBX`, con *Apply Transform* y escala 1.0) y subir solo el `.fbx` a `Assets/`.
- Los respaldos automáticos de Blender (`*.blend1`, `*.blend2`, …) están excluidos en el `.gitignore`.

## Cómo abrir el proyecto

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/kev405/Parcial-1-Parte-2.git
   ```
2. Abrir **Unity Hub** → *Add project from disk* → seleccionar la carpeta clonada.
3. Usar el editor **6000.6.6f1** (Unity Hub lo sugerirá automáticamente).
4. Abrir la escena `Assets/Scenes/SampleScene.unity` y darle *Play*.

> La primera apertura tarda un poco: Unity regenera la carpeta `Library/`, que no se versiona.

## Cómo configurar el normal map

1. Importar la imagen del normal map en `Assets/` (por ejemplo `Assets/Textures/Kevin_Normal.png`).
2. En el *Inspector*: **Texture Type → Normal map** → *Apply*.
3. Crear un material (`Create > Material`, shader **Universal Render Pipeline/Lit**).
4. Arrastrar la textura al slot **Normal Map** y ajustar la intensidad (valor junto al slot).
5. Arrastrar el material a la esfera.
6. Cambiar el color del **Base Map** a rojo (`#FF0000`).

### Crear el normal map en GIMP

1. Nueva imagen (por ejemplo 1024×512), fondo negro, escribir el nombre en blanco.
2. Desenfocar levemente (*Filtros > Desenfocar > Desenfoque gaussiano*, ~3–5 px) para suavizar el relieve.
3. *Filtros > Mapa genérico > Mapa de normales* (GIMP 2.10+), con **Y+ / OpenGL**, que es la convención de Unity.
4. Exportar como PNG.

## Estructura del proyecto

```
Parcial 1 Parte 2/
├── Assets/            # Escenas, materiales, texturas (versionado)
│   └── Scenes/
│       └── SampleScene.unity
├── Packages/          # manifest.json y lock de paquetes (versionado)
├── ProjectSettings/   # Configuración del proyecto (versionado)
├── .gitignore         # Excluye Library/, Temp/, Logs/, UserSettings/, .csproj, .sln, etc.
├── .gitattributes
└── README.md
```

Carpetas **no versionadas** (se regeneran solas): `Library/`, `Temp/`, `Logs/`, `UserSettings/`, `obj/`, `Build/` y los archivos `*.csproj` / `*.sln`.
