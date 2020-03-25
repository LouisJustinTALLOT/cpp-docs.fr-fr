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
ms.openlocfilehash: b0692c9befaa6b7e787ada624dcbb56b074c9f9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160461"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Section spécifique de Microsoft**

Remplace le type de l’objet `_variant_t` par le `VARTYPE`indiqué.

## <a name="syntax"></a>Syntaxe

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Paramètres

*utilisable*<br/>
`VARTYPE` pour cet objet `_variant_t`.

*pSrc*<br/>
Pointeur vers l'objet `_variant_t` à convertir. Si cette valeur est NULL, la conversion s'effectue sur place.

## <a name="remarks"></a>Notes

Cette fonction membre convertit un objet `_variant_t` en `VARTYPE`spécifié. Si *pSrc* a la valeur null, la conversion est effectuée sur place, sinon cet objet `_variant_t` est copié à partir de *pSrc* , puis converti.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)
