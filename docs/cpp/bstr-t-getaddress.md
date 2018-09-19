---
title: _bstr_t::GetAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b3aa001270a3dc608fabf73fce28ce51eb9295e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031299"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Section spécifique à Microsoft**

Libère toute chaîne existante et retourne l'adresse d'une chaîne nouvellement allouée.

## <a name="syntax"></a>Syntaxe

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Valeur de retour

Pointeur désignant le `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetAddress** affecte tous les `_bstr_t` objets qui partagent un `BSTR`. Plusieurs `_bstr_t` peuvent partager un `BSTR` en utilisant le constructeur de copie et **opérateur =**.

## <a name="example"></a>Exemple

Consultez [_bstr_t::Assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant **GetAddress**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)