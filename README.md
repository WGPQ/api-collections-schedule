# App Schedule API Bruno Collection

Coleccion versionada del backend `app_schedule_api` en formato Bruno/OpenCollection.

## Estructura

- `opencollection.yml`: manifiesto de la coleccion.
- `environments/local.yml`: variables locales para desarrollo.
- `Auth/`, `Companies/`, `Company Users/`, `Clients/`, `Calendar/`, `Audit Logs/`: carpetas funcionales.
- cada archivo `.yml` dentro de esas carpetas representa un request Bruno ejecutable.

## Abrir en Bruno

1. Clona o descarga este repositorio.
2. En Bruno usa `Open Collection`.
3. Selecciona la carpeta raiz de este repo:
   - `/Users/williampuma/Projects/ASPProjects/Schedule/api-collections`
4. Bruno debe detectar `opencollection.yml` y mostrar la coleccion `App Schedule API`.

Si ya importaste una version vieja y ves `Untitled Folder`, elimina esa coleccion en Bruno y vuelve a abrir la carpeta raiz. No importes archivos `.yml` sueltos.

## Environment local

Archivo: `environments/local.yml`

Variables principales:

- `baseUrl`: por defecto `http://localhost:5251`
- `accessToken`: se llena automaticamente despues de `Auth/Login`
- `companyId`: se llena automaticamente despues de `Companies/Create Company`
- `clientId`
- `appointmentId`
- `breakId`
- `internalBlockId`
- `ruleId`
- `companyUserId`
- `invitationToken`
- `responsibleUserId`

## Paginacion estandar

Los endpoints `GET` de lista usan el mismo contrato:

```json
{
  "items": [],
  "meta": {
    "page": 1,
    "pageSize": 20,
    "totalItems": 0,
    "totalPages": 0,
    "hasPreviousPage": false,
    "hasNextPage": false
  }
}
```

Query params comunes:

- `page`: default `1`
- `pageSize`: default `20`

Aplica a:

- `Companies/List Companies`
- `Company Users/List Users`
- `Company Users/List Invitations`
- `Clients/List Clients`
- `Calendar/List Events`
- `Calendar/List Availability Rules`
- `Calendar/Get Slots`
- `Audit Logs/List Audit Logs`

## Flujo recomendado

1. Ejecuta `Auth/Register` si necesitas un usuario nuevo.
2. Ejecuta `Auth/Login` para capturar `accessToken`.
3. Ejecuta `Companies/Create Company` para capturar `companyId`.
4. Usa `Clients`, `Company Users`, `Calendar` y `Audit Logs` con esas variables ya cargadas.

## Headers esperados

Los endpoints protegidos usan normalmente:

- `Authorization: Bearer {{accessToken}}`
- `X-Company-Id: {{companyId}}`

Los requests ya incluyen estos headers donde corresponde.

## Notas

- Esta coleccion esta alineada con el backend ASP.NET Core actual.
- Algunos requests guardan variables automaticamente usando scripts `after-response`.
- Si trabajas con HTTPS local, recuerda confiar el certificado de desarrollo de .NET o usar HTTP local.
- Hay una copia vieja anidada en `api-collections-schedule/`; Bruno debe abrir la carpeta raiz actual, no esa copia.
