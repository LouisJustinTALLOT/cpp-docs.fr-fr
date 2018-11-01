---
title: Énumérations d’espace de noms d’accès concurrentiel (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: d78299a9ce47760e6b1340c69d8be699a5eed8a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433567"
---
# <a name="concurrency-namespace-enums-amp"></a>Énumérations d’espace de noms d’accès concurrentiel (AMP)

|||
|-|-|
|[access_type, énumération](#access_type)|[Énumération queuing_mode](#queuing_mode)|

##  <a name="access_type"></a>  access_type, énumération

Type d’énumération utilisé pour identifier les différents types d’accès aux données.

```
enum access_type;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`access_type_auto`|Choisissez automatiquement le meilleur `access_type` pour l’accélérateur.|
|`access_type_none`|Dédié. L’allocation est uniquement accessible sur l’accélérateur et non sur l’UC.|
|`access_type_read`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en lecture sur l’UC.|
|`access_type_read_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en écriture sur l’UC.|
|`access_type_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en lecture et en écriture sur le processeur.|

##  <a name="queuing_mode"></a>  Énumération queuing_mode

Spécifie les modes de file d’attente qui sont pris en charge sur l’accélérateur.

```
enum queuing_mode;
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`queuing_mode_immediate`|Un mode de file d’attente qui spécifie que toutes les commandes, par exemple, [parallel_for_each, fonction (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), sont envoyées au périphérique accélérateur correspondant dès qu’elles renvoient à l’appelant.|
|`queuing_mode_automatic`|Un mode de file d’attente qui spécifie que commandes être la file d’attente sur une file d’attente de commande qui correspond à la [accelerator_view](accelerator-view-class.md) objet. Les commandes sont envoyées à l’appareil lorsque [accelerator_view::flush](accelerator-view-class.md#flush) est appelée.|

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
