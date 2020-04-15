---
title: Classe CAtlAutoThreadModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321540"
---
# <a name="catlautothreadmodulet-class"></a>Classe CAtlAutoThreadModuleT

Cette classe fournit des méthodes pour la mise en œuvre d’un serveur COM de type appartement pooled.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
La classe qui implémentera le serveur COM.

*ThreadAllocator (en)*<br/>
La sélection de thread de gestion de classe. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Spécifie l’intervalle de temps d’exécution, en millisecondes. La valeur par défaut est INFINITE, ce qui signifie que l’intervalle de temps d’écoulement de la méthode ne s’écoule jamais.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Cette fonction statique calcule et renvoie dynamiquement le nombre maximum de threads pour le module EXE, en fonction du nombre de processeurs.|

## <a name="remarks"></a>Notes

La classe [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) `CAtlAutoThreadModuleT` dérive de afin de mettre en œuvre un thread-pooled, appartement-modèle COM serveur. Il remplace la classe obsolète [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Cette classe ne doit pas être utilisée dans un DLL, car la valeur *dwWait* par défaut d’INFINITE entraînera une impasse lorsque le DLL est déchargé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Cette fonction statique calcule et renvoie dynamiquement le nombre maximum de threads pour le module EXE, en fonction du nombre de processeurs.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de threads à créer dans le module EXE.

### <a name="remarks"></a>Notes

Remplacez cette méthode si vous souhaitez utiliser une méthode différente pour calculer le nombre de threads. Par défaut, le nombre de threads est basé sur le nombre de processeurs.

## <a name="see-also"></a>Voir aussi

[Classe IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)
