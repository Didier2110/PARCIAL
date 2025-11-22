# 🚀 Instrucciones para Ejecutar y Probar - Mejoras de Interfaces

## ⚡ INICIO RÁPIDO

### Opción 1: Desde Spring Tools Suite (Recomendado)

1. **Abre el proyecto en STS**
   ```
   File → Open Projects from File System
   Selecciona: c:\SPRINGTOOL\saberpro-system
   ```

2. **Limpia el proyecto**
   ```
   Click derecho en proyecto → Maven → Update Project
   ```

3. **Ejecuta la aplicación**
   ```
   Click derecho en proyecto → Run As → Spring Boot App
   O presiona: Shift + F10
   ```

4. **Espera a que inicie**
   ```
   Verás en consola:
   "Started SaberProApplication in X.XXX seconds"
   ```

5. **Accede a la aplicación**
   ```
   Abre navegador: http://localhost:8080/login
   ```

---

### Opción 2: Desde Terminal PowerShell

```powershell
# Navega al directorio
cd c:\SPRINGTOOL\saberpro-system

# Ejecuta con Maven
.\mvnw spring-boot:run

# O ejecuta el JAR compilado
java -jar target\saberpro-system-1.0.0.jar
```

---

### Opción 3: Desde Línea de Comandos (Cmd)

```cmd
cd c:\SPRINGTOOL\saberpro-system
mvnw.cmd spring-boot:run
```

---

## 🔑 Credenciales de Prueba

### Administrador
```
Email:    admin@saberpro.edu.co
Password: admin123
```

### Coordinador
```
Email:    coordinacion@uts.edu.co
Password: coord123
```

### Estudiante (elige cualquiera)
```
Email:    estudiante01@uts.edu.co
Password: estudiante123

O: estudiante02@uts.edu.co hasta estudiante36@uts.edu.co
```

---

## ✅ Checklist de Prueba - Dashboard Principal

### Prueba 1: Login ADMIN

- [ ] Ingresa credenciales admin
- [ ] Click en "Login"
- [ ] Redirecciona a dashboard
- [ ] **Verifica que veas:**
  - Bienvenida con tu email
  - 3 tarjetas de estadísticas (púrpura)
  - Panel de Administración visible
  - Botones: Gestionar, Crear, Estadísticas
  - **NO debería ver:** Opciones de coordinación

**Resultado esperado:**
```
Dashboard con:
- Total Usuarios: 38
- Administradores: 1
- Estudiantes: 36
```

### Prueba 2: Login COORDINACIÓN

- [ ] Logout (arriba derecha)
- [ ] Regresa a login
- [ ] Ingresa: coordinacion@uts.edu.co / coord123
- [ ] **Verifica que veas:**
  - 4 tarjetas de estudiantes (verde)
  - Panel de Gestión de Estudiantes
  - Botones: Ver, Nuevo, Beneficiarios, Informes
  - **NO debería ver:** Gestión de Usuarios

**Resultado esperado:**
```
Dashboard con:
- Total Estudiantes: 36
- Con Puntajes: 36
- Con Beneficios: 36
- Sin Puntaje: 0
```

### Prueba 3: Login ESTUDIANTE

- [ ] Logout
- [ ] Regresa a login
- [ ] Ingresa: estudiante01@uts.edu.co / estudiante123
- [ ] **Verifica que veas:**
  - Interfaz simplificada
  - Opción: Mi Identificación
  - Opción: Mis Resultados
  - Tarjetas de beneficios (información)
  - **NO debería ver:** Nada de admin ni coordinación

**Resultado esperado:**
```
Dashboard simple con:
- Formulario para consulta
- Información de beneficios
- Acceso a resultados personales
```

---

## ✅ Checklist de Prueba - Tabla de Usuarios (ADMIN)

### Desde el Dashboard Admin:

1. **Click en "Gestionar Usuarios"**
   ```
   O accede directamente: http://localhost:8080/admin/usuarios
   ```

2. **Verifica la tabla:**
   - [ ] Muestra 38 usuarios
   - [ ] Tabla tiene columnas: ID, Nombre, Email, Rol, Estado, Acciones
   - [ ] Badges de rol con colores:
     - Rojo para ADMIN
     - Naranja para COORDINACION
     - Azul para ESTUDIANTE
   - [ ] Badges de estado: Verde (Activo) o Gris (Inactivo)

3. **Prueba interactividad:**
   - [ ] Hover en una fila → Se levanta y cambia fondo
   - [ ] Hover en botón editar → Efecto visual
   - [ ] Hover en botón eliminar → Efecto visual

