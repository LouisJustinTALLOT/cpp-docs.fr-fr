---
title: Erreur irrécupérable C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: b6253af9fcf400321fb58d4d8a6d7aacf461b926
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577643"
---
# <a name="fatal-error-c1103"></a>Erreur irrécupérable C1103

erreur irrécupérable lors de l’importation de progid : 'message'

Le compilateur a détecté un problème d’importation d’une bibliothèque de types.  Par exemple, vous ne pouvez pas spécifier une bibliothèque de types avec progid et spécifier également `no_registry`.

Pour plus d’informations, consultez [Directive #import](../../preprocessor/hash-import-directive-cpp.md).

L’exemple suivant génère l’erreur C1103 :

```
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```