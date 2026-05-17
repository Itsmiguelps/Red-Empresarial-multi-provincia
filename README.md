<div align="center">

```
██████╗ ███████╗██████╗     ███████╗███╗   ███╗██████╗ ██████╗ ███████╗███████╗ █████╗ ██████╗ ██╗ █████╗ ██╗
██╔══██╗██╔════╝██╔══██╗    ██╔════╝████╗ ████║██╔══██╗██╔══██╗██╔════╝██╔════╝██╔══██╗██╔══██╗██║██╔══██╗██║
██████╔╝█████╗  ██║  ██║    █████╗  ██╔████╔██║██████╔╝██████╔╝█████╗  ███████╗███████║██████╔╝██║███████║██║
██╔══██╗██╔══╝  ██║  ██║    ██╔══╝  ██║╚██╔╝██║██╔═══╝ ██╔══██╗██╔══╝  ╚════██║██╔══██║██╔══██╗██║██╔══██║██║
██║  ██║███████╗██████╔╝    ███████╗██║ ╚═╝ ██║██║     ██║  ██║███████╗███████║██║  ██║██║  ██║██║██║  ██║███████╗
╚═╝  ╚═╝╚══════╝╚═════╝     ╚══════╝╚═╝     ╚═╝╚═╝     ╚═╝  ╚═╝╚══════╝╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝╚═╝  ╚═╝╚══════╝
```


# 📦Infraestructura de Red Empresarial
**Diseño e implementación completa de una red empresarial distribuida con OSPF, VLANs, NAT, SSH y seguridad avanzada.**