4. **Prueba botones:**
   - [ ] Click en "Editar" → Abre formulario de edición
   - [ ] Click en "Eliminar" → Abre confirmación
     - [ ] Click Cancel → No elimina, vuelve a tabla
     - NO completes la eliminación
   - [ ] Click en "Nuevo Usuario" → Abre formulario crear

5. **Vuelve al dashboard:**
   - [ ] Click en botón "Atrás"
   - [ ] Click en logo "Saber Pro UTS"
   - Ambos deben redirigir al dashboard

---

## ✅ Checklist de Prueba - Consulta Estudiante

### Desde el Dashboard Estudiante:

1. **Click en "Mi Identificación"**

2. **Verifica el formulario:**
   - [ ] Campo para documento visible
   - [ ] Placeholder muestra ejemplo
   - [ ] Texto ayuda visible
   - [ ] Botones: "Buscar Resultados" y "Volver"

3. **Prueba el formulario:**
   - [ ] Ingresa número válido: 1000000001
   - [ ] Click en "Buscar Resultados"
   - [ ] Debe mostrar datos del estudiante

4. **Verifica tarjetas de beneficios:**
   - [ ] Tarjeta EXCELENTE (241+) → Púrpura
     - Nota 5.0 + Beca 100%
   - [ ] Tarjeta MUY BUENO (211-240) → Naranja
     - Nota 4.7 + Beca 50%
   - [ ] Tarjeta BUENO (180-210) → Azul
     - Nota 4.5
   - [ ] Tarjeta INSUFICIENTE (<80) → Rojo
     - No puede graduarse

5. **Verifica información adicional:**
   - [ ] Sección "¿Cómo usar?"
   - [ ] Alerta de información importante
   - [ ] Contacto de soporte visible

---

## 📱 Pruebas de Responsive

### Desktop (1920x1080)
```powershell
# Abre navegador Chrome/Firefox
http://localhost:8080/login

Verifica:
☐ Navbar normal (no hamburguesa)
☐ Layout completo (sin scrolls horizontales)
☐ Tarjetas en filas completas
☐ Tabla sin scroll horizontal
```

### Tablet (768px)
```powershell
# Abre DevTools: F12
# Selecciona modo dispositivo
# Selecciona "iPad" o 768x1024

Verifica:
☐ Navbar normal
☐ Algunas columnas pueden scrollear
☐ Tarjetas apiladas en 2 columnas
☐ Tabla con scroll si es necesaria
```

### Móvil (375px)
```powershell
# DevTools: F12
# Selecciona "Mobile"

Verifica:
☐ Navbar con hamburguesa
☐ Todo apilado verticalmente
☐ Tabla con scroll horizontal
☐ Botones clickeables (suficiente tamaño)
☐ Texto legible sin zoom
```

---

## 🎨 Verificación Visual

### Colores Esperados

#### Dashboard ADMIN
```
Fondo de página: Gradiente púrpura (#667eea → #764ba2)
Navbar: Gradiente oscuro (#1a1a2e → #16213e)
Tarjetas: Blanco con sombras
Estadísticas: Con gradientes de color
```

#### Dashboard COORDINACIÓN
```
Tarjeta estudiantes: Gradiente verde (#11998e → #38ef7d)
Efectos: Mismos gradientes oscuros
```

#### Dashboard ESTUDIANTE
```
Tarjeta consulta: Gradiente azul (#4facfe → #00f2fe)
Tarjetas beneficios: Varios gradientes según nivel
```

### Efectos Esperados
```
Hover en tarjetas:
☐ Suben 8px verticalmente
☐ Sombra aumenta
☐ Animación suave (0.3s)

Hover en botones:
☐ Suben 3px
☐ Sombra coloreada del botón
☐ Cambio de opacidad

Hover en filas tabla:
☐ Fondo ligeramente coloreado
☐ Escala aumenta a 1.01
☐ Efecto natural
```

---

## 🔒 Verificación de Seguridad

### Admin NO debería poder acceder a:
```
- ❌ /coordinacion/estudiantes (acceso negado)
- ❌ /estudiante/resultado (sin rol de estudiante)
```

### Coordinador NO debería poder acceder a:
```
- ❌ /admin/usuarios (acceso negado)
- ❌ No ve botones de admin en dashboard
```

### Estudiante NO debería poder acceder a:
```
- ❌ /admin/* (acceso negado)
- ❌ /coordinacion/* (acceso negado)
```

### Prueba:
```
1. Login como ADMIN
2. Abre URL: http://localhost:8080/coordinacion/estudiantes
3. Debería redirigir a Access Denied
```

