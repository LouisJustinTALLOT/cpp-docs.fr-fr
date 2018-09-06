---
title: Spécification du modèle de thread pour un projet (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8a37a3ec730b727f6e214aafad1a4acc65b1dc3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760027"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Spécification du modèle de thread pour un projet (ATL)

Les macros suivantes sont disponibles pour spécifier le modèle de thread d’un projet ATL :

|Macro|Instructions d’utilisation|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|Définir si tous vos objets utilisent le modèle de thread unique.|
|_ATL_APARTMENT_THREADED|Définir si un ou plusieurs de vos objets utilisent le cloisonnement des threads.|
|_ATL_FREE_THREADED|Définir si un ou plusieurs de vos objets utilisent de thread libre ou neutre. Code existant peut contenir des références à la macro équivalente [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|

Si vous ne définissez pas une de ces macros pour votre projet, _ATL_FREE_THREADED sera appliquée.

Les macros affectent les performances d’exécution comme suit :

- Spécification de la macro qui correspond aux objets dans votre projet peut améliorer les performances de l’exécution.

- Spécification d’un niveau supérieur de la macro, par exemple si vous spécifiez _ATL_APARTMENT_THREADED lorsque tous les objets sont seul thread, dégradera légèrement les performances au moment de l’exécution.

- Spécification d’un niveau inférieur de la macro, par exemple, si vous spécifiez _ATL_SINGLE_THREADED lorsqu’un ou plusieurs de vos objets utilisent thread cloisonné ou libre, peut entraîner de votre application échoue au moment de l’exécution.

Consultez [Options, Assistant objet Simple ATL](../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description de la thread les modèles disponibles pour un objet ATL.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)

