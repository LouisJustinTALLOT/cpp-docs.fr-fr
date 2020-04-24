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
ms.openlocfilehash: c2283158856a6781ab2e12c51f4e2ad0e4f1d531
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750729"
---
# <a name="_variant_tchangetype"></a>_variant_t::ChangeType

**Microsoft Spécifique**

Modifications du `_variant_t` type de `VARTYPE`l’objet à l’indiqué .

## <a name="syntax"></a>Syntaxe

```cpp
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>Paramètres

*vartype*<br/>
Le `VARTYPE` pour `_variant_t` cet objet.

*pSrc (en)*<br/>
Pointeur vers l'objet `_variant_t` à convertir. Si cette valeur est NULL, la conversion s'effectue sur place.

## <a name="remarks"></a>Notes

Cette fonction de `_variant_t` membre convertit `VARTYPE`un objet en indiqué . Si *pSrc* est NULL, la conversion est `_variant_t` effectuée en place, sinon cet objet est copié à partir de *pSrc,* puis converti.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Classe _variant_t](../cpp/variant-t-class.md)
