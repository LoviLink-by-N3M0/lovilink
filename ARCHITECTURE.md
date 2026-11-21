# LoviLink by N3M0 — System Architecture

### Network Operations & Business Management Platform

**Document type:** System Architecture  
**Project:** LoviLink by N3M0  
**Architecture version:** 1.0  
**Development status:** Architecture definition and gradual implementation  
**Copyright holder:** N3M0

---

# English

## 1. Architecture Overview

LoviLink is designed as a modular Network Operations & Business Management Platform.

The platform combines network monitoring, infrastructure management, subscriber operations, service management, analytics, and optional integrations within a unified application.

The architecture follows an incremental development approach: existing working components are preserved and extended where technically appropriate.

The system is intended to operate independently without requiring third-party monitoring or billing platforms.

## 2. Architectural Principles

The architecture is based on the following principles:

1. **Modularity** — functional areas are separated into logical modules.
2. **Independence** — core functionality does not require external platforms.
3. **Extensibility** — new modules can be introduced without unnecessary redesign.
4. **Data consistency** — shared infrastructure and operational data should have clear ownership.
5. **Security** — authentication, role-based permissions, and auditability.
6. **Maintainability** — clear separation between application layers.
7. **Compatibility** — existing collectors and integrations should be preserved where possible.
8. **Scalability** — the architecture should support gradual growth in devices, subscribers, and operational workloads.

## 3. High-Level Architecture

The target architecture consists of the following logical layers:

```text
+------------------------------------------------------+
|                    USER INTERFACE                    |
|                                                      |
| Dashboard | Devices | Topology | Subscribers         |
| Billing | Incidents | Service Desk | Analytics       |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                  APPLICATION LAYER                   |
|                                                      |
| NMS | OSS | BSS | CRM | Analytics | Administration   |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                     SERVICE LAYER                    |
|                                                      |
| Authentication | Permissions | Business Logic       |
| Event Processing | Notifications | Task Management   |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                     DATA LAYER                       |
|                                                      |
| Device Data | Historical Metrics | Events            |
| Subscribers | Services | Contracts | Inventory       |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                INFRASTRUCTURE LAYER                   |
|                                                      |
| Poller | Collectors | Network Devices | External APIs|
+------------------------------------------------------+
```

This diagram describes the target logical architecture. It does not imply that all modules are already implemented as separate services.

## 4. Existing Technical Foundation

The original NetWatch2 project provides the foundation for LoviLink.

The currently established technical direction includes:

| Component | Responsibility |
|---|---|
| Python | Backend application logic |
| FastAPI | HTTP API and application endpoints |
| Poller | Scheduled device monitoring |
| Collectors | Equipment-specific data collection |
| Cache | Access to recently collected information |
| Historical data | Storage and retrieval of monitoring history |
| Event processing | Detection and handling of monitoring events |
| Notifications | External alert delivery, including ntfy |
| Web interface | Dashboard and operational controls |

The existing implementation is being developed incrementally. Exact implementation details and technology dependencies are subject to technical verification.

## 5. Core Modules

### 5.1 NMS — Network Management System

The NMS module is responsible for network monitoring and equipment status.

Planned responsibilities:

- Device inventory.
- Device discovery and registration.
- Availability monitoring.
- Performance metrics.
- Signal quality monitoring.
- Historical measurements.
- Thresholds and triggers.
- Event severity and prioritization.
- Alert notifications.
- SLA monitoring.

The existing Poller and equipment collectors form the foundation of this module.

### 5.2 OSS — Operations Support System

The OSS module manages network infrastructure and operational resources.

Planned responsibilities:

- Network topology.
- Infrastructure inventory.
- Network connections.
- IP address management.
- Provider and uplink management.
- Equipment locations.
- Maintenance records.
- Infrastructure change history.

### 5.3 BSS — Business Support System

The BSS module provides subscriber and service management.

Planned responsibilities:

- Subscriber records.
- Customer accounts.
- Contracts.
- Tariff plans.
- Service packages.
- Connection status.
- Personal accounts.
- Charges and payments.
- Billing history.

Financial operations must use controlled and auditable business logic.

### 5.4 CRM and Service Desk

This module manages customer interactions and operational tasks.

Planned responsibilities:

- Customer requests.
- Technical support tickets.
- Incident registration.
- Task assignment.
- Responsibility tracking.
- Service history.
- Notifications.
- Resolution tracking.

### 5.5 Analytics

The analytics module provides operational and business reporting.

