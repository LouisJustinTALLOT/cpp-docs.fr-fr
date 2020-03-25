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
ms.openlocfilehash: 9737db6b77483fa55e1dad90b9464752cd8537a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187737"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Section spécifique de Microsoft**

Détache l’objet `VARIANT` encapsulé de cet objet `_variant_t`.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valeur de retour

`VARIANT`encapsulé.

## <a name="remarks"></a>Notes

Extrait et retourne le `VARIANT`encapsulé, puis efface ce `_variant_t` objet sans le détruire. Cette fonction membre supprime le `VARIANT` de l’encapsulation et définit la `VARTYPE` de cet objet `_variant_t` sur VT_EMPTY. Il vous revient de libérer la `VARIANT` retournée en appelant la fonction [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
