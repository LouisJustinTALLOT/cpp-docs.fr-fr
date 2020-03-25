---
title: Avertissement du compilateur (niveau 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: ed46620605a8d5d60acee2db37c5cfc1348b5f4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164467"
---
# <a name="compiler-warning-level-1-c4028"></a>Avertissement du compilateur (niveau 1) C4028

paramètre formel’nombre’différent de la déclaration

Le type du paramètre formel ne correspond pas au paramètre correspondant dans la déclaration. Le type dans la déclaration d’origine est utilisé.

Cet avertissement est valide uniquement pour le code source C.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4028.

```c
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```
