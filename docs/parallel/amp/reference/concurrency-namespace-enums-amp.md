---
title: Concurrency, énumérations de l’espace de noms (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376321"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency, énumérations de l’espace de noms (AMP)

|||
|-|-|
|[access_type, énumération](#access_type)|[Énumération queuing_mode](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type Énumération

Type d’énumération utilisé pour désigner les différents types d’accès aux données.

```cpp
enum access_type;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`access_type_auto`|Choisissez automatiquement `access_type` le meilleur pour l’accélérateur.|
|`access_type_none`|Dédié. L’allocation n’est accessible que sur l’accélérateur et non sur le processeur.|
|`access_type_read`|Partagé. L’allocation est accessible sur l’accélérateur et est lisible sur le processeur.|
|`access_type_read_write`|Partagé. L’allocation est accessible sur l’accélérateur et est aptielle sur le processeur.|
|`access_type_write`|Partagé. L’allocation est accessible sur l’accélérateur et est à la fois lisible et aptable sur le processeur.|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode Énumération

Spécifie les modes de file d’attente qui sont pris en charge sur l’accélérateur.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`queuing_mode_immediate`|Un mode de file d’attente qui spécifie que toutes les commandes, par exemple, [parallel_for_each fonction (AMP DE C),](concurrency-namespace-functions-amp.md#parallel_for_each)sont envoyées au dispositif d’accélérateur correspondant dès qu’elles retournent à l’appelant.|
|`queuing_mode_automatic`|Un mode de file d’attente qui spécifie que les commandes sont alignés sur une file d’attente de commande qui correspond à [l’objet accelerator_view.](accelerator-view-class.md) Les commandes sont envoyées à l’appareil [lorsqu’accelerator_view ::flush](accelerator-view-class.md#flush) est appelé.|

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
