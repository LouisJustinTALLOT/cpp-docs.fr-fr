---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4706'
title: Avertissement du compilateur (niveau 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: ca614d0ca55dcfa22ec31df78ebe2be904ffd9e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208526"
---
# <a name="compiler-warning-level-4-c4706"></a>Avertissement du compilateur (niveau 4) C4706

assignation dans une expression conditionnelle

La valeur de test dans une expression conditionnelle était le résultat d’une assignation.

Une assignation a une valeur (la valeur située à gauche de l’assignation) qui peut être utilisée légalement dans une autre expression, y compris une expression de test.

L’exemple suivant génère l’C4706 :

```cpp
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

L’avertissement se produit même si vous doublez les parenthèses autour de la condition de test :

```cpp
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Si vous avez l’intention de tester une relation et de ne pas effectuer d’affectation, utilisez l' `==` opérateur. Par exemple, la ligne suivante teste si a et b sont égaux :

```cpp
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Si vous envisagez de faire de la valeur de test le résultat d’une assignation, effectuez un test pour vérifier que l’assignation est différente de zéro ou non null. Par exemple, le code suivant ne génère pas cet avertissement :

```cpp
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```
