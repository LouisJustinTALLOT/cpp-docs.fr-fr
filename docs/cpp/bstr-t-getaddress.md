---
description: 'En savoir plus sur : _bstr_t :: GetAddress'
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: afb877a6f1b4cfcfb6fe08b36168af745d733b85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229312"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Spécifique à Microsoft**

Libère toute chaîne existante et retourne l'adresse d'une chaîne nouvellement allouée.

## <a name="syntax"></a>Syntaxe

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Valeur de retour

Pointeur désignant le `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetAddress** affecte tous les `_bstr_t` objets qui partagent un `BSTR` . Plusieurs `_bstr_t` peuvent partager un `BSTR` à l’aide du constructeur de copie et de **Operator =**.

## <a name="example"></a>Exemple

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple à l’aide de **GetAddress**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
