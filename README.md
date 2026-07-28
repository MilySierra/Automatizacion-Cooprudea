# Sistema de Automatización de Conciliación Bancaria — COOPRUDEA

Flujo automatizado desarrollado en **n8n** que realiza el proceso completo de conciliación bancaria: cruza los movimientos del banco con los registros contables, actualiza el papel de trabajo y envía los resultados al correo registrado.

---

# Requisitos

- Credencial de Google Cloud para el formulario.
- Archivos de entrada en formato `.xlsx` con la estructura definida en el manual de usuario.

---

# Estructura del repositorio

```text
.
├── flujo_conciliacion.json    # Flujo exportado listo para importar en n8n
├── manual_usuario.pdf         # Manual de uso para el área contable
└── README.md
```

---

# Instalación en n8n Cloud

1. Ingresar a **n8n Cloud**.
2. Crear un nuevo flujo.
3. Ir a **⋯ → Import from file**.
4. Seleccionar `flujo_conciliacion.json`.
5. Configurar la credencial de Gmail en el nodo correspondiente.
6. Activar el flujo.

---

# Instalación en local

1. Ejecutar en la consola:

```bash
n8n start
```

2. Abrir:

```text
http://localhost:5678
```

3. Crear un nuevo flujo.
4. Ir a **⋯ → Import from file**.
5. Seleccionar `flujo_conciliacion.json`.
6. Configurar la credencial de Gmail en el nodo correspondiente.
7. Activar el flujo.

---

# Uso

1. Abrir la URL del formulario.
2. Cargar los **4 archivos** requeridos (`.xlsx`).
3. Ingresar las **2 fechas de conciliación**.
4. Presionar **Submit**.
5. Esperar entre **1 y 3 minutos**.
6. El resultado llegará al correo registrado.

---

# Estructura de los archivos de entrada

| Archivo | Cabeceras / Hojas requeridas |
|---------|------------------------------|
| Movimientos bancarios | Formato de descarga Bancolombia (separado por comas) |
| Libro mayor | Formato de descarga del sistema contable interno |
| Conciliación DIA | Concepto, Referencia, Referencia, Doc, Valor, Nota |
| Papel de trabajo | ConsigNoContPendiente, RetirosNoContPendiente, RetContNoBancoPendiente, ConsigContNoBancoPendiente, Balances |

> **Importante:** Los nombres de las columnas y de las hojas deben respetarse exactamente. Cualquier modificación puede impedir el correcto funcionamiento del flujo.

---

# Autores

Desarrollado por Karen Jiménez, Mily Sierra y Luisa Soto para COOPRUDEA — 2026
