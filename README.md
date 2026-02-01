# App Cámara Básica

Aplicación básica de Android en Kotlin que demuestra el uso de CameraX 1.5.3 para capturar imágenes.

## Características

- ✅ Solicitud de permisos de cámara en tiempo de ejecución (Android 6.0+)
- ✅ Vista previa de cámara en tiempo real usando CameraX
- ✅ Captura de fotos con un botón flotante
- ✅ Guardado de imágenes en el almacenamiento externo (MediaStore)
- ✅ Manejo de errores y estados de permisos
- ✅ Soporte para rotación de pantalla
- ✅ Lifecycle-aware components

## Requisitos Técnicos

### SDK Versions
- **minSdk**: 21 (Android 5.0 Lollipop)
- **targetSdk**: 34 (Android 14)
- **compileSdk**: 36

### Dependencias Principales

#### CameraX 1.5.3
```kotlin
implementation("androidx.camera:camera-core:1.5.3")
implementation("androidx.camera:camera-camera2:1.5.3")
implementation("androidx.camera:camera-lifecycle:1.5.3")
implementation("androidx.camera:camera-view:1.5.3")
```

#### AndroidX
```kotlin
implementation("androidx.core:core-ktx:1.12.0")
implementation("androidx.appcompat:appcompat:1.6.1")
implementation("com.google.android.material:material:1.11.0")
implementation("androidx.constraintlayout:constraintlayout:2.1.4")
implementation("androidx.activity:activity-ktx:1.8.2")
```

## Estructura del Proyecto

```
app/
├── src/
│   └── main/
│       ├── java/com/example/appcamarabasica/
│       │   └── MainActivity.kt          # Lógica principal de la app
│       ├── res/
│       │   ├── layout/
│       │   │   └── activity_main.xml    # Layout con PreviewView y FAB
│       │   └── values/
│       │       └── strings.xml          # Recursos de texto
│       └── AndroidManifest.xml          # Permisos y configuración
└── build.gradle.kts                     # Dependencias del módulo
```

## Permisos

La aplicación requiere los siguientes permisos en el `AndroidManifest.xml`:

```xml
<uses-feature android:name="android.hardware.camera.any" />
<uses-permission android:name="android.permission.CAMERA" />
```

## Funcionalidad Principal

### MainActivity.kt

La actividad principal implementa:

1. **Solicitud de Permisos**: Usa `ActivityResultContracts.RequestPermission()` para solicitar el permiso de cámara de forma moderna.

2. **Inicialización de CameraX**: Configura `ProcessCameraProvider` con dos casos de uso:
   - `Preview`: Muestra la vista previa en tiempo real
   - `ImageCapture`: Permite capturar fotos

3. **Captura de Imágenes**: 
   - Genera nombres de archivo con timestamp
   - Guarda imágenes en MediaStore (Pictures/CameraX-Images)
   - Muestra mensajes Toast con el resultado

4. **Gestión del Ciclo de Vida**:
   - Usa `ExecutorService` para operaciones de cámara en segundo plano
   - Limpia recursos en `onDestroy()`

### Layout

El `activity_main.xml` contiene:

- **PreviewView**: Vista completa para mostrar la cámara
- **FloatingActionButton**: Botón centrado en la parte inferior para capturar fotos

## Compilación y Ejecución

### Requisitos
- Android Studio Arctic Fox o superior
- JDK 11
- Dispositivo Android físico o emulador con Android 5.0+ y cámara

### Pasos

1. Clonar el repositorio
2. Abrir el proyecto en Android Studio
3. Sincronizar Gradle
4. Ejecutar en un dispositivo o emulador

```bash
./gradlew assembleDebug
```

## Uso de la App

1. Al iniciar, la app solicitará permiso de cámara
2. Una vez concedido, se mostrará la vista previa de la cámara
3. Presiona el botón flotante (🎥) para capturar una foto
4. Las fotos se guardan automáticamente en Pictures/CameraX-Images
5. Se muestra un mensaje Toast confirmando el guardado

## Compatibilidad

- ✅ Android 5.0 (API 21) hasta Android 14 (API 34)
- ✅ Kotlin 2.0.21
- ✅ CameraX 1.5.3
- ✅ Android Gradle Plugin 8.5.0

## Notas de Implementación

- Código comentado en español para facilitar la comprensión
- Sigue las mejores prácticas de Android para manejo de permisos
- Usa APIs modernas de CameraX y Kotlin
- Implementación lifecycle-aware para evitar memory leaks
- Manejo adecuado de errores con mensajes descriptivos

## Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.
