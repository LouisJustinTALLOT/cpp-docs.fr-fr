---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181250"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Section spécifique de Microsoft**

Libère toute chaîne existante et retourne l'adresse d'une chaîne nouvellement allouée.

## <a name="syntax"></a>Syntaxe

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Valeur de retour

Pointeur désignant le `BSTR` encapsulé par l'objet `_bstr_t`.

## <a name="remarks"></a>Notes

**GetAddress** affecte tous les objets `_bstr_t` qui partagent un `BSTR`. Plusieurs `_bstr_t` peuvent partager un `BSTR` par le biais de l’utilisation du constructeur de copie et de **Operator =** .

## <a name="example"></a>Exemple

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple à l’aide de **GetAddress**.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
