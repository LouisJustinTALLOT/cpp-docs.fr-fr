---
description: 'En savoir plus sur : classe CAtlAutoThreadModuleT'
title: CAtlAutoThreadModuleT, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: ad55c78488567c12477c427b99a527b8154ddd22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158411"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT, classe

Cette classe fournit des méthodes pour implémenter un serveur COM à pool de threads et de modèle Apartment.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe qui implémentera le serveur COM.

*ThreadAllocator*<br/>
Classe qui gère la sélection des threads. La valeur par défaut est [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Spécifie l’intervalle de délai d’attente, en millisecondes. La valeur par défaut est Infinite, ce qui signifie que l’intervalle de délai d’attente de la méthode n’est jamais écoulé.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Cette fonction statique calcule dynamiquement et retourne le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs.|

## <a name="remarks"></a>Notes

La classe [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) dérive de `CAtlAutoThreadModuleT` pour implémenter un serveur com à pool de threads et de modèle Apartment. Il remplace la classe obsolète [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Cette classe ne doit pas être utilisée dans une DLL, car la valeur *dwWait* par défaut Infinite provoque un interblocage lorsque la dll est déchargée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a> CAtlAutoThreadModuleT::GetDefaultThreads

Cette fonction statique calcule dynamiquement et retourne le nombre maximal de threads pour le module EXE, en fonction du nombre de processeurs.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de threads à créer dans le module EXE.

### <a name="remarks"></a>Notes

Substituez cette méthode si vous souhaitez utiliser une autre méthode pour calculer le nombre de threads. Par défaut, le nombre de threads est basé sur le nombre de processeurs.

## <a name="see-also"></a>Voir aussi

[IAtlAutoThreadModule, classe](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule, classe](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
