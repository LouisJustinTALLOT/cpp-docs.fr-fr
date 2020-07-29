---
title: Transferts de contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: ef437d0a691ceff72485be1ff9584052f540031a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232181"
---
# <a name="transfers-of-control"></a>Transferts de contrôle

Vous pouvez utiliser l' **`goto`** instruction ou une **`case`** étiquette dans une **`switch`** instruction pour spécifier un programme qui se branche après un initialiseur. Ce code est conforme sauf si la déclaration qui contient l'initialiseur figure dans un bloc se trouvant lui-même dans le bloc dans lequel l'instruction de saut s'exécute.

L'exemple suivant montre une boucle qui déclare et initialise les objets `total`, `ch` et `i`. Il y a également une **`goto`** instruction erronée qui transfère le contrôle après un initialiseur.

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

Dans l’exemple précédent, l' **`goto`** instruction tente de transférer le contrôle au-delà de l’initialisation de `i` . Toutefois, si `i` était déclaré mais non initialisé, le transfert serait conforme.

Les objets `total` et `ch` , déclarés dans le bloc qui sert d' *instruction* de l' **`while`** instruction, sont détruits lors de la sortie de ce bloc à l’aide de l' **`break`** instruction.
