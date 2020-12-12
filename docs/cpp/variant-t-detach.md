---
description: 'En savoir plus sur : _variant_t ::D Etach'
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
ms.openlocfilehash: 502903f73f9b149a5f85a6eb1be44687aab20664
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204691"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Spécifique à Microsoft**

Détache l' `VARIANT` objet encapsulé de cet `_variant_t` objet.

## <a name="syntax"></a>Syntaxe

```
VARIANT Detach( );
```

## <a name="return-value"></a>Valeur de retour

Encapsulé `VARIANT` .

## <a name="remarks"></a>Notes

Extrait et retourne l' `VARIANT` objet encapsulé, puis efface cet `_variant_t` objet sans le détruire. Cette fonction membre supprime le de l' `VARIANT` encapsulation et définit le `VARTYPE` de cet `_variant_t` objet à VT_EMPTY. C’est à vous de libérer le retourné `VARIANT` en appelant la fonction [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
