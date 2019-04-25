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
ms.openlocfilehash: 719852c4556291747b612d54c44d4bf82caa9188
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165929"
---
# <a name="varianttdetach"></a>_variant_t::Detach

**Section spécifique à Microsoft**

Détache encapsulé `VARIANT` objet à partir de ce `_variant_t` objet.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valeur de retour

Encapsulé `VARIANT`.

## <a name="remarks"></a>Notes

Extrait et retourne encapsulé `VARIANT`, puis efface alors cet `_variant_t` objet sans le détruire. Cette fonction membre supprime le `VARIANT` d’encapsulation et définit le `VARTYPE` de ce `_variant_t` objet avec la valeur VT_EMPTY. Il vous incombe de libérer retourné `VARIANT` en appelant le [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) (fonction).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)