---
title: Structure FILE_DATA
description: Référence C++ de la structure du kit de développement logiciel (SDK) de Build Insights FILE_DATA.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333754"
---
# <a name="file_data-structure"></a>Structure FILE_DATA

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

La structure `FILE_DATA` décrit une entrée ou une sortie de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>Membres

|  |  |
|--|--|
| `Path` | Chemin d’accès absolu du fichier |
| `TypeCode` | Code décrivant le type du fichier. Pour plus d’informations, consultez [FILE_TYPE_CODE](file-type-code-enum.md). |

::: moniker-end