> **Proyecto — Seguridad de redes**
> **👨‍💻 Autor:** Miguel Angel Peña Acevedo 

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet%20Tracer-005EA2?style=flat-square) ![OSPF](https://img.shields.io/badge/Enrutamiento-OSPF%20Multi--área-7ED321?style=flat-square) ![Seguridad](https://img.shields.io/badge/Seguridad-ACLs%20%26%20VTY-D0021B?style=flat-square) ![Segmentación](https://img.shields.io/badge/Segmentaci%C3%B3n-VLANs-0091FF?style=flat-square) ![NAT](https://img.shields.io/badge/Traducci%C3%B3n-NAT%20Overload-F5A623?style=flat-square)

---

## 📋 Descripción del Proyecto

Diseño e implementación de una infraestructura de red robusta, de alta disponibilidad y segura. La topología está estructurada mediante un núcleo jerárquico redundante (Core) que interconecta de manera eficiente un total de 5 provincias (sucursales regionales) junto con servicios críticos perimetrales.

### 🏢 Estructura Organizacional de la Red

| Sede / Nodo | Rol en la Red | Segmento IP Principal |
| :--- | :--- | :--- |
| 📍 **Core Central (R1, R2, R3)** | Núcleo y Conmutación Central | `10.0.0.0/8` |
| 🏙️ **Provincia 1 (R4)** | Sucursal Regional (VLAN 10 y 20) | `192.168.0.0/16` |
| 🌆 **Provincia 2 (R5)** | Sucursal Regional (VLAN 30 y 40) | `192.168.0.0/16` |
| 🏞️ **Provincia 3 (R6)** | Sucursal Regional (VLAN 50, 60, 70, 80) | `192.168.0.0/16` |
| 🌅 **Provincia 4 (R7)** | Sucursal Regional (VLAN 90 y 100) | `192.168.0.0/16` |
| 🌌 **Provincia 5 (R8)** | Sucursal Regional (VLAN 110 y 120) | `192.168.0.0/16` |
| 🌐 **Perímetro (ISP - R9)** | Salida a Internet y Servidor Web | `192.168.200.0/24` |

---

### 🎯 Objetivos Cumplidos

| # | Requisito | Estado |
|---|-----------|--------|
| 1 | Direccionamiento IP público y privado (VLSM) | ✅ |
| 2 | Inter-VLAN Routing por Router-on-Stick | ✅ |
| 3 | DHCP automático por VLAN | ✅ |
| 4 | Hostname descriptivo en todos los dispositivos | ✅ |
| 5 | VLAN Administrativa (VLAN 99) | ✅ |
| 6 | Cambio de VLAN nativa por defecto (→ VLAN 999) | ✅ |
| 7 | OSPF con autenticación MD5 | ✅ |
| 8 | Enrutamiento estático con redundancia | ✅ |
| 9 | Ruta por defecto propagada via OSPF | ✅ |
| 10 | NAT Overload (PAT) en R1 | ✅ |
| 11 | Router-on-Stick en routers de provincia | ✅ |
| 12 | Usuarios con contraseña cifrada MD5 | ✅ |
| 13 | Line VTY 0 4 exclusivamente | ✅ |
| 14 | Interfaces no usadas apagadas | ✅ |
| 15 | Telnet deshabilitado — Solo SSH v2 | ✅ |
| 16 | Búsqueda DNS deshabilitada | ✅ |
| 17 | Banner MOTD en todos los dispositivos | ✅ |
| 18 | IP administrativa en switches (VLAN 99) | ✅ |
| 19 | Port-Security máx. 2 MAC — acción shutdown | ✅ |
| 20 | VLSM completo (WAN /30, LAN /24, Admin /27) | ✅ |
| 21 | 5+ ACLs configuradas | ✅ |
| 22 | Configuraciones de seguridad adicionales | ✅ |

---

## 🗺️ Topología Oficial de la Infraestructura


<img width="1916" height="851" alt="Captura de pantalla 2026-05-17 005705" src="https://github.com/user-attachments/assets/073d8158-b54c-46c7-8f6d-ed3d05014c3e" />

---
## 📡 Direccionamiento IP (VLSM)

### 🌍 Redes WAN Públicas

| Enlace | Red | Router A | Router B |
|--------|-----|----------|----------|
| ISP ↔ R1 | `210.10.10.0/30` | `210.10.10.1` (ISP) | `210.10.10.2` (R1) |
| ISP ↔ R9 | `210.10.11.0/30` | `210.10.11.1` (ISP) | `210.10.11.2` (R9) |

### 🔗 Red WAN Privada Core — `10.0.0.0/24`

> Todos los enlaces usan `/30` → máscara `255.255.255.252` → 2 hosts útiles

| Enlace | Red | IP Router A | IP Router B |
|--------|-----|-------------|-------------|
| R1 ↔ R2 | `10.0.0.4/30` | `10.0.0.5` | `10.0.0.6` |
| R1 ↔ R3 | `10.0.0.8/30` | `10.0.0.9` | `10.0.0.10` |
| R2 ↔ R3 | `10.0.0.12/30` | `10.0.0.13` | `10.0.0.14` |
| R2 ↔ R4 | `10.0.0.16/30` | `10.0.0.17` | `10.0.0.18` |
| R3 ↔ R4 | `10.0.0.20/30` | `10.0.0.21` | `10.0.0.22` |
| R2 ↔ R5 | `10.0.0.24/30` | `10.0.0.25` | `10.0.0.26` |
| R3 ↔ R5 | `10.0.0.28/30` | `10.0.0.29` | `10.0.0.30` |
| R2 ↔ R6 | `10.0.0.32/30` | `10.0.0.33` | `10.0.0.34` |
| R3 ↔ R6 | `10.0.0.36/30` | `10.0.0.37` | `10.0.0.38` |
| R2 ↔ R7 | `10.0.0.40/30` | `10.0.0.41` | `10.0.0.42` |
| R3 ↔ R7 | `10.0.0.44/30` | `10.0.0.45` | `10.0.0.46` |
| R2 ↔ R8 | `10.0.0.48/30` | `10.0.0.49` | `10.0.0.50` |
| R3 ↔ R8 | `10.0.0.52/30` | `10.0.0.53` | `10.0.0.54` |

### 🖥️ VLAN Administrativa — `172.16.99.0/27`

> Máscara `255.255.255.224` — 30 hosts disponibles

| Dispositivo | IP Administrativa | Gateway |
|-------------|------------------|---------|
| R4 (Gateway Prov. 1) | `172.16.99.1` | N/A |
| SW0 | `172.16.99.2` | `172.16.99.1` |
| SW1 | `172.16.99.3` | `172.16.99.1` |
| R5 (Gateway Prov. 2) | `172.16.99.4` | N/A |
| SW2 | `172.16.99.5` | `172.16.99.4` |
| SW3 | `172.16.99.6` | `172.16.99.4` |
| R6 (Gateway Prov. 3) | `172.16.99.7` | N/A |
| SW4 | `172.16.99.8` | `172.16.99.7` |
| SW5 | `172.16.99.9` | `172.16.99.7` |
| SW6 | `172.16.99.10` | `172.16.99.7` |
| R7 (Gateway Prov. 4) | `172.16.99.11` | N/A |
| SW7-r7 | `172.16.99.12` | `172.16.99.11` |
| SW8-r7 | `172.16.99.13` | `172.16.99.11` |
| R8 (Gateway Prov. 5) | `172.16.99.14` | N/A |
| SW10 | `172.16.99.15` | `172.16.99.14` |
| SW9 | `172.16.99.16` | `172.16.99.14` |
| SW11 | `172.16.99.17` | `172.16.99.14` |

---

## 🔀 VLANs Configuradas

| VLAN | Nombre | Red | Gateway | Provincia | Hosts |
|------|--------|-----|---------|-----------|-------|
| **10** | TI | `192.168.10.0/24` | `192.168.10.1` | 1 — R4 | 254 |
| **20** | RRHH | `192.168.20.0/24` | `192.168.20.1` | 1 — R4 | 254 |
| **30** | Contabilidad | `192.168.30.0/24` | `192.168.30.1` | 2 — R5 | 254 |
| **40** | Marketing | `192.168.40.0/24` | `192.168.40.1` | 2 — R5 | 254 |
| **50** | Ventas | `192.168.50.0/24` | `192.168.50.1` | 3 — R6 | 254 |
| **60** | Finanzas | `192.168.60.0/24` | `192.168.60.1` | 3 — R6 | 254 |
| **70** | Logística | `192.168.70.0/24` | `192.168.70.1` | 3 — R6 | 254 |
| **80** | Calidad | `192.168.80.0/24` | `192.168.80.1` | 3 — R6 | 254 |
| **90** | Compras | `192.168.90.0/24` | `192.168.90.1` | 4 — R7 | 254 |
| **100** | Almacén | `192.168.100.0/24` | `192.168.100.1` | 4 — R7 | 254 |
| **110** | Asistente | `192.168.110.0/24` | `192.168.110.1` | 5 — R8 | 254 |
| **120** | CRS | `192.168.120.0/24` | `192.168.120.1` | 5 — R8 | 254 |
| **99** | ADMIN | `172.16.99.0/27` | `172.16.99.x` | Todas | Admin |
| **999** | NATIVE | — | — | Todas | VLAN nativa trunk |

---

## 📂 Organización del Repositorio
## 📁 Estructura del Repositorio

```
📦 red-empresarial-multi-provincia/
│
├── 📄 README.md                          ← Este archivo
│
├── 📁 configs/
│   ├── 📁 core/
│   │   ├── 📄 ISP.txt                   ← Configuración del ISP
│   │   ├── 📄 R1-core.txt               ← R1 (NAT + Core principal)
│   │   ├── 📄 R2-core.txt               ← R2 (Distribución)
│   │   ├── 📄 R3-core.txt               ← R3 (Distribución backup)
│   │   └── 📄 R9-servidor.txt           ← R9 (Zona servidor web)
│   │
│   ├── 📁 provincias/
│   │   ├── 📄 R4-provincia1.txt         ← R4 | VLANs 10, 20
│   │   ├── 📄 R5-provincia2.txt         ← R5 | VLANs 30, 40
│   │   ├── 📄 R6-provincia3.txt         ← R6 | VLANs 50, 60, 70, 80
│   │   ├── 📄 R7-provincia4.txt         ← R7 | VLANs 90, 100
│   │   └── 📄 R8-provincia5.txt         ← R8 | VLANs 110, 120
│   │
│   └── 📁 switches/
│       ├── 📄 SW0.txt                   ← SW0 | VLAN 10 | 172.16.99.2
│       ├── 📄 SW1.txt                   ← SW1 | VLAN 20 | 172.16.99.3
│       ├── 📄 SW2.txt                   ← SW2 | VLAN 30 | 172.16.99.5
│       ├── 📄 SW3.txt                   ← SW3 | VLAN 40 | 172.16.99.6
│       ├── 📄 SW4.txt                   ← SW4 | VLAN 50,60 | 172.16.99.8
│       ├── 📄 SW5.txt                   ← SW5 | VLAN 70,80 | 172.16.99.9
│       ├── 📄 SW6.txt                   ← SW6 | Distribución Prov.3 | 172.16.99.10
│       ├── 📄 SW7-r7.txt               ← SW7 | VLAN 90 | 172.16.99.12
│       ├── 📄 SW8-r7.txt               ← SW8 | VLAN 100 | 172.16.99.13
│       ├── 📄 SW9.txt                   ← SW9 | VLAN 110 | 172.16.99.16
│       ├── 📄 SW10.txt                  ← SW10 | Distribución Prov.5 | 172.16.99.15
│       └── 📄 SW11.txt                  ← SW11 | VLAN 120 | 172.16.99.17
│
└── 📁 docs/
    ├── 📄 Documentacion_Red_Completa.docx   ← Documentación técnica completa
    └── 📄 VLSM_COMPLETO.docx                ← Tablas VLSM detalladas
```

---

## 🚀 Cómo Usar

### Requisitos

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) `8.x` o superior
- Conocimientos básicos de CLI Cisco IOS

