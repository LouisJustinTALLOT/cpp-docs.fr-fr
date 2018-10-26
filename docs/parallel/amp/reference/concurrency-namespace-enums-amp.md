---
title: Énumérations d’espace de noms d’accès concurrentiel (AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58d70b995642eaca3dbefd75383e6d6bf06f2c62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082429"
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
