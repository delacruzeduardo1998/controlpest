# ControlPest

Sistema web para la gestión de una empresa de control de plagas y fumigación. Permite registrar hojas de servicio, llevar las bitácoras requeridas por la operación (químicos, equipo, residuos, vehículos), emitir certificados y generar los reportes en PDF y Excel.

Construido con **Laravel 5.7** (PHP 7.1+) y **MySQL**.

## Módulos

| Módulo | Ruta | Descripción |
|---|---|---|
| Inicio de sesión | `/` , `/principal` | Login y página principal |
| Usuarios | `/admin/users` | Alta, edición, búsqueda y baja de usuarios |
| Hoja de servicio | `/HojaServicio` | Solicitudes de servicio por cliente (tipo de plaga, giro, características del local, químicos a utilizar) |
| Certificados | `/certificado`, `/CertificadoVehicular` | Certificados de fumigación de establecimientos y de vehículos |
| Bitácora de mantenimiento de equipo | `/BitacoraMantenimientoEquipo` | Registro y exportación a Excel |
| Bitácora de control de químicos en almacén | `/BitacoraControlQuimicosAlmacen` | Entradas y salidas de químicos |
| Bitácora de residuos de plaguicidas | `/BitacoraResiduosPlaguicidas` | Manejo y disposición de residuos |
| Vehículos y bitácora vehicular | `/nuevovehi`, `/bitacoravehiculo` | Padrón de vehículos y registro de combustible/recorridos por vehículo |
| Viáticos | `/formatoViaticos` | Formato de viáticos del personal |
| Facturas | `/facturas`, `/upload` | Consulta de facturas e importación/exportación con Excel |
| Calendario | `/events` | Calendario de servicios (FullCalendar) |

Casi todos los módulos tienen su reporte en PDF (rutas `pdf*` y `*PDF`), generado con TCPDF.

## Requisitos

- PHP 7.1.3 o superior (compatible con Laravel 5.7)
- Composer
- MySQL / MariaDB
- Node.js y npm (solo si vas a recompilar los assets)

## Instalación

```bash
git clone <url-del-repositorio> controlpest
cd controlpest

composer install
cp .env.example .env
php artisan key:generate
```

Edita `.env` con los datos de tu base de datos:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=controlpest
DB_USERNAME=root
DB_PASSWORD=
```

Crea la base de datos `controlpest` y ejecuta las migraciones:

```bash
php artisan migrate
php artisan db:seed   # opcional: datos de ejemplo
```

Levanta el servidor de desarrollo:

```bash
php artisan serve
```

La aplicación queda en <http://localhost:8000>.

### Assets (opcional)

```bash
npm install
npm run dev        # desarrollo
npm run prod       # producción
```

## Estructura

```
app/                      Modelos (Eloquent) y controladores
app/Http/Controllers/     Lógica de cada módulo y generadores de PDF
database/migrations/      Esquema de la base de datos
resources/views/          Vistas Blade
routes/web.php            Todas las rutas de la aplicación
public/                   Assets públicos (CSS, JS, imágenes)
```

## Dependencias principales

- [laravel/framework 5.7](https://laravel.com/docs/5.7)
- [elibyy/tcpdf-laravel](https://github.com/elibyy/tcpdf-laravel) — generación de PDF
- [maatwebsite/excel 2.1](https://docs.laravel-excel.com/2.1/) — importación/exportación de Excel
- [laravelcollective/html](https://laravelcollective.com/docs/5.7/html) — formularios
- [maddhatter/laravel-fullcalendar](https://github.com/maddhatter/laravel-fullcalendar) — calendario

## Licencia

MIT
