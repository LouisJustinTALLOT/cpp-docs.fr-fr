---
title: Erreur irrécupérable C1002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044143"
---
# <a name="fatal-error-c1002"></a>Erreur irrécupérable C1002

espace du tas insuffisant pour le compilateur lors de la deuxième passe

Le compilateur a manqué d’espace mémoire dynamique, la deuxième phase, probablement en raison d’un programme avec trop de symboles ou des expressions complexes.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Diviser le fichier source en plusieurs petits fichiers.

1. Fractionnez les expressions en sous-expressions plus petites.

1. Supprimez les autres programmes ou pilotes qui consomment de la mémoire.