---
description: 'En savoir plus sur : _variant_t :: SetString'
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: a36bab9189b6046325bb275469dc9dbdb495fc7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161414"
---
# <a name="_variant_tsetstring"></a>_variant_t::SetString

**Spécifique à Microsoft**

Assigne une chaîne à cet objet `_variant_t`.

## <a name="syntax"></a>Syntaxe

```cpp
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Paramètres

*pSrc*<br/>
Pointeur vers la chaîne de caractères.

## <a name="remarks"></a>Notes

Convertit une chaîne de caractères ANSI en chaîne Unicode `BSTR` et l'assigne à cet objet `_variant_t`.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
