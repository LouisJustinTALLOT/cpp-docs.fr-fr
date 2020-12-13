---
description: 'En savoir plus sur : classe CComSimpleThreadAllocator'
title: CComSimpleThreadAllocator, classe
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
ms.openlocfilehash: 5925707ecd459475d9e9002af76fb76dd9cf9d38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142185"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator, classe

Cette classe gère la sélection des threads pour la classe `CComAutoThreadModule` .

## <a name="syntax"></a>Syntaxe

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSimpleThreadAllocator :: GetThread,](#getthread)|Sélectionne un thread.|

## <a name="remarks"></a>Notes

`CComSimpleThreadAllocator` gère la sélection des threads pour [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` parcourt simplement chaque thread et retourne le suivant dans la séquence.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a> CComSimpleThreadAllocator :: GetThread,

Sélectionne un thread en spécifiant le thread suivant dans la séquence.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Paramètres

*pApt*<br/>
Non utilisé dans l’implémentation par défaut d’ATL.

*nThreads*<br/>
Nombre maximal de threads dans le module EXE.

### <a name="return-value"></a>Valeur renvoyée

Entier compris entre zéro et (*nThreads* -1). Identifie l’un des threads dans le module EXE.

### <a name="remarks"></a>Notes

Vous pouvez remplacer `GetThread` pour fournir une méthode de sélection différente ou pour utiliser le paramètre *pApt* .

`GetThread` est appelé par [CComAutoThreadModule :: CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Voir aussi

[CComApartment, classe](../../atl/reference/ccomapartment-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
