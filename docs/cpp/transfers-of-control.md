---
title: Transferts de contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: c9a46ccb1cf519080c5105855e41ecd3ebc23f77
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188049"
---
# <a name="transfers-of-control"></a>Transferts de contrôle

Vous pouvez utiliser l’instruction **goto** ou une étiquette **case** dans une instruction **switch** pour spécifier un programme qui rebranche un initialiseur. Ce code est conforme sauf si la déclaration qui contient l'initialiseur figure dans un bloc se trouvant lui-même dans le bloc dans lequel l'instruction de saut s'exécute.

L'exemple suivant montre une boucle qui déclare et initialise les objets `total`, `ch` et `i`. Il y a également une instruction **goto** erronée qui transfère le contrôle après un initialiseur.

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

Dans l’exemple précédent, l’instruction **goto** tente de transférer le contrôle au-delà de l’initialisation de `i`. Toutefois, si `i` était déclaré mais non initialisé, le transfert serait conforme.

Les objets `total` et `ch`, déclarés dans le bloc qui sert d' *instruction* de l’instruction **while** , sont détruits lors de la sortie de ce bloc à l’aide de l’instruction **break** .
