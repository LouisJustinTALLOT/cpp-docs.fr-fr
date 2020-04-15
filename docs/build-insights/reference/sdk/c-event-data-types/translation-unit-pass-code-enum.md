---
title: TRANSLATION_UNIT_PASS_CODE enum
description: La référence enum de L’ouvrage de construction de la CMD Build Insights TRANSLATION_UNIT_PASS_CODE.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRANSLATION_UNIT_PASS_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b0162d7e53bb7ee7035b94a6b640f6db87cd8b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325292"
---
# <a name="translation_unit_pass_code-enum"></a>TRANSLATION_UNIT_PASS_CODE enum

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

L’enum. `TRANSLATION_UNIT_PASS_CODE`

## <a name="members"></a>Membres

| Nom | Valeur | Description |
|--|--|--|
| `TRANSLATION_UNIT_PASS_CODE_FRONT_END` | 0 (0x000000000) | Le pass front-end, chargé d’analyser le code source et de le convertir en langage intermédiaire. |
| `TRANSLATION_UNIT_PASS_CODE_BACK_END` | 1 (0x00000001) | Le passage back-end, chargé d’optimiser le langage intermédiaire et de le convertir en code machine. |

## <a name="remarks"></a>Notes

Utilisé par les fonctions C SDK.

::: moniker-end
