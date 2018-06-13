---
title: ComPtrRefBase::operator IInspectable **, opérateur | Documents Microsoft
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
ms.openlocfilehash: e337f6bbc92718c839fc2bd12c9df9f0caa5d5aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883457"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable**, opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Notes

Convertit en cours [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données pour un pointeur à une-pointeur-à l’interface IInspectable.

Une erreur est générée si le ComPtrRefBase actuelle ne dérive pas de IInspectable.

Ce cast est disponible uniquement si **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** est défini.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRefBase (classe)](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)