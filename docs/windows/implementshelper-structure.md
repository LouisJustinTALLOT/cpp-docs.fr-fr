---
title: ImplementsHelper (Structure) | Documents Microsoft
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
ms.openlocfilehash: 58f27e418946987633f771bc8d2c3224bc2cd7fd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875937"
---
# <a name="implementshelper-structure"></a>ImplementsHelper (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `RuntimeClassFlagsT`  
 Un champ d’indicateurs qui spécifie un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.  
  
 `ILst`  
 Liste des ID d’interface.  
  
 `IsDelegateToClass`  
 Spécifiez `true` si l’instance actuelle d’implémente est une classe de base du premier ID d’interface dans `ILst`; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Permet d’implémenter le [implémente](../windows/implements-structure.md) structure.  
  
 Ce modèle parcourt la liste des interfaces et les ajoute comme classes de base et que les informations nécessaires pour permettre à QueryInterface.  
  
## <a name="members"></a>Membres  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Référence (bibliothèque Windows Runtime)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)