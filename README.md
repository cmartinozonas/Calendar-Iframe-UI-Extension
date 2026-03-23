# Calendar-Iframe-UI-Extension
# Calendar UI Extension (HubSpot)

UI Extension para HubSpot que añade una tarjeta personalizada en CRM y Help Desk, permitiendo abrir una agenda externa dentro de un modal iframe.

---

## Overview

Esta extensión añade una tarjeta llamada **"Agenda"** en:

* Contactos (CRM)
* Tickets (CRM)
* Help Desk (Service Hub)

Desde la tarjeta, el usuario puede:

* Abrir un modal
* Visualizar una agenda externa embebida
* Interactuar sin salir de HubSpot

---

## 🧱 Arquitectura

El proyecto utiliza **HubSpot UI Extensions** (plataforma 2025.2).

Estructura principal:

```
src/
  app/
    app-hsmeta.json
    cards/
      calendar-card-hsmeta.json
      helpdesk-card-hsmeta.json
      DisplayIframe.jsx
```

---

## ⚙️ Funcionalidad

La tarjeta muestra un botón:

**"Abrir Agenda"**

Al hacer clic:

* Se abre un modal
* Se carga una URL externa mediante iframe

Ejemplo:

```
https://cloud-s18.mnprogram.net/24.2.3.0/#/login
```

---

## 🔐 Requisitos técnicos

Para que el iframe funcione correctamente, el servidor externo debe permitir embebido.

Se requiere configurar:

```
Content-Security-Policy: frame-ancestors https://app.hubspot.com https://*.hubspot.com;
```

Y evitar:

```
X-Frame-Options: DENY
X-Frame-Options: SAMEORIGIN
```

---

## 📦 Instalación

### 1. Clonar repositorio

```
git clone <repo-url>
cd <project-folder>
```

---

### 2. Instalar dependencias

```
cd src/app
npm install
```

---

### 3. Configurar cuenta HubSpot

```
hs accounts add
hs accounts list
```

---

### 4. Validar proyecto

```
hs project validate --account=<ACCOUNT_ID>
```

---

### 5. Subir y desplegar

```
hs project upload --account=<ACCOUNT_ID>
hs project deploy --account=<ACCOUNT_ID>
```

---

## 🧩 Configuración de cards

### CRM (Contactos y Tickets)

Archivo:

```
calendar-card-hsmeta.json
```

* location: `crm.record.sidebar`
* objectTypes: `contacts`, `tickets`

---

### Help Desk

Archivo:

```
helpdesk-card-hsmeta.json
```

* location: `helpdesk.sidebar`
* objectTypes: `tickets`

---

## 👀 Uso en HubSpot

### CRM

1. Abrir contacto o ticket
2. Click en "Customize record"
3. Añadir la card **Agenda**

---

### Help Desk

1. Abrir conversación
2. Panel derecho
