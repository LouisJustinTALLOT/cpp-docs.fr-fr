---
title: Erreur irrécupérable C1054 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1054
dev_langs:
- C++
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 439019b1f510127ae54e77d445d59e86be09a49b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101967"
---
# <a name="fatal-error-c1054"></a>Erreur irrécupérable C1054

limite du compilateur : initialiseurs imbriqués trop profondément

Le code dépasse la limite d’imbrication des initialiseurs (10-15 niveaux, selon la combinaison de types en cours d’initialisation).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Simplifiez les types de données en cours d’initialisation pour réduire l’imbrication.

1. Initialiser des variables dans des instructions distinctes après la déclaration.