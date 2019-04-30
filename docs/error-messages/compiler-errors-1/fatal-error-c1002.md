---
title: Erreur irrécupérable C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344834"
---
# <a name="fatal-error-c1002"></a>Erreur irrécupérable C1002

espace du tas insuffisant pour le compilateur lors de la deuxième passe

Le compilateur a manqué d’espace mémoire dynamique, la deuxième phase, probablement en raison d’un programme avec trop de symboles ou des expressions complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Diviser le fichier source en plusieurs petits fichiers.

1. Fractionnez les expressions en sous-expressions plus petites.

1. Supprimez les autres programmes ou pilotes qui consomment de la mémoire.