---
description: 'En savoir plus sur : erreur irrécupérable C1103'
title: Erreur irrécupérable C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: 7e49d4f4420fc202f54a580c194244d24a4d181c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144922"
---
# <a name="fatal-error-c1103"></a>Erreur irrécupérable C1103

erreur irrécupérable lors de l’importation de progid : 'message'

Le compilateur a détecté un problème d’importation d’une bibliothèque de types.  Par exemple, vous ne pouvez pas spécifier une bibliothèque de types avec progid et spécifier également `no_registry`.

Pour plus d’informations, consultez [#import directive](../../preprocessor/hash-import-directive-cpp.md).

L’exemple suivant génère l’erreur C1103 :

```cpp
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```
