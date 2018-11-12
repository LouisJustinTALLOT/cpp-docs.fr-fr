---
title: progress_reporter, classe
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: 5fc433beea560001badf919f55dbff45428ef876
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464855"
---
# <a name="progressreporter-class"></a>progress_reporter, classe

La classe d'indication de la progression permet de signaler des notifications de progression d'un type spécifique. Chaque objet progress_reporter est lié à une opération ou à une action asynchrone particulière.

## <a name="syntax"></a>Syntaxe

```
template<typename _ProgressType>
class progress_reporter;
```

#### <a name="parameters"></a>Paramètres

*_ProgressType*<br/>
Type de charge utile de chaque notification d'avancement signalé via l'indicateur de progression.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[report](#report)|Envoie un rapport d'avancement à l'action asynchrone ou à l'opération à laquelle est lié cet indicateur de progression.|

## <a name="remarks"></a>Notes

Ce type est uniquement disponible pour les applications Windows Runtime.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`progress_reporter`

## <a name="requirements"></a>Configuration requise

**En-tête :** ppltasks.h

**Espace de noms :** concurrency

##  <a name="ctor"></a> progress_reporter

```
progress_reporter();
```

##  <a name="report"></a> rapport

Envoie un rapport d'avancement à l'action asynchrone ou à l'opération à laquelle est lié cet indicateur de progression.

```
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
La charge utile à signaler via une notification de progression.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
