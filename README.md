# Frontend - Angular Login App

Aplicación Angular con sistema de login JWT y conexión a API REST.

## 🚀 Inicio Rápido

### 1. Instalar dependencias
```bash
cd app-front
npm install
```

### 2. Configurar URL del backend

Edita `src/environments/environment.ts` para desarrollo local:
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:3000/api'  // URL de tu backend
};
```

Para producción, edita `src/environments/environment.prod.ts`:
```typescript
export const environment = {
  production: true,
  apiUrl: 'https://api.macrilplas.com/api'  // Cambia por tu URL
};
```

### 3. Iniciar servidor de desarrollo
```bash
npm start
```

O:
```bash
ng serve
```

La aplicación estará disponible en: `http://localhost:4200`

## 📦 Compilar para producción

```bash
npm run build
```

Los archivos compilados estarán en `dist/app-front/`

Para compilar con configuración de producción:
```bash
ng build --configuration production
```

## 🔐 Credenciales de Prueba

- **Usuario:** admin
- **Contraseña:** admin

## 📁 Estructura del Proyecto

```
src/
├── app/
│   ├── components/
│   │   ├── login/          # Componente de login
│   │   └── dashboard/      # Componente dashboard (protegido)
│   ├── guards/
│   │   └── auth.guard.ts   # Guard para rutas protegidas
│   ├── interceptors/
│   │   └── auth.interceptor.ts  # Interceptor para agregar JWT a peticiones
│   ├── models/
│   │   └── user.model.ts   # Interfaces TypeScript
│   └── services/
│       └── auth.service.ts  # Servicio de autenticación
├── environments/
│   ├── environment.ts       # Configuración desarrollo
│   └── environment.prod.ts  # Configuración producción
└── styles.css              # Estilos globales
```

## 🛡️ Características

- ✅ Login con JWT
- ✅ Rutas protegidas con Guards
- ✅ Interceptor HTTP automático
- ✅ Almacenamiento de token en localStorage
- ✅ Manejo de sesión
- ✅ UI moderna y responsiva
- ✅ Validación de formularios

## 📡 Endpoints Utilizados

### Login
```http
POST /api/auth/login
Body: { username: string, password: string }
```

### Verificar Token
```http
GET /api/auth/verify
Header: Authorization: Bearer {token}
```

### Logout
```http
POST /api/auth/logout
Header: Authorization: Bearer {token}
```

## 🔧 Scripts Disponibles

- `npm start` - Iniciar servidor de desarrollo
- `npm run build` - Compilar para producción
- `npm test` - Ejecutar tests
- `npm run watch` - Compilar en modo watch
- `ng serve --open` - Abrir automáticamente en el navegador

## 📝 Notas

- Asegúrate de que el backend esté corriendo antes de iniciar el frontend
- El token JWT se almacena en localStorage
- La sesión persiste mientras el token sea válido (24h por defecto)
- Las rutas protegidas redirigen a /login si no estás autenticado

## 🌐 Desplegar en Hostinger

### Opción 1: GitHub (Recomendado)
1. Sube el código a GitHub
2. Conecta el repositorio en Hostinger
3. Configura build command: `ng build --configuration production`
4. Carpeta de salida: `dist/app-front/browser`

### Opción 2: Archivo ZIP
1. Ejecuta: `ng build --configuration production`
2. Comprime la carpeta `dist/app-front/browser/`
3. Sube y extrae en el hosting

⚠️ **Importante:** Configura `.htaccess` para Angular routing:
```apache
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
```
