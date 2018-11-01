---
title: _variant_t, opérateurs relationnels
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: e0d26247868440f47c73422510ac0e998f8e8dee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431647"
---
# <a name="variantt-relational-operators"></a>_variant_t, opérateurs relationnels

**Section spécifique à Microsoft**

Comparez deux objets `_variant_t` pour déterminer leur égalité ou inégalité.

## <a name="syntax"></a>Syntaxe

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Un `VARIANT` à comparer avec la `_variant_t` objet.

*pSrc*<br/>
Pointeur vers le `VARIANT` à comparer avec la `_variant_t` objet.

## <a name="return-value"></a>Valeur de retour

Retourne **true** si la comparaison est vérifiée, **false** si ce n’est pas le cas.

## <a name="remarks"></a>Notes

Compare un `_variant_t` de l’objet avec un `VARIANT`, afin de tester l’égalité ou d’inégalité.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_variant_t, classe](../cpp/variant-t-class.md)