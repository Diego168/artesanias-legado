# Artesanías Legado S.A.C. · Sistema de gestión

Sistema web para talleres de artesanía de alto valor (ventas, insumos, producción por taller, encargos, registros).
Arquitectura MVC por capas (Controller → DTO → Service → DAO → BD), TDD con `node:test`, sin dependencias de npm.

## Puesta en marcha
```
node scripts/restaurar-bd.js      # crea data/artesanias_legado.db desde el respaldo versionado
npm test                          # pruebas (Node 22+)
npm start                         # http://localhost:4000
```
Variables: `PORT`, `DB_PATH`, `LOG_DIR`, `LOG_LEVEL`, `CORS_ORIGIN`.

## Backend en Java
La carpeta `backend-java/` contiene la versión Java 21 (Guava, Apache POI, Apache Commons, Logback) que sirve el mismo frontend.
Instrucciones en `backend-java/README.md`.

## Control de versiones
Ver [CONTRIBUTING.md](CONTRIBUTING.md): ramas, convención de commits, hooks, releases y reversiones.
Historial de versiones en [CHANGELOG.md](CHANGELOG.md).

## Carpetas
`src/` backend por capas · `public/` frontend · `tests/` pruebas · `data/` respaldo y modelo físico · `docs/` evidencias · `scripts/` utilidades.

> Nota del colaborador: usar Node 22 o superior.

## Datos de demostración (50+ filas por tabla)

`data/backup_artesanias_legado.sql` y `data/artesanias_legado.db` contienen ≥50 filas en cada tabla (excepto taller: se mantienen 3 talleres y crece el número de artesanos)
(proveedor 50, taller 3 —con 20 artesanos cada uno—, artesano 60, insumo 60, pieza 120, produccion_pieza 55, cliente 60, venta 60,
venta_detalle 62, encargo 55) más 50 usuarios que `server.js` crea al iniciar sin `ADMIN_PASSWORD`
(admin/Admin#2026, operador01…, consulta01…). Para regenerar: `node scripts/poblar-demo.js`
(usa `data/demo-data.sql`, generado por `backend-java/tools/generar_datos_demo.py`). Prueba: `tests/datos-demo.test.js`.
