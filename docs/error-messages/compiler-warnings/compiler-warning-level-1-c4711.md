---
title: Compilateur avertissement (niveau 1) C4711 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4711
dev_langs:
- C++
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d184d5043dad1138f774ca7288a773bcc38c6d9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069941"
---
# <a name="compiler-warning-level-1-c4711"></a>Avertissement du compilateur (niveau 1) C4711

fonction 'fonction' sélectionnée pour expansion inline

Le compilateur applique la fonctionnalité inline sur la fonction donnée, bien qu’il n’a pas été marqué pour incorporation (inlining).

C4711 est activé si [/Ob2](../../build/reference/ob-inline-function-expansion.md) est spécifié.

La fonctionnalité inline est effectuée à la discrétion du compilateur. Cet avertissement possède un caractère informatif.

Cet avertissement est désactivé par défaut. Pour activer un avertissement, utilisez [#pragma warning](../../preprocessor/warning.md). Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.