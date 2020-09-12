---
title: Structure FILE_DATA
description: Le kit de développement logiciel (SDK) C++ Build Insights FILE_DATA référence de la structure.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5f793df0340005665a8f4ab42e9793f51f3aa0c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041807"
---
# <a name="file_data-structure"></a>Structure FILE_DATA

::: moniker range="<=vs-2015"

Le kit de développement logiciel (SDK) C++ Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2017 ou visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `FILE_DATA` structure décrit une entrée ou une sortie de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Membres

| Nom | Description |
|--|--|
| `Path` | Chemin d’accès absolu du fichier |
| `TypeCode` | Code décrivant le type du fichier. Pour plus d’informations, consultez [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
