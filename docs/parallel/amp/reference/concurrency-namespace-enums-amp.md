---
title: Concurrency, énumérations de l’espace de noms (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126947"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency, énumérations de l’espace de noms (AMP)

|||
|-|-|
|[Énumération access_type](#access_type)|[Énumération queuing_mode](#queuing_mode)|

## <a name="access_type"></a>Énumération access_type

Type d’énumération utilisé pour désigner les différents types d’accès aux données.

```cpp
enum access_type;
```

### <a name="values"></a>Valeurs

|Name|Description|
|----------|-----------------|
|`access_type_auto`|Choisissez automatiquement le meilleur `access_type` pour l’accélérateur.|
|`access_type_none`|Spécialisés. L’allocation est uniquement accessible sur l’accélérateur et non sur l’UC.|
|`access_type_read`|Partagé. L’allocation est accessible sur l’accélérateur et est lisible sur le processeur.|
|`access_type_read_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en écriture sur l’UC.|
|`access_type_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en lecture et en écriture sur l’UC.|

## <a name="queuing_mode"></a>Énumération queuing_mode

Spécifie les modes de mise en file d’attente pris en charge sur l’accélérateur.

```cpp
enum queuing_mode;
```

### <a name="values"></a>Valeurs

|Name|Description|
|----------|-----------------|
|`queuing_mode_immediate`|Mode de mise en file d’attente qui spécifie que toutes les commandes, par exemple, [Parallel_for_each fonction (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each), sont envoyées au périphérique accélérateur correspondant dès qu’elles sont retournées à l’appelant.|
|`queuing_mode_automatic`|Mode de mise en file d’attente qui spécifie que les commandes sont mises en file d’attente dans une file d’attente de commandes qui correspond à l’objet [accelerator_view](accelerator-view-class.md) . Les commandes sont envoyées à l’appareil lorsque [accelerator_view :: Flush](accelerator-view-class.md#flush) est appelé.|

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
