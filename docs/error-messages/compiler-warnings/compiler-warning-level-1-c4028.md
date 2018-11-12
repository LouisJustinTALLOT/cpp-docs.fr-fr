---
title: Compilateur avertissement (niveau 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490514"
---
# <a name="compiler-warning-level-1-c4028"></a>Compilateur avertissement (niveau 1) C4028

paramètre formel 'nombre' différent de la déclaration

Le type du paramètre formel ne correspond pas au paramètre correspondant de la déclaration. Le type dans la déclaration d’origine est utilisé.

Cet avertissement est uniquement valide pour le code source C.

## <a name="example"></a>Exemple

L’exemple suivant génère C4028.

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```