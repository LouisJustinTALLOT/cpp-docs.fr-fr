---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4710'
title: Avertissement du compilateur (niveau 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: b10a2add132335db48c49ae69740d04f792f126e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330585"
---
# <a name="compiler-warning-level-4-c4710"></a>Avertissement du compilateur (niveau 4) C4710

'fonction' : fonction non inline

La fonction donnée a été sélectionnée pour l’expansion Inline, mais le compilateur n’a pas effectué l’incorporation.

L’incorporation est effectuée à la discrétion du compilateur. Le **`inline`** mot clé, comme le **`register`** mot clé, est utilisé comme indicateur pour le compilateur. Le compilateur utilise l’heuristique pour déterminer s’il doit incorporer une fonction particulière pour accélérer le code lors de la compilation pour la vitesse, ou s’il doit incorporer une fonction particulière pour réduire la taille du code lors de la compilation de l’espace. Le compilateur configure uniquement les très petites fonctions lors de la compilation de l’espace.

Dans certains cas, le compilateur n’incorpore pas une fonction particulière pour des raisons mécaniques. Pour obtenir la liste des raisons pour lesquelles le compilateur peut ne pas incorporer une fonction, consultez [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) .

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.
