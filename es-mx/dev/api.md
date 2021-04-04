---
title: API
description: Accede a recursos y realiza acciones mediante la API de PreMiD
published: true
date: 2021-02-01T12:36:44.713Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:59.010Z
---

# API

> URL base: https://api.premid.app 
> 
> {.is-info}

## Administración de versiones de la API
> La v2 de la API está descontinuada y va a ser eliminada en un futuro cercano. Por favor, usa la v3 para cualquier solicitud futura para prevenir problemas. Please use v3 for any future request to prevent issues. 
> 
> {.is-danger}

PreMiD exposes different versions of our API. You can specify version by including it in the request path like `https://api.premid.app/v{version_number}`. Omitting the version number from the route will route requests to the current default version (marked below accordingly).

## Encryption

All HTTP-layer services and protocols (e.g. http) within the PreMiD API use TLS 1.2.

# Documentación
> Currently under construction! 
> 
> {.is-danger}

**Choose the API version:**
- [v2 *deprecated*](/dev/api/v2)
- [v3 *active*](/dev/api/v3)
{.links-list}