# LoviLink — Project Status
**Project:** LoviLink by N3M0  
**Version:** 2.0 — Development  
**Document status:** Preliminary  
**Last updated:** November 21, 2026

---

# English

## 1. Overview

LoviLink is under active planning and development as an independent Network Operations & Business Management platform.

The current project is based on an existing NetWatch2 application. The long-term objective is to evolve this foundation into a modular platform combining network monitoring, infrastructure management, subscriber and billing management, service desk workflows, and analytics.

This document distinguishes existing functionality from verified functionality and future plans.

**Important:** This is a preliminary status based on currently available project information. The implementation status will be updated following a detailed source-code, database, API, security, and operational audit.

## 2. Existing Implementation

The following components are part of the existing project foundation. Their complete implementation and operational reliability have not yet been independently audited.

- Python-based backend using FastAPI.
- Background polling and monitoring processes.
- Network equipment collectors.
- Cached monitoring data.
- Device information and monitoring API endpoints.
- Client information retrieval.
- Device diagnostics functionality.
- Monitoring history endpoints.
- Event and alert handling.
- ntfy notification integration.
- Web-based monitoring dashboard.

These components form the starting point for LoviLink development.

## 3. Verification Pending

The following areas require systematic technical verification:

- API functionality and consistency.
- Device collector reliability across supported models and firmware versions.
- Monitoring data accuracy and history retention.
- Database structure and persistence.
- Authentication, authorization, and role separation.
- Error handling and recovery mechanisms.
- Security configuration and exposure of network services.
- Backup and restoration procedures.
- Performance under sustained monitoring load.
- Installation, upgrade, and maintenance procedures.

No production-readiness claim is made until these areas have been evaluated.

## 4. Current Development

Current work is focused on project organization and technical preparation:

- Public project documentation.
- Product vision and development roadmap.
- Target architecture definition.
- Project status documentation.
- Repository organization.
- Intellectual property and licensing preparation.
- Planning of the transition from NetWatch2 to LoviLink 2.0.

## 5. Planned Capabilities

The following capabilities are part of the target product direction. They must not be interpreted as already implemented.

### NMS — Network Management System
- Advanced monitoring and metrics.
- Configurable triggers and alert rules.
- SLA monitoring.
- Network discovery.
- Historical analysis and dashboards.

### OSS — Operations Support System
- Network topology management.
- Infrastructure inventory.
- IP address management.
- Equipment and resource management.
- Maintenance workflows.

### BSS — Business Support System
- Subscriber management.
- Contracts and service plans.
- Personal accounts.
- Billing and payment records.
- Financial reporting.

### CRM & Service Desk
- Customer requests.
- Incidents and service tickets.
- Work assignment and tracking.
- Customer service history.

### Analytics & Integrations
- Operational and business analytics.
- Automated workflows.
- External API integrations.
- Optional integration with Zabbix and other systems.

## 6. Verification Status

| Status | Meaning |
|---|---|
| Implemented | Functionality exists in the current codebase; detailed verification may still be pending. |
| Verified | Functionality has passed defined tests. |
| In Progress | Work is actively underway. |
| Planned | Included in the product roadmap but not confirmed as implemented. |
| Pending Audit | Requires inspection or testing before its status can be confirmed. |

A feature must not be marked as Verified without supporting test results or other reliable evidence.

## 7. Repository and Intellectual Property

The public GitHub repository is intended for project documentation, architecture descriptions, roadmap information, and public development updates.

The proprietary production source code, credentials, private configurations, and sensitive infrastructure information are intentionally excluded.

LoviLink is being developed as an independently owned software project. Licensing and distribution terms are being prepared separately.

## 8. Current Project Stage

**Current stage:** Audit and Planning  
**Documentation stage:** In Progress  
**Architecture definition:** Published  
**Project status documentation:** In Progress  
**Full technical audit:** Pending  
**Production readiness:** Not established

---

# Русская версия

## 1. Обзор проекта

LoviLink находится на стадии планирования и развития как самостоятельная платформа Network Operations & Business Management.

Текущая основа проекта — существующее приложение NetWatch2. Долгосрочная цель — развить его в модульную платформу, объединяющую мониторинг сетей, управление инфраструктурой, абонентами и биллингом, обслуживание клиентов и аналитику.

Этот документ разделяет существующие компоненты, проверенный функционал и будущие возможности.

**Важно:** документ отражает предварительное состояние проекта на основании доступной информации. Статусы будут уточняться после полного аудита исходного кода, базы данных, API, безопасности и эксплуатационных процессов.