### Pasos para Implementar

**1. Orden de configuración recomendado**

```
1️⃣  ISP           → configs/core/ISP.txt
2️⃣  R1            → configs/core/R1-core.txt
3️⃣  R2 y R3       → configs/core/R2-core.txt  |  R3-core.txt
4️⃣  R9            → configs/core/R9-servidor.txt
5️⃣  R4 → R8       → configs/provincias/R4-provincia1.txt  (etc.)
6️⃣  SW0 → SW11    → configs/switches/SW0.txt  (etc.)
```

**2. Aplicar configuración en cada dispositivo**

```cisco
! En Packet Tracer, abre el CLI del dispositivo y pega el contenido del archivo
enable
configure terminal
! ... pegar configuración ...
end
write memory
```

---

## ✅ Verificación

### Verificar conectividad OSPF
```cisco
show ip ospf neighbor
show ip route ospf
show ip ospf interface
```

### Verificar VLANs
```cisco
show vlan brief
show interfaces trunk
```

### Verificar DHCP
```cisco
show ip dhcp binding
show ip dhcp pool
```

### Verificar NAT
```cisco
show ip nat translations
show ip nat statistics
```

### Verificar SSH y acceso
```cisco
show ip ssh
show ssh
show users
```

### Verificar Port-Security
```cisco
show port-security
show port-security address
```

### Verificar ACLs
```cisco
show access-lists
show ip access-lists
```

---

## 📊 Estadísticas del Proyecto

<div align="center">

| Métrica | Valor |
|---------|-------|
| 🖥️ Routers configurados | 9 (ISP, R1-R3, R4-R8, R9) |
| 🔀 Switches configurados | 11 (SW0-SW11) |
| 📡 VLANs de usuario | 12 |
| 🔗 Enlaces WAN totales | 15 |
| 📦 Pools DHCP | 12 |
| 🛡️ ACLs totales | 7 |
| 🌐 NAT Overload | 1 (en R1) |
| 🔒 Port-Security ports | ~40+ puertos |
| 💻 Hosts máximos soportados | 3,048 |
| 🏛️ Protocolo de ruteo | OSPF Área 0 con MD5 |

</div>

---

<div align="center">

---

**⭐ Si este proyecto te fue útil, dale una estrella al repositorio ⭐**

Hecho con 💙 por **Miguel Angel Peña Acevedo**  
`ITLA • Seguridad de Redes • 2025`

</div>

