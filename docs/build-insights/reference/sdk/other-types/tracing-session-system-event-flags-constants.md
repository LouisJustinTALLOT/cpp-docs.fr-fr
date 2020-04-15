---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS constantes
description: La référence des perspectives de construction de la CMD SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS constantes.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323272"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS constantes

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

Les `TRACING_SESSION_SYSTEM_EVENT_FLAGS` constantes sont utilisées pour décrire les événements système à recueillir lors d’une trace. Utilisez-les pour initialiser le champ `SystemEventFlags` de la structure [TRACING_SESSION_OPTIONS.](tracing-session-options-struct.md)

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Membres

| Nom | Événements activés par ce drapeau |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Ce drapeau est activé par défaut par le SDK Build Insights, même s’il n’est pas précisé explicitement. Il permet aux événements système de base qui sont requis par les aperçus de construction de CMD de fonctionner correctement. Les événements activés par ce drapeau fournissent des informations sur les processus, les threads et le chargement d’images. Vous ne pouvez pas désactiver ces événements. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Échantillons de processeur |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Ce drapeau tourne sur tous les événements du système. |

::: moniker-end
