---
title: Avertissement du compilateur (niveau 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: 0f8e66982192f8af6498c9151d32a44226e0560a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487774"
---
# <a name="compiler-warning-level-4-c4710"></a>Avertissement du compilateur (niveau 4) C4710

'fonction' : fonction non inline

La fonction donnée a été sélectionnée pour expansion inline, mais le compilateur n’a pas effectué l’incorporation (inlining).

La fonctionnalité inline est effectuée à la discrétion du compilateur. Le **inline** mot clé, comme le **inscrire** mot clé, est utilisé comme un indicateur pour le compilateur. Le compilateur utilise des heuristiques pour déterminer s’il doit être inline une fonction particulière pour accélérer le code lors de la compilation pour la vitesse, ou si elle doit incorporer une fonction particulière pour rendre le code plus petit lors de la compilation pour l’espace. Le compilateur crée les très petites fonctions inline uniquement lors de la compilation pour l’espace.

Dans certains cas, le compilateur n’incorpore pas une fonction particulière pour des raisons mécaniques. Consultez [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) pour obtenir la liste des raisons, le compilateur peut ne pas incorporer une fonction.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.