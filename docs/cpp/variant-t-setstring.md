---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: 0cd300a09c29668c496d93109d1bc862947e948c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187555"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Section spécifique de Microsoft**

Assigne une chaîne à cet objet `_variant_t`.

## <a name="syntax"></a>Syntaxe

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
Pointeur vers la chaîne de caractères.

## <a name="remarks"></a>Notes

Convertit une chaîne de caractères ANSI en chaîne Unicode `BSTR` et l'assigne à cet objet `_variant_t`.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
