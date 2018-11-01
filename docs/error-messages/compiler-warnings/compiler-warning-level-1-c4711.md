---
title: Avertissement du compilateur (niveau 1) C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: c10b19b39fcb40527c9e9276f47ecff42ca5a643
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600094"
---
# <a name="compiler-warning-level-1-c4711"></a>Avertissement du compilateur (niveau 1) C4711

fonction 'fonction' sélectionnée pour expansion inline

Le compilateur applique la fonctionnalité inline sur la fonction donnée, bien qu’il n’a pas été marqué pour incorporation (inlining).

C4711 est activé si [/Ob2](../../build/reference/ob-inline-function-expansion.md) est spécifié.

La fonctionnalité inline est effectuée à la discrétion du compilateur. Cet avertissement possède un caractère informatif.

Cet avertissement est désactivé par défaut. Pour activer un avertissement, utilisez [#pragma warning](../../preprocessor/warning.md). Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.