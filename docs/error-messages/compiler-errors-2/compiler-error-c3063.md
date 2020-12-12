---
description: 'En savoir plus sur : erreur du compilateur C3063'
title: Erreur du compilateur C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 304359e34b6cbae07d2f901db02c6e5ed04e373c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281702"
---
# <a name="compiler-error-c3063"></a>Erreur du compilateur C3063

opérateur’opérateur' : tous les opérandes doivent avoir le même type d’énumération

Lors de l’utilisation d’opérateurs sur les énumérateurs, les deux opérandes doivent être du type énumération. Pour plus d’informations, consultez [Comment : définir et consommer des énumérations en C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3063 et montre comment la corriger :

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
