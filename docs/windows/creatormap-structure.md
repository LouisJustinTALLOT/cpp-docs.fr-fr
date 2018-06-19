---
title: CreatorMap (Structure) | Documents Microsoft
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
ms.openlocfilehash: a6113737d7463354ffa273ced61b190246f63a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873282"
---
# <a name="creatormap-structure"></a>CreatorMap (structure)
Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>Notes  
 Contient des informations sur la façon d’initialiser, enregistrer et annuler l’inscription des objets.  
  
 CreatorMap contient les informations suivantes :  
  
-   Comment initialiser, enregistrer et annuler l’inscription des objets.  
  
-   Comment comparer les données d’activation en fonction d’une fabrique de COM ou Windows Runtime classique.  
  
-   Informations sur la fabrique du cache et nom de serveur pour une interface.  
  
## <a name="members"></a>Membres  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CreatorMap::activationId, données de membre](../windows/creatormap-activationid-data-member.md)|Représente un ID d’objet qui est identifié par un ID de classe COM classique ou un nom de Windows Runtime.|  
|[CreatorMap::factoryCache, données de membre](../windows/creatormap-factorycache-data-member.md)|Stocke le pointeur vers le cache de fabrication pour le CreatorMap.|  
|[CreatorMap::factoryCreator, données de membre](../windows/creatormap-factorycreator-data-member.md)|Crée une fabrique pour le CreatorMap spécifié.|  
|[CreatorMap::serverName, données de membre](../windows/creatormap-servername-data-member.md)|Stocke le nom du serveur pour le CreatorMap.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CreatorMap`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** module.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)