---
title: Erreur du compilateur C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: fcf2bbb01f2aac668ff52884a6ccfb36c66aa89d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445837"
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