Planned responsibilities:

- Network performance reports.
- Availability statistics.
- Signal quality trends.
- Incident analysis.
- SLA reports.
- Subscriber statistics.
- Operational dashboards.

## 6. Monitoring Data Flow

The target monitoring workflow is:

```text
Network Equipment
       |
       v
Equipment Collector
       |
       v
Poller
       |
       v
Data Validation
       |
       v
Cache / Historical Storage
       |
       v
Event Processing
       |
       +------------------+
       |                  |
       v                  v
Dashboard             Notifications
       |
       v
Analytics and Reports
```

The workflow represents the intended logical process. Specific storage and processing mechanisms depend on the implementation of each component.

## 7. Application API

FastAPI provides the HTTP API foundation.

Existing API areas include:

| Endpoint | Purpose |
|---|---|
| `/api/devices` | Device information |
| `/api/cache` | Cached monitoring data |
| `/api/clients` | Connected client information |
| `/api/diagnostics` | Diagnostic information |
| `/api/device/{device_id}/history` | Device monitoring history |
| `/users` | User-related operations |

These endpoints describe the existing API surface known during architecture preparation. Their exact behavior and access restrictions must be verified against the current source code.

Future API development should use consistent resource naming, validation, authentication, authorization, and documented response formats.

## 8. Data Architecture

The platform requires structured management of several data domains:

- Network devices.
- Device measurements.
- Historical monitoring records.
- Events and alerts.
- Infrastructure resources.
- Network connections.
- Subscribers and customer accounts.
- Contracts and services.
- Billing records.
- Support requests.
- User accounts and permissions.
- Audit records.

The data model should distinguish technical monitoring records from business and financial records.

Changes to critical business data must be traceable.

The final database schema and storage technologies will be documented after source-code and database auditing.

## 9. Security and Access Control

The target security model includes:

- Authenticated user sessions.
- Role-based access control.
- Engineer and operator permissions.
- Restricted access to technical diagnostics.
- Protected administrative operations.
- Audit logging.
- Secure configuration management.
- Backup and recovery procedures.
- Protection of credentials and infrastructure secrets.

Access permissions should be enforced on the backend, not only by hiding interface elements.

## 10. Integrations

LoviLink is designed to operate independently.

External integrations are optional and may include:

- Zabbix.
- Network equipment APIs.
- Notification services.
- External billing systems.
- Third-party service platforms.

Integration should use documented interfaces and should not make core LoviLink functionality dependent on an external product.

## 11. Deployment Architecture

The existing project has a Linux-based deployment foundation.

The deployment model is intended to support:

- Backend application service.
- Web interface delivery.
- Data storage.
- Monitoring workers.
- Notification delivery.
- Secure external access.
- Backup and recovery.

Production deployment details, network addresses, credentials, and server configuration are intentionally excluded from this public document.

## 12. Future Architecture Development

The architecture will evolve through the following directions:

1. Consolidation of the existing monitoring foundation.
2. Separation of logical application modules.
3. Expansion of infrastructure management.
4. Introduction of subscriber and billing domains.
5. Introduction of CRM and service workflows.
6. Unified analytics and reporting.
7. API standardization and optional integrations.
8. Security, performance, and production readiness.

See [ROADMAP.md](ROADMAP.md) for the planned development phases.

---

# Русский

## 1. Обзор архитектуры

LoviLink проектируется как модульная платформа управления сетевой инфраструктурой и бизнес-процессами — Network Operations & Business Management Platform.

Платформа объединяет мониторинг сети, управление инфраструктурой, абонентские операции, обслуживание услуг, аналитику и необязательные интеграции в едином программном решении.

Разработка ведётся поэтапно: существующие работающие компоненты сохраняются и развиваются там, где это технически оправдано.

Система должна иметь возможность самостоятельной работы без обязательной зависимости от сторонних платформ мониторинга или биллинга.

## 2. Архитектурные принципы

Архитектура основывается на следующих принципах:

1. **Модульность** — функциональные направления разделяются на логические модули.
2. **Независимость** — основные функции не требуют обязательного подключения внешних платформ.
3. **Расширяемость** — новые модули добавляются без необоснованной переработки системы.
4. **Целостность данных** — у общих инфраструктурных и операционных данных должны быть определены правила хранения и использования.
5. **Безопасность** — авторизация, разграничение прав и возможность аудита действий.
6. **Сопровождаемость** — чёткое разделение уровней приложения.
7. **Совместимость** — существующие сборщики данных и интеграции сохраняются там, где это возможно.
8. **Масштабируемость** — возможность постепенного увеличения количества устройств, абонентов и операционных задач.

