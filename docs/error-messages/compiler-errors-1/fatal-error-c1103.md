---
title: Erreur irrécupérable C1103 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9e48d827c58ebf41ce3cf3862cbfbeaa494cf76
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055947"
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