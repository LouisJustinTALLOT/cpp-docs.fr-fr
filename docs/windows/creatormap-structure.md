---
title: CreatorMap (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fadba5993b7445af2386f6e0669f210e29560c6c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464254"
---
# <a name="creatormap-structure"></a>CreatorMap (structure)
Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>Notes  
 Contient des informations sur la façon d’initialiser, inscrire et annuler l’inscription d’objets.  
  
 **CreatorMap** contient les informations suivantes :  
  
-   Guide pratique pour initialiser, inscrire et annuler l’inscription d’objets.  
  
-   Comment comparer les données d’activation en fonction d’une fabrique classique COM ou Windows Runtime.  
  
-   Informations sur la fabrique du cache et nom de serveur pour une interface.  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CreatorMap::activationId, données de membre](../windows/creatormap-activationid-data-member.md)|Représente un ID d’objet qui est identifié par un ID de classe COM classique ou un nom de Windows Runtime.|  
|[CreatorMap::factoryCache, données de membre](../windows/creatormap-factorycache-data-member.md)|Stocke le pointeur vers le cache de fabrication pour le **CreatorMap**.|  
|[CreatorMap::factoryCreator, données de membre](../windows/creatormap-factorycreator-data-member.md)|Crée une fabrique pour spécifié **CreatorMap**.|  
|[CreatorMap::serverName, données de membre](../windows/creatormap-servername-data-member.md)|Stocke le nom du serveur pour le **CreatorMap**.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CreatorMap`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)