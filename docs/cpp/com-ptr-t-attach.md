---
description: 'En savoir plus sur : _com_ptr_t :: Attach'
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 5b27a4bd6572f2f1429766328c01f377672ee11d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295651"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Spécifique à Microsoft**

Encapsule un pointeur d'interface brut du type de ce pointeur intelligent.

## <a name="syntax"></a>Syntaxe

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Paramètres

*pInterface*<br/>
Pointeur d'interface brut.

*fAddRef*<br/>
Si c’est le cas **`true`** , `AddRef` est appelé. Si c’est **`false`** le cas, l' `_com_ptr_t` objet prend la propriété du pointeur d’interface brut sans appeler `AddRef` .

## <a name="remarks"></a>Notes

- **Attacher (**  *pInterface*  **)** `AddRef` n’est pas appelé. La propriété de l'interface est passée à cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

- **Attach (**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* a la valeur **`true`** , `AddRef` est appelé pour incrémenter le décompte de références pour le pointeur d’interface encapsulé. Si *fAddRef* est **`false`** , cet `_com_ptr_t` objet prend la propriété du pointeur d’interface brut sans appeler `AddRef` . `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
