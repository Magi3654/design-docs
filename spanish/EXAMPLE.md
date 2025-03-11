# TravelMate
Link: [Link a este design doc](#)

Author(s): Ilse Machado, Ana Quinonez

Status: [Draft, Ready for review, In Review, Reviewed]

Ultima actualización: 2025-03-06

## Contenido
- Goals
- Non-Goals
- Background
- Overview
- Detailed Design
  - Solucion 1
    - Frontend
    - Backend
  - Solucion 2
    - Frontend
    - Backend
- Consideraciones
- Métricas

## Links
- [Un link](#)
- [Otro link](#)

## Objetivo
Una aplicación que permita al usuario identificar los requisitos migratorios para su viaje, y tipo de divisa
con base a su nacionalidad.

## Goals
- Desplegar los permisos y/o requisitos necesarios para el ingreso a un pais extrangero 
- Direccionar a los sitos correspondientes para su  tramite
- Desplegar la divisa del lugar de destino
## Non-Goals - Pendiente
- Que se encuentre la informacion de todos los paises del mundo 

## Background
Es comun que un viajero cuando viaja de manera internacional no tiene la certeza de los requisitos de visado  que son indispensables para
el ingreso a ese pais, igualmente desconoce la divisa que va a utilizar, donde conseguirla y requisitos sanitarios 

## Overview
Necesitaremos una API que contenga permisos, visados, divisa y vacunas por pais que sean necesarios para poder entrar al mismo, ademas 
contendra los links de los sitios oficiales de los departamentos de migracion para mas informacion y tramite. 

-  Se accedera a la API con id de nacionalidades a traves de una lista 
-  Con la seleccion del pais de destino desplega la informacion organizada

## Detailed Design

## Solución 1

## Spotify

## **🛠️ Arquitectura de la Solución**

### **🖥️ Tecnologías y Herramientas**
- **Backend:** Flask (Python) 
- **Base de Datos:**  SQLite
- **Frontend:** Telegram
- **APIs Externas:**
  - **Requisitos migratorios:** IATA Travel Centre, Sherpa API (Revision si hay algo abierto, o construirla manualmente)
  - **Divisas:** Open Exchange Rates, XE Currency API
  - **Vacunas:** WHO (Organización Mundial de la Salud)

---

## **🔄 Flujo de Funcionamiento**
1. **El usuario ingresa su nacionalidad** (selección en dropdown o detección automática).
2. **Selecciona el país de destino** desde una lista desplegable o búsqueda.
3. **El sistema consulta la API** y obtiene los siguientes datos:
   - **Requisitos de visado** según la nacionalidad.
   - **Vacunas obligatorias o recomendadas**.
   - **Divisa del país y tasa de cambio actual**.
   - **Enlaces oficiales** para más información y trámites.
4. **La información se despliega** de manera clara y organizada.
5. **El usuario puede acceder a enlaces directos** para trámites migratorios.

---

##  Módulos Clave

###  API de Datos Migratorios
- Endpoint:  
``` GET /api/requisitos?origen={pais_origen}&destino={pais_destino} ```

- Ejemplo de Respuesta JSON:
```json
{
  "pais_destino": "Canadá",
  "visa_requerida": true,
  "tipo_visa": "Turista - eTA",
  "enlace_tramite": "https://www.canada.ca/en/immigration",
  "vacunas_requeridas": ["Fiebre Amarilla"],
  "moneda": "Dólar Canadiense",
  "tipo_cambio": "1 CAD = 13.50 MXN"
}
```
🖥️ UI/UX - Interfaz de Usuario
** Pantalla principal: Selección de nacionalidad y país de destino.
** Pantalla de resultados:
- Requisitos migratorios.
- Vacunas recomendadas.
- Divisa y conversión.
- Botón de acceso a enlaces oficiales.

## Consideraciones
** Consideraciones Adicionales
- Escalabilidad: Modularización para añadir más países en el futuro.
- Multilenguaje: Soporte para español e inglés.
- Actualización de Datos: Consulta periódica a APIs externas para mantener información actualizada.

## Métricas
1 Web Vitals - Rendimiento
Largest Contentful Paint (LCP) – Tiempo en mostrar información de requisitos migratorios.
First Input Delay (FID) – Tiempo de respuesta tras elegir nacionalidad y destino.
Cumulative Layout Shift (CLS) – Estabilidad de la interfaz al cargar datos.
2 Conversión de Usuarios en la Consulta de Requisitos
Usuarios que inician una consulta vs. los que la completan.
Tiempo promedio para completar la búsqueda de requisitos.
Puntos de abandono en el proceso de consulta.
3  Seguimiento de Clics en Enlaces de Trámite
Usuarios que hacen clic en los enlaces de trámites oficiales.
Tasa de conversión: usuarios que ven los requisitos vs. los que acceden a trámites.
