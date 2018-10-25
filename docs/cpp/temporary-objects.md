---
title: Objets temporaires | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e94fa412b76107dde90d3a6a664ec68c6b6bdaf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078790"
---
# <a name="temporary-objects"></a>Objets temporaires

Dans certains cas, le compilateur a besoin de créer des objets temporaires. Ces objets temporaires peuvent être créés pour les raisons suivantes :

- Pour initialiser un **const** référence avec un initialiseur d’un type différent de celui du type sous-jacent de la référence en cours d’initialisation.

- pour stocker la valeur de retour d'une fonction qui retourne un type défini par l'utilisateur. Ces objets temporaires sont créés uniquement si votre programme ne copie pas la valeur de retour passée à un objet. Exemple :

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   La valeur de retour n'étant pas copiée dans un autre objet, un objet temporaire est créé. Un des cas les plus courants où des objets temporaires sont créés est l'évaluation d'une expression où des fonctions surchargées d'opérateur doivent être appelées. Ces fonctions d'opérateur surchargées retournent un type défini par l'utilisateur qui n'est souvent pas copié dans un autre objet.

   Prenons l'exemple de l'expression `ComplexResult = Complex1 + Complex2 + Complex3`. L'expression `Complex1 + Complex2` est évaluée, et le résultat est stocké dans un objet temporaire. Ensuite, l’expression *temporaire* `+ Complex3` est évaluée, et le résultat est copié dans `ComplexResult` (en supposant que l’opérateur d’assignation ne soit pas surchargé).

- Pour stocker le résultat d'un cast en un type défini par l'utilisateur. Lorsqu'un objet d'un type donné est converti explicitement en un type défini par l'utilisateur, ce nouvel objet est construit sous la forme d'un objet temporaire.

Les objets temporaires ont une durée de vie définie par leur point de conception et le point auquel ils sont détruits. Toute expression qui crée plusieurs objet temporaire finalement les détruit dans l'ordre inverse dans lequel ils ont été créés. Les points auxquels la destruction se produit sont présentés dans le tableau suivant.

### <a name="destruction-points-for-temporary-objects"></a>Points de destruction des objets temporaires

|Motif de création de l'objet temporaire|Point de destruction|
|------------------------------|-----------------------|
|Résultat de l'évaluation de l'expression|Tous les objets temporaires créés à la suite d’évaluation de l’expression sont détruits à la fin de l’instruction d’expression (c'est-à-dire au point-virgule), ou à la fin des expressions de contrôle pour **pour**, **si**, **tandis que**, **faire**, et **basculer** instructions.|
|L’initialisation **const** références|Si un initialiseur n'est pas une l-value du même type que la référence initialisée, un objet temporaire du type d'objet sous-jacent est créé et initialisé avec l'expression d'initialisation. Cet objet temporaire est détruit juste après la destruction de l’objet de référence auquel il est lié.|