---
title: Structure INVOCATION_VERSION_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights INVOCATION_VERSION_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333677"
---
# <a name="invocation_version_data-structure"></a>Structure INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `INVOCATION_VERSION_DATA` décrit un numéro de version sous la forme d’un groupe de valeurs intégrales.

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
| `VersionMajor` | Numéro principal de la version. |
| `VersionMinor` | Numéro secondaire de la version. |
| `BuildNumberMajor` | Numéro principal de la Build. |
| `BuildNumberMinor` | Numéro secondaire de la Build. |

::: moniker-end
