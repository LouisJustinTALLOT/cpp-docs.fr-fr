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
ms.openlocfilehash: 0c23ba7ba476b44b44f48b76119776e2f2cb188e
ms.sourcegitcommit: 04d327940787df1297b72d534f388a035d472af0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39181144"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable\* \* opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Notes

Effectue un cast en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) données membres à un pointeur-à-un-pointeur-à l’interface IInspectable.

Une erreur est générée si le ComPtrRefBase actuel n’est pas dérivé d’IInspectable.

Ce cast est disponible uniquement si **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** est défini.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRefBase (classe)](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
