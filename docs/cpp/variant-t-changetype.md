---
description: 'En savoir plus sur : _variant_t :: ChangeType'
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
ms.openlocfilehash: 32ce43f1d9afb388c97e5271927113c71d31bb92
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116624"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Spécifique à Microsoft**

Remplace le type de l' `_variant_t` objet par le indiqué `VARTYPE` .

## <a name="syntax"></a>Syntaxe

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Paramètres

*utilisable*<br/>
`VARTYPE`Pour cet `_variant_t` objet.

*pSrc*<br/>
Pointeur vers l'objet `_variant_t` à convertir. Si cette valeur est NULL, la conversion s'effectue sur place.

## <a name="remarks"></a>Notes

Cette fonction membre convertit un `_variant_t` objet en le indiqué `VARTYPE` . Si *pSrc* a la valeur null, la conversion est effectuée sur place, sinon cet `_variant_t` objet est copié à partir de *pSrc* , puis converti.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
