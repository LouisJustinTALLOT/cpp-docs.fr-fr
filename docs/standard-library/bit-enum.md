---
title: endian enum
description: Énumération utilisée pour spécifier le endianness des types scalaires
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: b535bc009fbdc0b047444a6bc2ca36eed7a6d1cb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040078"
---
# <a name="endian-enum"></a>endian enum

Indique le endianness de tous les types scalaires.

## <a name="syntax"></a>Syntaxe

```cpp
enum class endian {
    little = 0,
    big = 1,
    native = little
 };
```

### <a name="members"></a>Membres

|Élément|Description|
|-|-|
| `little` | Indique que les types scalaires sont Little-endian. Autrement dit, l’octet le moins significatif est stocké dans la plus petite adresse. Par exemple, `0x1234` est stocké `0x34` `0x12` .  |
| `big` | Indique que les types scalaires sont de poids fort (Big-endian), autrement dit, l’octet le plus significatif est stocké dans la plus petite adresse. Par exemple, `0x1234` est stocké `0x12` `0x34` .  |

## <a name="remarks"></a>Remarques

Tous les types scalaires natifs sont Little endian pour les plateformes qui Microsoft Visual C++ cibles (x86, x64, ARM, ARM64).

## <a name="requirements"></a>Configuration requise

**En-tête :**\<bit>

**Espace de noms :** std

[/std : c + + latest](../build/reference/std-specify-language-standard-version.md) est requis.

## <a name="see-also"></a>Voir aussi

[\<bit>](../standard-library/bit.md)  
