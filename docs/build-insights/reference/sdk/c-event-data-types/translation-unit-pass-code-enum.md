---
title: Énumération TRANSLATION_UNIT_PASS_CODE
description: Le C++ Kit de développement logiciel (SDK) de Build Insights TRANSLATION_UNIT_PASS_CODE référence Enum.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1219eed98fd01e8c91d8750977e2d8ca4498d649
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333579"
---
# <a name="translation_unit_pass_code-enum"></a>Énumération TRANSLATION_UNIT_PASS_CODE

::: moniker range="<=vs-2015"

Le C++ Kit de développement logiciel (SDK) Build Insights est compatible avec Visual Studio 2017 et versions ultérieures. Pour consulter la documentation de ces versions, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2017 ou Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Énumération `TRANSLATION_UNIT_PASS_CODE`.

## <a name="members"></a>Membres

| Name | Valeur | Description |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x00000000) | L’étape frontale, responsable de l’analyse du code source et de sa conversion en langage intermédiaire. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | L’étape principale, responsable de l’optimisation du langage intermédiaire et de sa conversion en code machine. |

## <a name="remarks"></a>Notes

Utilisé par les fonctions du kit de développement logiciel (SDK) C.

::: moniker-end
