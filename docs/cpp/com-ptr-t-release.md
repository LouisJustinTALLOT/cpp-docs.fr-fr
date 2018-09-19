---
title: _com_ptr_t::Release | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444f56c1a999f09a79d725173c9f0f19399ab363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118360"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Section spécifique à Microsoft**

Appelle le **version** fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.

## <a name="syntax"></a>Syntaxe

```
void Release( );
```

## <a name="remarks"></a>Notes

Appels `IUnknown::Release` sur le pointeur d’interface encapsulé, déclencher un `E_POINTER` erreur si ce pointeur d’interface est NULL.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)