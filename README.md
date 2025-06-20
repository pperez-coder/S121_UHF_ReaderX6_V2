# Proyecto Android Studio: Demo Serial X6 S121_UHF_ReaderX6_V2
## *Nuevo proyecto Android Studio

    Nombre: X6UHFSerialDemo

    Tipo de actividad: ----

    Lenguaje: java

    Mínimo SDK: Android 8.0 (O superior, por ser Android 10.0 el dispositivo)

   
# ¿Qué es el Impinj R2000?

El Impinj R2000 es un chip lector RFID UHF usado en diferentes dispositivos, como lectores portátiles o industriales. No se conecta directamente a una PC, normalmente se accede a través de un dispositivo (como un lector con Android o Windows, o un gateway).


 El X6 es un modelo de PDA Android UHF RFID genérico que muchos fabricantes chinos ensamblan (a veces aparece como “X6 UHF” o “Android X6 Handheld Terminal”). Suele usar el chip Impinj R2000 y la build x6-mp-q0.mp1-v6 confirma que es un modelo típico de Shenzhen y similares.

# Opciones para el SDK y desarrollo:
## 1. SDK Genérico para X6 UHF Android

Por lo general, estos dispositivos traen una app llamada “UHF Demo” o “RFID Demo”.
Dentro de esa app, en el menú, muchas veces aparece “About” o “Help” con un enlace o correo de contacto para pedir el SDK.

## 2. Código de Ejemplo Usando el SDK

Cuando bajes el SDK, normalmente te trae una carpeta llamada /uhf o /libs con un .jar y ejemplos en Java.

Aquí tienes un ejemplo típico para X6 en Java:

```
// Supón que ya importaste com.uhf.api.UhfManager o similar desde el SDK

// Inicializar
UhfManager mUhfManager = UhfManager.getInstance();
mUhfManager.open();

// Leer etiquetas EPC (Inventario rápido)
List<EPC> epcList = mUhfManager.inventoryRealTime();
for (EPC epc : epcList) {
    Log.d("UHF", "EPC: " + epc.getId());
}

// Cerrar
mUhfManager.close();
```
# --------------------------------------------------------------------------------

## 1. Identificar el puerto serial

En la mayoría de los X6 genéricos:

    El puerto suele ser /dev/ttyS4, /dev/ttyS3, o similar.

    Puedes probar todos los puertos enumerando los /dev/ttyS* en el sistema.

## 2. Permisos necesarios

Agrega esto a tu AndroidManifest.xml:
```
<uses-permission android:name="android.permission.SERIAL_PORT"/>
<uses-permission android:name="android.permission.USB_PERMISSION"/>
<uses-permission android:name="android.permission.USB_HOST"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.INTERNET"/>
```
## ¿Y si el puerto es otro?

    * Cambia /dev/ttyS4 por /dev/ttyS3, /dev/ttyS2, etc., hasta que recibas respuesta.
    
    * Puedes escanear puertos desde una terminal ADB con:
```
ls /dev/ttyS*
```
