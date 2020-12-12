---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4190'
title: Avertissement du compilateur (niveau 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: ff27d5913e23fa1488816b3e2bb7284440c7577b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266583"
---
# <a name="compiler-warning-level-1-c4190"></a>Avertissement du compilateur (niveau 1) C4190

'identificateur1 'a une liaison C spécifiée, mais retourne UDT’identificateur2 'qui est incompatible avec C

Une fonction ou un pointeur vers une fonction a un UDT (type défini par l’utilisateur, qui est une classe, une structure, une énumération ou une Union) comme type de retour et `extern "C"` liaison. Cela est légal si :

- Tous les appels à cette fonction se produisent à partir de C++.

- La définition de la fonction est en C++.

## <a name="example"></a>Exemple

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
