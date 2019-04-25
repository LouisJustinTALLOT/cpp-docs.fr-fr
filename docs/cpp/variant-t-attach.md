---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166216"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Section spécifique à Microsoft**

Attache un `VARIANT` de l’objet dans le **_variant_t** objet.

## <a name="syntax"></a>Syntaxe

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Un `VARIANT` objet à attacher à cet **_variant_t** objet.

## <a name="remarks"></a>Notes

Prend possession de la `VARIANT` en l’encapsulant. Cette fonction membre libère tout encapsulé existant `VARIANT`, puis copie fourni `VARIANT`et définit sa `VARTYPE` avec la valeur VT_EMPTY s’assurer que ses ressources peuvent uniquement être libérées par le **_variant_t** destructeur.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)