---
description: 'En savoir plus sur : erreur irrécupérable C1509'
title: Erreur irrécupérable C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: dc2483ae96f599912b3ba6d1594257fec81ac251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276346"
---
# <a name="fatal-error-c1509"></a>Erreur irrécupérable C1509

limite du compilateur : trop d’États de gestionnaire d’exceptions dans la fonction’Function'. simplifier la fonction

Le code dépasse une limite interne sur les États du gestionnaire d’exceptions (États 32 768).

La cause la plus courante est que la fonction contient une expression complexe de variables de classe définies par l’utilisateur et d’opérateurs arithmétiques.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifiez les expressions en assignant des sous-expressions communes à des variables temporaires.

1. Fractionnez la fonction en fonctions plus petites.
