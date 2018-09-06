---
title: Archétype de travail | Microsoft Docs
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
ms.openlocfilehash: 13f34f7ceca5cf958e981f8390044863a07b4317
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767163"
---
# <a name="worker-archetype"></a>Archétype de travail

Classes qui se conforment à la *worker* archétype fournissent le code pour traiter des éléments de travail en file d’attente sur un pool de threads.

**Implémentation**

Pour implémenter une classe conforme à cette archétype, la classe doit fournir les fonctionnalités suivantes :

|Méthode|Description|
|------------|-----------------|
|[Initialize](#initialize)|Appelée pour initialiser l’objet de travail avant que toutes les demandes sont passées à [Execute](#execute).|
|[Execute](#execute)|Appelé pour traiter un élément de travail.|
|[Terminate](#terminate)|Appelé pour annuler l’initialisation de l’objet de travail une fois que toutes les demandes ont été transmis au [Execute](#execute).|

|TypeDef|Description|
|-------------|-----------------|
|[RequestType](#requesttype)|Typedef pour le type d’élément de travail qui peut être traitée par la classe de travail.|

Classique *worker* classe ressemble à ceci :

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Implémentations existantes**

Ces classes sont conformes à cette archétype :

|Classe|Description|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes du pool de threads et les transmet à un objet de travail qui est créé et détruit pour chaque demande.|

**Utilisation**

Ces paramètres de modèle que la classe à se conformer à cette archétype :

|Nom du paramètre|Utilisé par|
|--------------------|-------------|
|*Travail*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Travail*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Configuration requise

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

*Demande*  
L’élément de travail à traiter. L’élément de travail est du même type que `RequestType`.

*pvWorkerParam*  
Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Initialize` et `Terminate`.

*pOverlapped*  
Un pointeur vers le [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure utilisée pour créer la file d’attente à laquelle le travail des éléments ont été en file d’attente.

## <a name="initialize"></a> WorkerArchetype::Initialize

Appelée pour initialiser l’objet de travail avant que toutes les demandes sont passées à `WorkerArchetype::Execute`.  
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*  
Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Terminate` et `WorkerArchetype::Execute`.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

## <a name="requesttype"></a> WorkerArchetype::RequestType

Typedef pour le type d’élément de travail qui peut être traitée par la classe de travail.

```  
typedef MyRequestType RequestType;    
```

### <a name="remarks"></a>Notes

Ce type doit être utilisé comme premier paramètre de `WorkerArchetype::Execute` et doit être capable d’en cours de conversion vers et depuis un ULONG_PTR entière.

## <a name="terminate"></a> WorkerArchetype::Terminate

Appelé pour annuler l’initialisation de l’objet de travail une fois que toutes les demandes ont été transmis au `WorkerArchetype::Execute`).

``` 
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Paramètres

*pvParam*  
Un paramètre personnalisé compris par la classe de travail. Également transmis à `WorkerArchetype::Initialize` et `WorkerArchetype::Execute`.

## <a name="see-also"></a>Voir aussi

[Concepts](../../atl/active-template-library-atl-concepts.md)   
[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)

