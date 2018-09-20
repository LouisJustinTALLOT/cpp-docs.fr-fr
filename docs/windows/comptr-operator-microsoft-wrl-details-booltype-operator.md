---
title: ComPtr::operator Microsoft::WRL::Details::BoolType opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05e26296646b61997baff880a671958769eb099b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433398"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur

Indique ou non un **ComPtr** gère la durée de vie d’une interface.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

## <a name="return-value"></a>Valeur de retour

Si une interface est associée à ce **ComPtr**, l’adresse de la [BoolStruct::Member](../windows/boolstruct-member-data-member.md) membre de données ; sinon, **nullptr**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ComPtr, classe](../windows/comptr-class.md)<br/>
[ComPtr::Get, méthode](../windows/comptr-get-method.md)