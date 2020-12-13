---
description: 'En savoir plus sur : spécification du modèle de thread pour un projet (ATL)'
title: Spécification du modèle de thread pour un projet (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 81bf8413a2118797ec0e0c177a06468b8e3c7ba0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138474"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Spécification du modèle de thread pour un projet (ATL)

Les macros suivantes sont disponibles pour spécifier le modèle de thread d’un projet ATL :

|Macro|Instructions pour l’utilisation de|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|Définissez si tous vos objets utilisent le modèle de thread unique.|
|_ATL_APARTMENT_THREADED|Définissez si un ou plusieurs de vos objets utilisent le thread cloisonné.|
|_ATL_FREE_THREADED|Définissez si un ou plusieurs de vos objets utilisent le Threading libre ou neutre. Le code existant peut contenir des références à la macro [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)équivalente.|

Si vous ne définissez pas l’une de ces macros pour votre projet, _ATL_FREE_THREADED sera appliqué.

Les macros affectent les performances au moment de l’exécution comme suit :

- La spécification de la macro qui correspond aux objets de votre projet peut améliorer les performances d’exécution.

- Si vous spécifiez un niveau de macro supérieur, par exemple si vous spécifiez _ATL_APARTMENT_THREADED lorsque tous vos objets sont à thread unique, les performances d’exécution seront légèrement dégradées.

- Si vous spécifiez un niveau de macro inférieur, par exemple, si vous spécifiez _ATL_SINGLE_THREADED quand un ou plusieurs de vos objets utilisent le thread cloisonné ou le Threading libre, peut provoquer l’échec de votre application au moment de l’exécution.

Consultez [options, Assistant objet simple ATL](../atl/reference/options-atl-simple-object-wizard.md) pour obtenir une description des modèles de thread disponibles pour un objet ATL.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)
