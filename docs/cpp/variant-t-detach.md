---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500557"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Section spécifique à Microsoft**

Détache l' `VARIANT` objet encapsulé de cet `_variant_t` objet.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valeur de retour

Encapsulé `VARIANT`.

## <a name="remarks"></a>Notes

Extrait et retourne l’objet encapsulé `VARIANT`, puis efface cet `_variant_t` objet sans le détruire. Cette fonction membre supprime le `VARIANT` de l’encapsulation et définit `VARTYPE` le de `_variant_t` cet objet avec la valeur VT_EMPTY. C’est à vous de libérer le retourné `VARIANT` en appelant la fonction [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)