---
title: Erreur irrécupérable C1509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 837ab5b7cf76b724726c6c52fbfe974d4da6ca85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033132"
---
# <a name="fatal-error-c1509"></a>Erreur irrécupérable C1509

limite du compilateur : trop d’états de gestionnaire dans la fonction 'fonction' exception. Simplifiez la fonction

Le code dépasse une limite interne sur les États de gestionnaire d’exceptions (32 768 états).

La cause la plus courante est que la fonction contient une expression complexe des variables de la classe définie par l’utilisateur et des opérateurs arithmétiques.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifier les expressions en assignant des sous-expressions communes à des variables temporaires.

1. Fractionnez la fonction en fonctions plus petites.