---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 3b52661097ca1feab4c8045be240e4138a0c0f21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190662"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Section spécifique de Microsoft**

Lie un wrapper `_bstr_t` à un `BSTR`.

## <a name="syntax"></a>Syntaxe

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Paramètres

*s*<br/>
`BSTR` à associer ou assigné à la variable `_bstr_t`.

## <a name="remarks"></a>Notes

Si `_bstr_t` a été précédemment attaché à un autre `BSTR`, `_bstr_t` nettoie la ressource `BSTR`, si aucune autre variable `_bstr_t` n'utilise `BSTR`.

## <a name="example"></a>Exemple

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant **Attach**.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
