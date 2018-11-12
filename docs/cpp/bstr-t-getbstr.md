---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618047"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR

**Section spécifique à Microsoft**

Pointe sur le début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Valeur de retour

Début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetBSTR** affecte tous les `_bstr_t` objets qui partagent un `BSTR`. Plusieurs `_bstr_t` peuvent partager un `BSTR` en utilisant le constructeur de copie et **opérateur =**.

## <a name="example"></a>Exemple

Consultez [_bstr_t::Assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant **GetBSTR**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)