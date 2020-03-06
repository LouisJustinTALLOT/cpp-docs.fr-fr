---
title: Structure CL_PASS_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights CL_PASS_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333824"
---
# <a name="cl_pass_data-structure"></a>Structure CL_PASS_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `CL_PASS_DATA` décrit une réussite de compilation.

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

|  |  |
|--|--|
| `TranslationUnitPassCode` | Code identifiant la passe de compilation en cours d’exécution. Pour plus d’informations, consultez [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | Fichier C ou C++ source sur lequel cette étape de compilation est exécutée. |
| `OutputObjectPath` | Fichier objet qui est produit par le compilateur. |

::: moniker-end
