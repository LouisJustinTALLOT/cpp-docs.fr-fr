---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393894"
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