---

## 🐛 Solución de Problemas

### Problema: "La aplicación no inicia"

**Solución:**
```powershell
# Limpia y reconstruye
.\mvnw clean package -DskipTests

# Si falla, verifica Java
java -version

# Debe ser Java 17 o superior
java version "17.0.x"
```

### Problema: "Base de datos vacía"

**Solución:**
```sql
# Ejecuta el script en MySQL
source c:/SPRINGTOOL/saberpro-system/database-setup.sql

# O manualmente en MySQL Workbench
-- Ver archivo database-setup.sql
```

### Problema: "Credenciales no funcionan"

**Solución:**
1. Verifica que BD está cargada (38 usuarios)
2. Usa exactamente: admin@saberpro.edu.co (con punto en saberpro)
3. Contraseña sin espacios: admin123

### Problema: "Estilos no se cargan"

**Solución:**
```
1. Limpia caché: Ctrl + Shift + Delete
2. Recarga página: Ctrl + F5
3. Verifica conexión a CDN (Bootstrap, FontAwesome)
4. Abre DevTools: F12 → Network → Verifica CSS cargan
```

### Problema: "Tabla vacía en admin"

**Solución:**
1. Verifica login como admin realmente
2. Ejecuta: SELECT COUNT(*) FROM usuarios; en BD
3. Si está vacía, ejecuta database-setup.sql
4. Reinicia aplicación

### Problema: "Botones no responden"

**Solución:**
```
1. Abre consola JavaScript: F12 → Console
2. Verifica si hay errores
3. Recarga página: F5
4. Limpia caché: Ctrl + Shift + Delete
5. Reinicia navegador
```

---

## 📊 Validación Final

Después de todas las pruebas, completa esto:

```
INTERFACES GRÁFICAS
☐ Dashboard ADMIN funciona
☐ Dashboard COORDINACIÓN funciona
☐ Dashboard ESTUDIANTE funciona
☐ Cada dashboard es diferente
☐ Solo muestra opciones permitidas

ESTILO Y DISEÑO
☐ Gradientes visibles y bonitos
☐ Efectos hover funcionan
☐ Colores consistentes
☐ Textos legibles
☐ Iconos claros

FUNCIONALIDAD
☐ Links llevan a destino correcto
☐ Botones ejecutan acciones
☐ Formularios validan entrada
☐ Logouts funcionan
☐ Redireccionamientos automáticos

RESPONSIVE
☐ Desktop se ve bien
☐ Tablet se ve bien
☐ Móvil se ve bien
☐ Sin scrolls horizontales innecesarios
☐ Textos legibles en todos los tamaños

SEGURIDAD
☐ Admin solo ve opciones admin
☐ Coordinador solo ve coordinación
☐ Estudiante solo ve estudiante
☐ Acceso denegado cuando intenta forzar URL
☐ Logout funciona correctamente
```

---

## 🎓 Documentación Referencia

Archivos creados en el proyecto:

1. **MEJORAS-INTERFACES.md**
   - Detalles técnicos completos
   - CSS y gradientes
   - Descripción de cambios

2. **GUIA-PRUEBA-INTERFACES.md**
   - Guía paso a paso
   - Para cada rol
   - Troubleshooting

3. **RESUMEN-MEJORAS.txt**
   - Vista rápida
   - Antes vs después
   - Métricas

4. **Este archivo**
   - Instrucciones de ejecución
   - Checklist de prueba
   - Solución de problemas

---

## 📞 Contacto / Soporte

Si algo no funciona:

1. Verifica que la aplicación está iniciada
   ```
   http://localhost:8080/login
   ```

2. Verifica logs de consola
   ```
   En STS: Ventana "Console"
   O en terminal: Salida de comandos
   ```

3. Revisa archivos de documentación
   ```
   MEJORAS-INTERFACES.md
   GUIA-PRUEBA-INTERFACES.md
   ```

4. Verifica base de datos
   ```
   SELECT COUNT(*) FROM usuarios;
   -- Debe retornar: 38
   ```

---

## ✅ Resumen Rápido

```
1. INICIA aplicación Spring Boot
2. ACCEDE a http://localhost:8080/login
3. PRUEBA con admin@saberpro.edu.co / admin123
4. VERIFICA dashboard personalizado aparece
5. EXPLORA opciones de tu rol
6. LOGOUT y REPITE con otros roles
7. PRUEBA en móvil
8. MARCA TODO COMPLETADO ✅
```

---

*Sistema Saber Pro UTS v1.0.0*
*Instrucciones de Ejecución*
*17 de noviembre de 2024*