## 3. Общая архитектура

Целевая архитектура состоит из следующих логических уровней:

```text
+------------------------------------------------------+
|                  ПОЛЬЗОВАТЕЛЬСКИЙ ИНТЕРФЕЙС          |
|                                                      |
| Обзор | Устройства | Топология | Абоненты            |
| Биллинг | Инциденты | Заявки | Аналитика             |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                  УРОВЕНЬ ПРИЛОЖЕНИЯ                  |
|                                                      |
| NMS | OSS | BSS | CRM | Аналитика | Администрирование|
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                  СЕРВИСНЫЙ УРОВЕНЬ                   |
|                                                      |
| Авторизация | Права | Бизнес-логика                 |
| События | Уведомления | Управление задачами          |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                   УРОВЕНЬ ДАННЫХ                     |
|                                                      |
| Устройства | История метрик | События                |
| Абоненты | Услуги | Договоры | Оборудование          |
+------------------------------------------------------+
                         |
                         v
+------------------------------------------------------+
|                ИНФРАСТРУКТУРНЫЙ УРОВЕНЬ              |
|                                                      |
| Poller | Сборщики | Сетевое оборудование | Внешние API|
+------------------------------------------------------+
```

Схема описывает целевую логическую архитектуру. Она не означает, что все модули уже реализованы в виде отдельных сервисов.

## 4. Существующая техническая основа

Первоначальный проект NetWatch2 является технической основой для развития LoviLink.

На данный момент существующее направление разработки включает:

| Компонент | Назначение |
|---|---|
| Python | Серверная логика приложения |
| FastAPI | HTTP API и прикладные интерфейсы |
| Poller | Периодический опрос оборудования |
| Collectors | Сбор данных с конкретных типов оборудования |
| Cache | Доступ к недавно собранным данным |
| История | Хранение и получение истории мониторинга |
| Обработка событий | Обнаружение и обработка событий мониторинга |
| Уведомления | Передача оповещений, в том числе через ntfy |
| Web-интерфейс | Панель мониторинга и управления |

Существующая реализация развивается постепенно. Точные технические детали и зависимости подлежат проверке по актуальному исходному коду.

## 5. Основные модули платформы

### 5.1 NMS — система управления и мониторинга сети

Модуль NMS отвечает за мониторинг сети и контроль состояния оборудования.

Планируемые функции:

- Реестр сетевых устройств.
- Обнаружение и регистрация оборудования.
- Контроль доступности.
- Мониторинг производительности.
- Контроль уровня и качества сигнала.
- История измерений.
- Пороговые значения и триггеры.
- Классификация и приоритизация событий.
- Уведомления об авариях.
- Контроль SLA.

Существующие Poller и сборщики данных с оборудования являются основой данного модуля.

### 5.2 OSS — управление сетевой инфраструктурой

Модуль OSS предназначен для учёта и управления инфраструктурой.

Планируемые функции:

- Сетевая топология.
- Реестр инфраструктуры.
- Учёт сетевых соединений.
- Управление IP-адресами.
- Учёт провайдеров и вышестоящих подключений.
- Размещение оборудования.
- История технического обслуживания.
- Учёт изменений инфраструктуры.

### 5.3 BSS — абонентская система и биллинг

Модуль BSS предназначен для управления абонентами и предоставляемыми услугами.

Планируемые функции:

- База данных абонентов.
- Клиентские учётные записи.
- Договоры.
- Тарифные планы.
- Пакеты услуг.
- Управление состоянием подключений.
- Лицевые счета.
- Начисления и платежи.
- История биллинговых операций.

Финансовые операции должны выполняться по контролируемой бизнес-логике с возможностью аудита.

### 5.4 CRM и Service Desk

Данный модуль предназначен для управления взаимодействием с клиентами и техническими задачами.

Планируемые функции:

- Обращения клиентов.
- Заявки в техническую поддержку.
- Регистрация инцидентов.
- Назначение исполнителей.
- Контроль ответственности.
- История обслуживания.
- Уведомления.
- Контроль выполнения и закрытия заявок.

### 5.5 Аналитика

Модуль аналитики предназначен для формирования технической и бизнес-отчётности.

Планируемые функции:

- Отчёты о производительности сети.
- Статистика доступности.
- Динамика качества сигнала.
- Анализ инцидентов.
- Отчёты SLA.
- Статистика абонентов.
- Операционные панели мониторинга.

