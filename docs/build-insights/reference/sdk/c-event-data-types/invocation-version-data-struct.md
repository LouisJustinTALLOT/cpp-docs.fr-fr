---
title: structure INVOCATION_VERSION_DATA
description: La référence de structure de construction SDK INVOCATION_VERSION_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325473"
---
# <a name="invocation_version_data-structure"></a>structure INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_VERSION_DATA` structure décrit un numéro de version comme un groupe de valeurs intégrales.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `VersionMajor` | Le numéro principal de la version. |
| `VersionMinor` | Le numéro mineur de la version. |
| `BuildNumberMajor` | Le nombre principal de la construction. |
| `BuildNumberMinor` | Le petit numéro de la construction. |

::: moniker-end
