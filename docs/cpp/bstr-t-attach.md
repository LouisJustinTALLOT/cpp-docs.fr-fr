---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749703"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Microsoft Spécifique**

Lie un wrapper `_bstr_t` à un `BSTR`.

## <a name="syntax"></a>Syntaxe

```cpp
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

Voir [_bstr_t::Assigner](../cpp/bstr-t-assign.md) par exemple en utilisant **Attach**.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[_bstr_t, classe](../cpp/bstr-t-class.md)
