---
title: Archétype de travail | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cee9df0b137655fe66e68c189de756f15233a94d
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255976"
---
# <a name="worker-archetype"></a>Archétype de travail
Les classes qui se conforment à la *travail* archétype fournissent le code pour traiter des éléments de travail en file d’attente sur un pool de threads.  
  
 **Implémentation**  
  
 Pour implémenter une classe conforme à cette archétype, la classe doit fournir les fonctionnalités suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[Initialize](#initialize)|Appelé pour initialiser l’objet de travail avant que toutes les demandes sont passées à [Execute](#execute).|  
|[Exécuter](#execute)|Appelé pour traiter un élément de travail.|  
|[Arrêter](#terminate)|Appelé pour annuler l’initialisation de l’objet travail une fois que toutes les demandes qui ont été transmis au [Execute](#execute).|  
  
|TypeDef|Description|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Typedef pour le type d’élément de travail qui peut être traité par la classe de travail.|  
  
 Par défaut *travail* classe ressemble à ceci :  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **Implémentations existantes**  
  
 Ces classes sont conformes à cette archétype :  
  
|Classe|Description|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes du pool de threads et les transmet à un objet de travail qui est créé et détruit pour chaque demande.|  
  
 **Utilisez**  
  
 Ces paramètres de modèle que la classe se conforme à cette archétype :  
  
|Nom du paramètre|Utilisé par|  
|--------------------|-------------|  
|*Processus de travail*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Processus de travail*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
Appelé pour traiter un élément de travail.  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>Paramètres  
 `request`  
 L’élément de travail à traiter. L’élément de travail est du même type que `RequestType`.  
  
 `pvWorkerParam`  
 Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Initialize` et `Terminate`.  
  
 `pOverlapped`  
 Un pointeur vers le [OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) structure utilisée pour créer la file d’attente à laquelle les éléments ont été en file d’attente.  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
Appelé pour initialiser l’objet de travail avant que toutes les demandes sont passées à `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvParam`  
 Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Terminate` et `WorkerArchetype::Execute`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourner **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
Typedef pour le type d’élément de travail qui peut être traité par la classe de travail.  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>Notes  
 Ce type doit être utilisé comme premier paramètre de `WorkerArchetype::Execute` et doit être capable d’en cours de conversion vers et depuis un ULONG_PTR entière.  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
Appelé pour annuler l’initialisation de l’objet travail une fois que toutes les demandes qui ont été transmis au `WorkerArchetype::Execute`).  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>Paramètres  
 `pvParam`  
 Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Initialize` et `WorkerArchetype::Execute`.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)



