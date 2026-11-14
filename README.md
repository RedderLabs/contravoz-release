# Contravoz — versiones para Android

Copia pública de las **APK de Contravoz** para Android: la app, su suma SHA-256 y, cuando está disponible,
su firma GPG.

El código está en un repositorio privado. Este repo existe solo para que cualquiera pueda descargar la app
sin cuenta de GitHub.

- **Última versión**: pestaña [Releases](../../releases).

## Por qué hay una versión fuera de Google Play

La versión de GitHub es la misma app que la de Google Play y añade una cosa: **grabar las llamadas**.
Android solo deja usar el micrófono durante una llamada a los servicios de accesibilidad, y Google Play no
permite usarlos para grabar. En España es legal grabar una conversación en la que participas.
Difundirla sin permiso de la otra persona puede no serlo.

Las grabaciones se quedan en tu móvil. Contravoz no lee la pantalla ni lo que escribes.

## Qué trae cada versión

| Archivo | Qué es |
|---|---|
| `contravoz-<versión>-arm64.apk` | La app, para Android 12 o posterior (móviles de 64 bits, casi todos desde 2018). |
| `contravoz-<versión>-arm64.apk.sha256` | Suma SHA-256, en formato `sha256sum`. |
| `contravoz-<versión>-arm64.apk.asc` | Firma GPG de Redder Labs (si la versión la incluye). |

## Comprobar la APK antes de instalarla

Todas las APK van firmadas con la clave de Contravoz. Android solo instala una actualización si está firmada
con la misma clave, así que nadie más puede publicar una actualización que se instale encima de la tuya.

Huella SHA-256 del certificado de firma:

```
A2:75:E6:C7:12:3B:75:B6:6F:3F:4F:6F:0C:99:4D:CF:30:77:2D:95:2B:45:0E:30:68:44:A9:18:FA:EA:1C:EB
```

```sh
sha256sum -c contravoz-<versión>-arm64.apk.sha256
apksigner verify --print-certs contravoz-<versión>-arm64.apk   # «SHA-256 digest» debe coincidir con la huella
gpg --verify contravoz-<versión>-arm64.apk.asc contravoz-<versión>-arm64.apk   # si hay .asc
```

Si la suma o la huella no coinciden, borra la APK y no la instales.

## Instalar

1. Descarga la `.apk` desde [Releases](../../releases) y ábrela. Android te pedirá permiso para instalar
   apps desde el navegador o el gestor de archivos.
2. Para grabar llamadas: Ajustes de Contravoz → **Grabar llamadas** → «Activar en Accesibilidad».
   En Android 13 o posterior, si no te deja activarlo: Ajustes del móvil → Apps → Contravoz → ⋮ →
   **Permitir ajustes restringidos**, y vuelve a intentarlo.

Las actualizaciones no son automáticas: instala la nueva APK encima de la anterior y conservarás tus datos.

Las versiones las compila, firma y publica GitHub Actions. Dudas o una APK sospechosa:
<releases@redderlabs.com>.
