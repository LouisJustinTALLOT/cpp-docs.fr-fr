---
description: 'En savoir plus sur : erreur irrécupérable C1104'
title: Erreur irrécupérable C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: 4cc9c46850e864d0de867c99aabb635a5fcd3f9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144899"
---
# <a name="fatal-error-c1104"></a>Erreur irrécupérable C1104

erreur irrécupérable lors de l’importation de libid : 'message'

Le compilateur a détecté un problème d’importation d’une bibliothèque de types.  Par exemple, vous ne pouvez pas spécifier une bibliothèque de types avec libid et spécifier également `no_registry`.

Pour plus d’informations, consultez [#import directive](../../preprocessor/hash-import-directive-cpp.md).

L’exemple suivant génère l’erreur C1104 :

```cpp
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```
