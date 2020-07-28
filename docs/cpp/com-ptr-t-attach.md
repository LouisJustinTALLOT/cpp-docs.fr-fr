---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: cb5950e311711dd489b3cab223714b1840773f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220585"
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

- **Attacher (**  *pInterface*  **)** `AddRef` n’est pas appelé. La propriété de l'interface est passée à cet objet `_com_ptr_t`. `Release`est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

- **Attach (**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* a la valeur **`true`** , `AddRef` est appelé pour incrémenter le décompte de références pour le pointeur d’interface encapsulé. Si *fAddRef* est **`false`** , cet `_com_ptr_t` objet prend la propriété du pointeur d’interface brut sans appeler `AddRef` . `Release`est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
