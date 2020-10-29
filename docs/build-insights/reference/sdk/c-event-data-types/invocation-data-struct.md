---
title: Structure INVOCATION_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights INVOCATION_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 98ac234b702ef2c73a5c8d90ee6bf4dc59349ed6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920968"
---
# <a name="invocation_data-structure"></a>Structure INVOCATION_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `INVOCATION_DATA` structure décrit un appel du compilateur ou de l’éditeur de liens.

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

| Nom | Description |
|--|--|
| `MSVCToolCode` | Code qui identifie le type de l’appel. Pour plus d’informations, consultez [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objet qui stocke la version de l’outil appelé sous la forme d’un groupe de valeurs intégrales. |
| `ToolVersionString` | Décrit la version sous forme de texte de l’outil appelé. |
| `WorkingDirectory` | Répertoire à partir duquel l’appel a été effectué. |
| `ToolPath` | Chemin d’accès absolu de l’outil appelé. |

::: moniker-end