## 2. Существующая реализация

Следующие компоненты относятся к существующей технической основе проекта. Полнота их реализации и эксплуатационная надёжность ещё требуют комплексного аудита.

- Backend на Python с использованием FastAPI.
- Фоновые процессы опроса и мониторинга.
- Коллекторы сетевого оборудования.
- Кэширование мониторинговых данных.
- API для получения информации об устройствах.
- Получение информации о клиентах подключённого оборудования.
- Функциональность диагностики устройств.
- API получения истории мониторинга.
- Обработка событий и уведомлений.
- Интеграция уведомлений через ntfy.
- Веб-интерфейс мониторинга.

Эти компоненты являются отправной точкой дальнейшего развития LoviLink.

## 3. Требует проверки

Следующие направления необходимо проверить в рамках технического аудита:

- Корректность и полнота работы API.
- Надёжность коллекторов на поддерживаемых моделях и версиях прошивок.
- Точность мониторинговых данных и хранение истории.
- Структура базы данных и сохранность информации.
- Аутентификация, авторизация и разделение ролей.
- Обработка ошибок и восстановление после сбоев.
- Безопасность конфигурации и сетевых сервисов.
- Резервное копирование и восстановление.
- Производительность при длительной работе и увеличении количества устройств.
- Установка, обновление и техническое обслуживание.

До завершения этих проверок проект не объявляется готовым к промышленной эксплуатации.

## 4. Текущая разработка

В настоящее время работа сосредоточена на организации проекта и технической подготовке:

- Публичная документация проекта.
- Формирование концепции и дорожной карты.
- Определение целевой архитектуры.
- Документирование текущего состояния.
- Организация репозитория.
- Подготовка документов об интеллектуальных правах и лицензировании.
- Планирование перехода от NetWatch2 к LoviLink 2.0.

## 5. Планируемые возможности

Следующие возможности входят в целевую концепцию продукта. Их наличие в этом документе не означает, что они уже реализованы.

### NMS — система управления сетью
- Расширенный мониторинг и сбор метрик.
- Настраиваемые триггеры и правила оповещения.
- Контроль SLA.
- Автоматическое обнаружение сети.
- Историческая аналитика и панели мониторинга.

### OSS — управление инфраструктурой
- Управление сетевой топологией.
- Инвентаризация инфраструктуры.
- Управление IP-адресами.
- Учёт оборудования и ресурсов.
- Процессы технического обслуживания.

### BSS — управление бизнес-процессами
- Управление абонентами.
- Договоры и тарифные планы.
- Лицевые счета.
- Начисления и платежи.
- Финансовая отчётность.

### CRM и Service Desk
- Обращения клиентов.
- Инциденты и заявки.
- Назначение и контроль выполнения задач.
- История обслуживания клиентов.

### Аналитика и интеграции
- Техническая и бизнес-аналитика.
- Автоматизация процессов.
- Интеграция через внешние API.
- Необязательное взаимодействие с Zabbix и другими системами.

## 6. Статусы функциональности

| Статус | Значение |
|---|---|
| Implemented — Реализовано | Функциональность присутствует в текущем коде; полноценная проверка ещё может требоваться. |
| Verified — Проверено | Функциональность прошла определённые испытания. |
| In Progress — В разработке | Работа над функциональностью продолжается. |
| Planned — Запланировано | Возможность включена в дорожную карту, но её реализация не подтверждена. |
| Pending Audit — Ожидает аудита | Требуется проверка исходного кода или испытания. |

Функциональность нельзя обозначать как проверенную без результатов испытаний или других достоверных подтверждений.

## 7. Репозиторий и интеллектуальная собственность

Публичный репозиторий GitHub предназначен для размещения документации, описания архитектуры, дорожной карты и открытых сведений о развитии проекта.

Закрытый производственный исходный код, учётные данные, приватные конфигурации и чувствительная информация об инфраструктуре в публичный репозиторий не включаются.

LoviLink развивается как самостоятельный программный проект с индивидуальным правообладателем. Условия лицензирования и распространения готовятся отдельно.

## 8. Текущий этап проекта

**Текущий этап:** Аудит и планирование.  
**Документация:** В разработке.  
**Описание архитектуры:** Опубликовано.  
**Документ о состоянии проекта:** Подготавливается.  
**Полный технический аудит:** Не проведён.  
**Готовность к промышленной эксплуатации:** Не подтверждена.

---

**LoviLink by N3M0**  
*Independent Network Operations & Business Management Platform*
