---
title: Avertissement du compilateur (niveau 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: c30b98204f447f4d9d0ab8d687602a361d909363
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218063"
---
# <a name="compiler-warning-level-4-c4710"></a>Avertissement du compilateur (niveau 4) C4710

'fonction' : fonction non inline

La fonction donnée a été sélectionnée pour l’expansion Inline, mais le compilateur n’a pas effectué l’incorporation.

L’incorporation est effectuée à la discrétion du compilateur. Le **`inline`** mot clé, comme le **`register`** mot clé, est utilisé comme indicateur pour le compilateur. Le compilateur utilise l’heuristique pour déterminer s’il doit incorporer une fonction particulière pour accélérer le code lors de la compilation pour la vitesse, ou s’il doit incorporer une fonction particulière pour réduire la taille du code lors de la compilation de l’espace. Le compilateur configure uniquement les très petites fonctions lors de la compilation de l’espace.

Dans certains cas, le compilateur n’incorpore pas une fonction particulière pour des raisons mécaniques. Pour obtenir la liste des raisons pour lesquelles le compilateur peut ne pas incorporer une fonction, consultez [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) .

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.
