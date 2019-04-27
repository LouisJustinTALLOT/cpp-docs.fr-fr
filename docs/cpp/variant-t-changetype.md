---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 319c4fde808932e86021ee59b051261c43ca2edd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166202"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Section spécifique à Microsoft**

Change le type de la `_variant_t` objet au `VARTYPE`.

## <a name="syntax"></a>Syntaxe

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Paramètres

*vartype*<br/>
Le `VARTYPE` pour ce `_variant_t` objet.

*pSrc*<br/>
Pointeur vers l'objet `_variant_t` à convertir. Si cette valeur est NULL, la conversion est effectuée en place.

## <a name="remarks"></a>Notes

Cette fonction membre convertit un `_variant_t` objet dans le texte indiqué `VARTYPE`. Si *pSrc* est NULL, la conversion s’effectue sur place, sinon cela `_variant_t` objet est copié à partir de *pSrc* , puis sont converties.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)