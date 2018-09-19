---
title: Erreur du compilateur C2548 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2548
dev_langs:
- C++
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4fd5087613466ecb483ad4ec28018c9321453ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050501"
---
# <a name="compiler-error-c2548"></a>Erreur du compilateur C2548

'classe::membre' : paramètre par défaut pour le paramètre paramètre manquant

Il manque un paramètre dans la liste des paramètres par défaut. Si vous fournissez un paramètre par défaut n’importe où dans une liste de paramètres, vous devez définir les paramètres par défaut pour tous les paramètres suivants.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2548 :

```
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```