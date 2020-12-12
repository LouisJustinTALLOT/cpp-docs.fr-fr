---
description: 'En savoir plus sur : _bstr_t :: Attach'
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: b3f29c8eaf81a492f7e3c4282227d3d6d246988e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229429"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Spécifique à Microsoft**

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

Consultez [_bstr_t :: assign](../cpp/bstr-t-assign.md) pour obtenir un exemple utilisant **Attach**.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _bstr_t](../cpp/bstr-t-class.md)
