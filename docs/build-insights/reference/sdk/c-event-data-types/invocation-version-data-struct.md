---
title: Structure INVOCATION_VERSION_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights INVOCATION_VERSION_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec54c560dd408dc3beecbc20eaac69d389c7ec37
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041557"
---
# <a name="invocation_version_data-structure"></a>Structure INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_VERSION_DATA` structure décrit un numéro de version sous la forme d’un groupe de valeurs intégrales.

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

| Nom | Description |
|--|--|
| `VersionMajor` | Numéro principal de la version. |
| `VersionMinor` | Numéro secondaire de la version. |
| `BuildNumberMajor` | Numéro principal de la Build. |
| `BuildNumberMinor` | Numéro secondaire de la Build. |

::: moniker-end
