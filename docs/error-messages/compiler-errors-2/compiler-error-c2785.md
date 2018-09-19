---
title: Erreur du compilateur C2785 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfae8a58d9c42c9ddc3ef7779fc86f7157ba41b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080855"
---
# <a name="compiler-error-c2785"></a>Erreur du compilateur C2785

'déclaration1' et 'déclaration2' ont des types de retournés différents

Le type de retour de la spécialisation de modèle de fonction est différent du type de retour du modèle de fonction principale.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Vérifiez toutes les spécialisations du modèle de fonction par souci de cohérence.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2785 :

```
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```