## 6. Поток данных мониторинга

Целевой процесс мониторинга:

```text
Сетевое оборудование
        |
        v
Сборщик данных оборудования
        |
        v
Poller
        |
        v
Проверка и обработка данных
        |
        v
Кэш / Историческое хранилище
        |
        v
Обработка событий
        |
        +-------------------+
        |                   |
        v                   v
Панель мониторинга     Уведомления
        |
        v
Аналитика и отчёты
```

Схема отражает предполагаемый логический процесс. Конкретные механизмы хранения и обработки определяются реализацией соответствующих компонентов.

## 7. Прикладной API

FastAPI является основой HTTP API платформы.

К существующим направлениям API относятся:

| Endpoint | Назначение |
|---|---|
| `/api/devices` | Информация об устройствах |
| `/api/cache` | Кэшированные данные мониторинга |
| `/api/clients` | Информация о подключённых клиентах |
| `/api/diagnostics` | Диагностическая информация |
| `/api/device/{device_id}/history` | История мониторинга устройства |
| `/users` | Операции, связанные с пользователями |

Перечень отражает известные на момент подготовки архитектуры области существующего API. Фактическое поведение и ограничения доступа необходимо сверить с актуальным исходным кодом.

Дальнейшее развитие API должно предусматривать единообразное именование ресурсов, проверку входных данных, аутентификацию, авторизацию и документированные форматы ответов.

## 8. Архитектура данных

Платформа должна обеспечивать структурированный учёт нескольких категорий данных:

- Сетевые устройства.
- Показатели устройств.
- Исторические записи мониторинга.
- События и оповещения.
- Инфраструктурные ресурсы.
- Сетевые соединения.
- Абоненты и клиентские учётные записи.
- Договоры и услуги.
- Биллинговые записи.
- Заявки в техническую поддержку.
- Пользователи и права доступа.
- Аудиторские записи.

Необходимо разделять технические данные мониторинга и бизнес-финансовые данные.

Изменения критически важных бизнес-данных должны иметь прослеживаемую историю.

Окончательная структура базы данных и используемые технологии хранения будут описаны после аудита исходного кода и базы данных.

## 9. Безопасность и разграничение доступа

Целевая модель безопасности предусматривает:

- Авторизованные пользовательские сессии.
- Разграничение прав по ролям.
- Права инженера и оператора.
- Ограничение доступа к технической диагностике.
- Защищённые административные операции.
- Журналирование действий.
- Безопасное хранение конфигураций.
- Резервное копирование и восстановление.
- Защиту паролей, ключей и инфраструктурных секретов.

Проверка прав доступа должна выполняться на серверной стороне, а не только посредством скрытия элементов интерфейса.

## 10. Интеграции

LoviLink проектируется как самостоятельная платформа.

При необходимости могут использоваться интеграции с:

- Zabbix.
- API сетевого оборудования.
- Сервисами уведомлений.
- Внешними биллинговыми системами.
- Сторонними сервисными платформами.

Интеграции должны использовать документированные интерфейсы и не должны превращать внешние продукты в обязательную зависимость основных функций LoviLink.

## 11. Архитектура развёртывания

Существующий проект имеет основу для развёртывания в Linux-среде.

Целевая модель развёртывания должна поддерживать:

- Серверное приложение.
- Предоставление веб-интерфейса.
- Хранение данных.
- Процессы мониторинга.
- Доставку уведомлений.
- Защищённый внешний доступ.
- Резервное копирование и восстановление.

Параметры промышленного развёртывания, сетевые адреса, учётные данные и конфигурации серверов намеренно не включаются в публичную документацию.

## 12. Дальнейшее развитие архитектуры

Развитие архитектуры будет осуществляться по следующим направлениям:

1. Укрепление существующей основы мониторинга.
2. Разделение логических модулей приложения.
3. Расширение управления инфраструктурой.
4. Внедрение абонентского учёта и биллинга.
5. Внедрение CRM и сервисных процессов.
6. Объединение аналитики и отчётности.
7. Стандартизация API и необязательных интеграций.
8. Повышение безопасности, производительности и готовности к промышленной эксплуатации.

План этапов разработки представлен в документе [ROADMAP.md](ROADMAP.md).

---

**LoviLink by N3M0**  
*Network Operations & Business Management Platform*  
*Платформа управления сетевой инфраструктурой и бизнес-процессами*
