---
title: Fonctions globales de Point de connexion | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs: C++
helpviewer_keywords: connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce7f6fc3d2a0b51f88952dd720955367b1dfe9d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connection-point-global-functions"></a>Fonctions globales de Point de connexion
Ces fonctions prennent en charge les points de connexion et le récepteur de cartes.  
  
> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.|  
|[AtlUnadvise](#atlunadvise)|Met fin à la connexion établie via `AtlAdvise`.|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|Indique qu’il contient ou avertit les entrées dans une table de récepteur d’événements.|  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkCP`  
 [in] Un pointeur vers le **IUnknown** de l’objet, le client souhaite se connecter avec.  
  
 *pUnk*  
 [in] Un pointeur vers du client **IUnknown**.  
  
 `iid`  
 [in] Le GUID du point de connexion. En règle générale, cela est identique à l’interface sortante gérée par le point de connexion.  
  
 `pdw`  
 [out] Pointeur vers le cookie qui identifie de façon unique la connexion.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Le récepteur implémente l’interface sortante pris en charge par le point de connexion. Le client utilise le `pdw` cookie pour supprimer la connexion en le passant à [AtlUnadvise](#atlunadvise).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 Met fin à la connexion établie via [AtlAdvise](#atladvise).  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkCP`  
 [in] Un pointeur vers le **IUnknown** de l’objet auquel le client est connecté avec.  
  
 `iid`  
 [in] Le GUID du point de connexion. En règle générale, cela est identique à l’interface sortante gérée par le point de connexion.  
  
 `dw`  
 [in] Le cookie qui identifie de façon unique la connexion.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 Appelez cette fonction pour conseiller ou déconseiller toutes les entrées de la table d'événements du récepteur de l'objet.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>Paramètres  
 *pT*  
 [in] Pointeur vers l’objet qui contient la table de récepteur.  
  
 `bAdvise`  
 [in] **true** si toutes les entrées de récepteur doivent être avertie ; **false** si toutes les entrées de récepteur doivent être cessent d’être averties.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)   
 [Macros de point de connexion](../../atl/reference/connection-point-macros.md)
