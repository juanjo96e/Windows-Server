# 🖥️ Laboratorio Sysadmin Windows: Simulación de red empresarial pequeña con Active Directory

Este proyecto simula una red empresarial utilizando **Windows Server 2016/2019** y **clientes Windows 10 Pro**, aplicando roles reales de una empresa ficticia de 10 empleados.

## 📌 Objetivo

Implementar una infraestructura empresarial básica para gestionar usuarios, permisos, políticas de grupo y perfiles móviles, basada en servicios de **Active Directory**.

## 🏗️ Infraestructura

- **1x Windows Server 2016/2019** (Controlador de dominio)
- **2x Windows 10 Pro** (Clientes unidos al dominio)
- Red local simulada en VirtualBox o Proxmox

## 🧩 Requisitos técnicos

- VirtualBox o Proxmox (o cualquier otro hipervisor)
- ISO de Windows Server 2016/2019
- ISO de Windows 10 Pro (no Home)
- Disco adicional virtual de 25 GB en el servidor

## 🧱 Estructura organizativa

### Departamentos

- **Sistemas** (3 empleados: 1 admin, 2 técnicos)
- **Desarrolladores** (5 empleados, divididos en Proyecto1 y Proyecto2)
- **Analista** (acceso solo lectura)
- **Director** (acceso total)

### Reglas por departamento

| Rol       | Unidad asignada | Perfil móvil | Permisos                                       |
|-----------|------------------|--------------|------------------------------------------------|
| Sistemas  | `Z:`             | No           | Acceso total a carpetas `administración` e `incidencias` |
| Devs      | `Y:`             | Sí           | Acceso a su proyecto específico                |
| Analista  | `X:`             | No           | Solo lectura a toda la documentación y código |
| Director  | -                | No           | Acceso total a todo                            |

## 🔨 Pasos principales

1. **Promoción del servidor como DC y creación del dominio `empresa.local`.**
2. **Configuración de IPs estáticas y DNS.**
3. **Creación de usuarios, OUs y grupos en Active Directory.**
4. **Modificación de políticas de contraseñas (sin complejidad, sin historial, sin vigencia).**
5. **Añadir disco E: etiquetado con el apellido, NTFS, 8K block size.**
6. **Crear estructura de carpetas en el disco E:\EMPRESA.**
7. **Asignar permisos NTFS según rol (eliminando herencia donde sea necesario).**
8. **Asignación de unidades mapeadas mediante GPO o scripts de inicio.**
9. **Unir clientes W10 al dominio.**
10. **Validar acceso correcto, montaje de carpetas y funcionamiento de perfiles móviles.**

## 📁 Estructura de carpetas sugerida

```
E:└── EMPRESA    ├── depart_sistemas    │   ├── administracion    │   └── incidencias    ├── desarrollo    │   ├── proyecto1    │   └── proyecto2    └── analista```

## ✅ Validación

- Verificación de acceso correcto a carpetas desde clientes.
- Montaje automático de unidades compartidas.
- Comprobación del funcionamiento de perfiles móviles (persistencia de configuraciones).
- Prueba de permisos de solo lectura (analista).
- Usuarios no autorizados no pueden acceder a otras carpetas.

---

¡Gracias por revisar este laboratorio!  
**Conecta conmigo en LinkedIn** si quieres ver más prácticas como esta.
