---
title: Erreur du compilateur C2678 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2678
dev_langs:
- C++
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2af18a98304cafc70441acda7ef0ebb1a827d88
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035347"
---
# <a name="compiler-error-c2678"></a>Erreur du compilateur C2678

'opérateur' binaire : aucun opérateur trouvé qui accepte un opérande de partie gauche de type 'type' (ou il n’existe pas de conversion acceptable)

Pour utiliser l'opérateur, vous devez le surcharger pour le type spécifié ou définir une conversion vers un type pour lequel l'opérateur est défini.

## <a name="example"></a>Exemple

L’erreur C2678 peut se produire quand l’opérande de partie gauche est qualifié const, mais que l’opérateur est défini pour accepter un argument non const.

L'exemple suivant génère l'erreur C2678 et montre comment la corriger :

```
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

## <a name="example"></a>Exemple

L'erreur C2678 peut également se produire si vous n'épinglez pas un membre natif avant d'appeler une fonction membre dessus.

L'exemple suivant génère l'erreur C2678 et montre comment la corriger :

```
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
