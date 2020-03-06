---
title: Énumération FILE_TYPE_CODE
description: Le C++ Kit de développement logiciel (SDK) de Build Insights FILE_TYPE_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333719"
---
# <a name="file_type_code-enum"></a>Énumération FILE_TYPE_CODE

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

L’énumération `FILE_TYPE_CODE` décrit le type d’un fichier.

## <a name="members"></a>Membres

| Name | Valeur | Description |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | Type de fichier non listé dans cet Enum. |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | Fichier objet (\*. obj). |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | Fichier exécutable (\*. exe) ou DLL (\*. dll). |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | Fichier de bibliothèque statique (*. lib). |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | Une bibliothèque d’importation (*. lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | Fichier d’exportation (*. exp). |

## <a name="remarks"></a>Notes

::: moniker-end
