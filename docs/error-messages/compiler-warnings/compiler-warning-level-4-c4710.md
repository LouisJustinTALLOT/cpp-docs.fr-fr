---
title: Compilateur avertissement (niveau 4) C4710 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6de17f7005db3834bfcfc93aff03f12f0293ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046093"
---
# <a name="compiler-warning-level-4-c4710"></a>Avertissement du compilateur (niveau 4) C4710

'fonction' : fonction non inline

La fonction donnée a été sélectionnée pour expansion inline, mais le compilateur n’a pas effectué l’incorporation (inlining).

La fonctionnalité inline est effectuée à la discrétion du compilateur. Le **inline** mot clé, comme le **inscrire** mot clé, est utilisé comme un indicateur pour le compilateur. Le compilateur utilise des heuristiques pour déterminer s’il doit être inline une fonction particulière pour accélérer le code lors de la compilation pour la vitesse, ou si elle doit incorporer une fonction particulière pour rendre le code plus petit lors de la compilation pour l’espace. Le compilateur crée les très petites fonctions inline uniquement lors de la compilation pour l’espace.

Dans certains cas, le compilateur n’incorpore pas une fonction particulière pour des raisons mécaniques. Consultez [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) pour obtenir la liste des raisons, le compilateur peut ne pas incorporer une fonction.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.