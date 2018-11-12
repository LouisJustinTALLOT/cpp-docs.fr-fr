---
title: Erreur irrécupérable C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620003"
---
# <a name="fatal-error-c1509"></a>Erreur irrécupérable C1509

limite du compilateur : trop d’états de gestionnaire dans la fonction 'fonction' exception. Simplifiez la fonction

Le code dépasse une limite interne sur les États de gestionnaire d’exceptions (32 768 états).

La cause la plus courante est que la fonction contient une expression complexe des variables de la classe définie par l’utilisateur et des opérateurs arithmétiques.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifier les expressions en assignant des sous-expressions communes à des variables temporaires.

1. Fractionnez la fonction en fonctions plus petites.