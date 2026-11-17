# Invitación Emilia — integración RSVP

Proyecto Vercel con funciones de servidor en `/api` y diseño original V18.

## Configuración privada en Vercel
- `SUPABASE_URL`: URL del proyecto Supabase.
- `SUPABASE_SERVICE_ROLE_KEY`: clave **legacy service_role** (servidor únicamente). Nunca publicarla en GitHub ni en HTML. No usar `SUPABASE_PUBLISHABLE_KEY` para esta función.

En Supabase SQL Editor, si `service_role` no tiene permiso de ejecución:

```sql
GRANT EXECUTE ON FUNCTION public.confirmar_asistencia(uuid, integer) TO service_role;
```

**Antes de publicar:** comprobar que la función `confirmar_asistencia` valida la fecha límite, que el trigger de auditoría funciona, y que RLS y privilegios están configurados correctamente. La consulta de invitación solo devuelve los datos del código suministrado. La seguridad del enlace depende de mantener privado el UUID. Se recomienda agregar limitación de solicitudes antes de distribuir ampliamente los enlaces.

## Enlaces individuales
`https://TU-DOMINIO/?codigo=UUID_DE_LA_INVITACION`

No se incluye base de datos, claves, ni listado de invitados en este repositorio.

## Precaución
No reemplazar el despliegue de producción hasta probar las funciones y las confirmaciones en una URL de vista previa. La versión V18 original permanece intacta en el ZIP proporcionado por la familia.
