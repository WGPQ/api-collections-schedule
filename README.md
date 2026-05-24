# App Schedule API Collections

Colecciones versionadas del backend en formato YAML, separadas del código de la API.

## Estructura

- `collections/AppSchedule API`
- `environments/local.yml`

Cada carpeta representa un módulo funcional.
Cada archivo `.yml` representa un endpoint.

## Variables

Las colecciones usan estas variables:

- `{{baseUrl}}`
- `{{accessToken}}`
- `{{companyId}}`
- `{{appointmentId}}`
- `{{clientId}}`
- `{{ruleId}}`
- `{{companyUserId}}`
- `{{invitationToken}}`

## Uso recomendado

1. Registrar o sembrar un usuario.
2. Hacer login y guardar `accessToken`.
3. Crear empresa y guardar `companyId`.
4. Consumir el resto de endpoints enviando:
   - `Authorization: Bearer {{accessToken}}`
   - `X-Company-Id: {{companyId}}`

## Nota

Este formato está pensado para documentación y versionado por endpoint, similar al patrón de un repo separado de `api-collections`.
Si quieres, el siguiente paso puede ser exportarlo también a:

- Postman collection JSON
- OpenAPI YAML/JSON
- Bruno collection
# api-collections-schedule
