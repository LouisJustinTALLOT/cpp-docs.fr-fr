---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181211"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Section spécifique de Microsoft**

Pointe sur le début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="syntax"></a>Syntaxe

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Valeur de retour

Début du `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetBSTR** affecte tous les objets `_bstr_t` qui partagent un `BSTR`. Plusieurs `_bstr_t` peuvent partager un `BSTR` par le biais de l’utilisation du constructeur de copie et de **Operator =** .

## <a name="example"></a>Exemple

Pour obtenir un exemple à l’aide de **GetBSTR**, consultez [_Bstr_t :: assign](../cpp/bstr-t-assign.md) .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
