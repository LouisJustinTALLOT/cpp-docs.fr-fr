---
title: Classe de CAtlAutoThreadModule | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c89d142254909591ebd01bfa859be5488cbfaf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356616"
---
# <a name="catlautothreadmodule-class"></a>Classe de CAtlAutoThreadModule
Cette classe implémente un serveur COM mis en pool de threads, le modèle de cloisonnement.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>Notes  
 `CAtlAutoThreadModule` dérive de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) et implémente un serveur COM mis en pool de threads, le modèle de cloisonnement. `CAtlAutoThreadModule` utilise [CComApartment](../../atl/reference/ccomapartment-class.md) pour gérer un cloisonnement pour chaque thread dans le module.  
  
 Vous devez utiliser le [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro dans votre définition de l’objet classe pour spécifier [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) en tant que la fabrique de classe. Vous devez ensuite ajouter une instance unique d’une classe dérivée de `CAtlAutoThreadModuleT` comme `CAtlAutoThreadModule`. Par exemple :  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Cette classe remplace l’obsolète [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)   
 [Classe de IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Module (Classes)](../../atl/atl-module-classes.md)
