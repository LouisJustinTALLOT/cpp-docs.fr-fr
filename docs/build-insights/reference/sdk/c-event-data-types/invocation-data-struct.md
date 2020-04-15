---
title: structure INVOCATION_DATA
description: La référence de structure de construction SDK INVOCATION_DATA de CMD Build Insights.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325486"
---
# <a name="invocation_data-structure"></a>structure INVOCATION_DATA

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `INVOCATION_DATA` structure décrit une invocation compilateur ou linker.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `MSVCToolCode` | Un code qui identifie le type d’invocation. Pour plus d’informations, voir [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Un objet qui stocke la version de l’outil invoqué comme un groupe de valeurs intégrales. |
| `ToolVersionString` | Décrit la version de l’outil invoqué sous forme de texte. |
| `WorkingDirectory` | Le répertoire à partir duquel l’invocation a été faite. |
| `ToolPath` | Le chemin absolu de l’outil invoqué. |

::: moniker-end
