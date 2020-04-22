---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 4dcf643357c9b368d4b2ea3bc51e6567acf45a44
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745091"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Microsoft Spécifique**

Appelle `AddRef` la fonction `IUnknown` de membre sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```cpp
void AddRef( );
```

## <a name="remarks"></a>Notes

Appels `IUnknown::AddRef` sur le pointeur d’interface `E_POINTER` encapsulé, soulevant une erreur si le pointeur est NULL.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
