---
title: Classe CComSimpleThreadAllocator
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327343"
---
# <a name="ccomsimplethreadallocator-class"></a>Classe CComSimpleThreadAllocator

Cette classe gère la `CComAutoThreadModule`sélection de thread pour la classe .

## <a name="syntax"></a>Syntaxe

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Sélectionne un thread.|

## <a name="remarks"></a>Notes

`CComSimpleThreadAllocator`gère la sélection de thread pour [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`il suffit de cycles à travers chaque thread et retourne le prochain dans la séquence.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleThreadAllocator::GetThread

Sélectionne un thread en spécifiant le thread suivant dans la séquence.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Paramètres

*pApt*<br/>
Non utilisé dans la implémentation par défaut d’ATL.

*nThreads*<br/>
Le nombre maximum de threads dans le module EXE.

### <a name="return-value"></a>Valeur de retour

Un intégrant entre zéro et *(nThreads* - 1). Identifie l’un des fils du module EXE.

### <a name="remarks"></a>Notes

Vous pouvez `GetThread` remplacer pour fournir une méthode de sélection différente ou pour utiliser le *paramètre pApt.*

`GetThread`est appelé par [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Voir aussi

[Classe CComApartment](../../atl/reference/ccomapartment-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
