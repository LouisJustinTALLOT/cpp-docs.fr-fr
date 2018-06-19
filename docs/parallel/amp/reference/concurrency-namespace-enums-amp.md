---
title: Énumérations d’espace de noms d’accès concurrentiel (AMP) | Documents Microsoft
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
ms.openlocfilehash: a67b5e77b8ab8c52e55dea96e64a3f16a4d70e39
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695666"
---
# <a name="concurrency-namespace-enums-amp"></a>Énumérations d’espace de noms d’accès concurrentiel (AMP)
|||  
|-|-|  
|[access_type, énumération](#access_type)|[Énumération queuing_mode](#queuing_mode)|  
  
##  <a name="access_type"></a>  access_type, énumération  
 Type d’énumération utilisé pour désigner les différents types d’accès aux données.  
  
```  
enum access_type;  
```  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`access_type_auto`|Choisir automatiquement le meilleur `access_type` pour l’accélérateur.|  
|`access_type_none`|Dédié. L’allocation est uniquement accessible sur l’accélérateur et non sur l’UC.|  
|`access_type_read`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en lecture sur l’UC.|  
|`access_type_read_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en écriture sur l’UC.|  
|`access_type_write`|Partagé. L’allocation est accessible sur l’accélérateur et est accessible en lecture et en écriture sur le processeur.|  

  
##  <a name="queuing_mode"></a>  Énumération queuing_mode  
 Spécifie les modes de files d’attente qui sont pris en charge sur l’accélérateur.  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`queuing_mode_immediate`|Un mode de files d’attente qui spécifie tous les commandes, par exemple, [parallel_for_each, fonction (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), sont envoyés à l’appareil d’accélérateur correspondant dès qu’elles sont retournées à l’appelant.|  
|`queuing_mode_automatic`|Un mode de files d’attente qui spécifie que commandes mises en attente une file d’attente de la commande qui correspond à la [accelerator_view](accelerator-view-class.md) objet. Les commandes sont envoyées à l’appareil lors de la [accelerator_view::flush](accelerator-view-class.md#flush) est appelée.|   
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
