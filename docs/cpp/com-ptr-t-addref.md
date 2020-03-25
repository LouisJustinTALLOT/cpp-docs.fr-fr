---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189925"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Section spécifique de Microsoft**

Appelle la fonction membre `AddRef` de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
void AddRef( );
```

## <a name="remarks"></a>Notes

Appelle `IUnknown::AddRef` sur le pointeur d’interface encapsulé, en déclenchant une erreur de `E_POINTER` si le pointeur est NULL.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
