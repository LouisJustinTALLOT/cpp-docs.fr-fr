---
description: 'En savoir plus sur : erreur du compilateur C2833'
title: Erreur du compilateur C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: 3c1bd2cc60478dc5868c74d4bfeac1d7d3a4d9a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194486"
---
# <a name="compiler-error-c2833"></a>Erreur du compilateur C2833

> 'operator *opérateur-Name*'n’est pas un opérateur ou un type reconnu

Le mot **`operator`** doit être suivi d’un *nom d’opérateur* que vous souhaitez substituer ou d’un type que vous souhaitez convertir.

Pour obtenir la liste des opérateurs que vous pouvez définir dans un type managé, consultez [opérateurs définis par l’utilisateur](../../dotnet/user-defined-operators-cpp-cli.md).

L’exemple suivant génère l’C2833 :

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
