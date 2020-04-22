---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745072"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft Spécifique**

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
Si c’est `AddRef` VRAI, alors est appelé. Si c’est `_com_ptr_t` FALSE, l’objet prend possession `AddRef`du pointeur d’interface brute sans appeler .

## <a name="remarks"></a>Notes

- **Attacher (**  *pInterface*  **)** `AddRef` n’est pas appelé. La propriété de l'interface est passée à cet objet `_com_ptr_t`. `Release`est appelé à décrémenter le nombre de références pour le pointeur précédemment encapsulé.

- **Attacher(**  *pInterface* **,**  *fAddRef*  **)** Si *fAddRef* est `AddRef` VRAI, est appelé à incrémenter le nombre de références pour le pointeur d’interface encapsulé. Si *fAddRef* est `_com_ptr_t` FALSE, cet objet prend possession `AddRef`du pointeur d’interface brute sans appeler . `Release`est appelé à décrémenter le nombre de références pour le pointeur précédemment encapsulé.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
