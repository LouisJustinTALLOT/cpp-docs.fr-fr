---
description: 'En savoir plus sur : erreur irrécupérable C1002'
title: Erreur irrécupérable C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: edd4ffbd6ce4c8a7f70640619d8dc52775dd0195
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262709"
---
# <a name="fatal-error-c1002"></a>Erreur irrécupérable C1002

espace du tas insuffisant pour le compilateur lors de la deuxième passe

Le compilateur a manqué d’espace mémoire dynamique pendant la deuxième passe, probablement en raison d’un programme avec trop de symboles ou d’expressions complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Divisez le fichier source en plusieurs fichiers plus petits.

1. Scinder les expressions en sous-expressions plus petites.

1. Supprimez les autres programmes ou pilotes qui consomment de la mémoire.
