---
title: _com_ptr_t::AddRef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b66f4944d9ccdfb36587817c5f856c127513784e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087699"
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