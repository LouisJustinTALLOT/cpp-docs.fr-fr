---
title: ImplementsHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a3a31125d8489551f1eec143013661bf385f29a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212443"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassFlagsT*  
Un champ d’indicateurs qui spécifie un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.

*ILst*  
Liste des ID d’interface.

*IsDelegateToClass*  
Spécifiez **true** si l’instance actuelle de `Implements` est une classe de base de l’ID d’interface première dans *ILst*; sinon, **false**.

## <a name="remarks"></a>Notes

Permet d’implémenter le [implémente](../windows/implements-structure.md) structure.

Ce modèle parcourt une liste d’interfaces et les ajoute comme classes de base et en tant que les informations nécessaires pour activer `QueryInterface`.

## <a name="members"></a>Membres

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ImplementsHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Référence (Windows Runtime Library)](https://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)