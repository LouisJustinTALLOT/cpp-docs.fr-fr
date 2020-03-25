---
title: Erreur irrécupérable C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204930"
---
# <a name="fatal-error-c1002"></a>Erreur irrécupérable C1002

espace du tas insuffisant pour le compilateur lors de la deuxième passe

Le compilateur a manqué d’espace mémoire dynamique pendant la deuxième passe, probablement en raison d’un programme avec trop de symboles ou d’expressions complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Divisez le fichier source en plusieurs fichiers plus petits.

1. Scinder les expressions en sous-expressions plus petites.

1. Supprimez les autres programmes ou pilotes qui consomment de la mémoire.
