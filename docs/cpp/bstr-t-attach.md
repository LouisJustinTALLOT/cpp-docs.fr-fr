---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604436"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Section spécifique à Microsoft**

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

Consultez [_bstr_t::Assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant **attacher**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)