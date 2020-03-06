---
title: Structure INVOCATION_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights INVOCATION_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333691"
---
# <a name="invocation_data-structure"></a>Structure INVOCATION_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `INVOCATION_DATA` décrit un appel du compilateur ou de l’éditeur de liens.

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
| `MSVCToolCode` | Code qui identifie le type de l’appel. Pour plus d’informations, consultez [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objet qui stocke la version de l’outil appelé sous la forme d’un groupe de valeurs intégrales. |
| `ToolVersionString` | Décrit la version sous forme de texte de l’outil appelé. |
| `WorkingDirectory` | Répertoire à partir duquel l’appel a été effectué. |
| `ToolPath` | Chemin d’accès absolu de l’outil appelé. |

::: moniker-end
