---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154940"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Section spécifique à Microsoft**

Appelle le `AddRef` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
void AddRef( );
```

## <a name="remarks"></a>Notes

Appels `IUnknown::AddRef` sur le pointeur d’interface encapsulé, déclencher un `E_POINTER` erreur si le pointeur est NULL.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)