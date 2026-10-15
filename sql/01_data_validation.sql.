-- =============================================================
-- 01. Data quality checks before the analysis
-- Engine: PostgreSQL
-- =============================================================
 
-- Null values in the key columns of ventas_2017
SELECT
    SUM(CASE WHEN numero_pedido   IS NULL THEN 1 ELSE 0 END) AS nulos_numero_pedido,
    SUM(CASE WHEN clave_producto  IS NULL THEN 1 ELSE 0 END) AS nulos_clave_producto,
    SUM(CASE WHEN clave_territorio IS NULL THEN 1 ELSE 0 END) AS nulos_clave_territorio
FROM
    ventas_2017;
 
-- Invalid quantities in ventas_2017 (business rule: quantity must be greater than 0)
SELECT
    COUNT(*) AS filas_cantidad_no_valida
FROM
    ventas_2017
WHERE
    cantidad_pedido <= 0;
 
-- Invalid prices in productos (business rule: price cannot be negative)
SELECT
    COUNT(*) AS productos_precio_no_valido
FROM
    productos
WHERE
    precio_producto < 0;
 
