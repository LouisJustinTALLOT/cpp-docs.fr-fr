---
title: Structure CL_PASS_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights CL_PASS_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 24e524b802a124f38043f3b69afed7f1aa9cd156
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923645"
---
# <a name="cl_pass_data-structure"></a>Structure CL_PASS_DATA

::: moniker range="<=msvc-140"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=msvc-150"

La `CL_PASS_DATA` structure décrit une réussite de compilation.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `TranslationUnitPassCode` | Code identifiant la passe de compilation en cours d’exécution. Pour plus d’informations, consultez [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Fichier source C ou C++ sur lequel cette étape de compilation est exécutée. |
| `OutputObjectPath` | Fichier objet qui est produit par le compilateur. |

::: moniker-end
