---
title: ComPtrRefBase::operator IInspectable **, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19e04f5415f9f7a736371c888dff7559df6c6c66
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462334"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable\* \* opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Notes

Effectue un cast en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) données membres à un pointeur-à-un-pointeur-to la `IInspectable` interface.

Une erreur est générée si actuel **ComPtrRefBase** ne dérive pas de `IInspectable`.

Ce cast est disponible uniquement si **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** est défini.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi
[ComPtrRefBase (classe)](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)