---
description: 'En savoir plus sur : _bstr_t :: GetBSTR'
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: ced985bb5123d86ff119279fc49a2b4d181ba8b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229299"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Spécifique à Microsoft**

Pointe sur le début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Valeur de retour

Début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetBSTR** affecte tous les `_bstr_t` objets qui partagent un `BSTR` . Plusieurs `_bstr_t` peuvent partager un `BSTR` à l’aide du constructeur de copie et de **Operator =**.

## <a name="example"></a>Exemple

Pour obtenir un exemple à l’aide de **GetBSTR**, consultez [_Bstr_t :: assign](../cpp/bstr-t-assign.md) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
