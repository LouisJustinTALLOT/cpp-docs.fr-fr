---
title: _variant_t, opérateurs relationnels | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95cb1ac663607f26c4f168c2e98910f5b41963c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040146"
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