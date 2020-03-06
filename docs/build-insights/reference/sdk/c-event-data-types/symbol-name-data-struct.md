---
title: Structure SYMBOL_NAME_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights SYMBOL_NAME_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333635"
---
# <a name="symbol_name_data-structure"></a>Structure SYMBOL_NAME_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `SYMBOL_NAME_DATA` décrit un symbole frontal du compilateur.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Key` | Clé du symbole. Cette valeur est unique au sein de la trace en cours d’analyse. |
| `Name` | Nom du symbole. |

## <a name="remarks"></a>Notes

Les symboles provenant de deux passes front-end de compilateur différents peuvent avoir le même nom mais une clé différente. Dans ce cas, utilisez des noms de symboles pour déterminer si deux types sont identiques.

::: moniker-end
