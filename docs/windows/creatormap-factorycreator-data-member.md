---
title: Creatormap::FactoryCreator, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57f6e841326339f78d24fa8affea5e74ae5b8d74
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465381"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator, données de membre
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT (*factoryCreator)(  
   unsigned int* currentflags,  
   const CreatorMap* entry,  
   REFIID iidClassFactory,  
 IUnknown** factory);  
```  
  
## <a name="parameters"></a>Paramètres  
 *currentflags*  
 Parmi les [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.  
  
 *entry*  
 Un CreatorMap.  
  
 *iidClassFactory*  
 L’ID d’interface d’une fabrique de classe.  
  
 *fabrique*  
 Lorsque l’opération terminée, l’adresse d’une fabrique de classe.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="remarks"></a>Notes  
 Crée une fabrique pour la CreatorMap spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [CreatorMap (Structure)](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)