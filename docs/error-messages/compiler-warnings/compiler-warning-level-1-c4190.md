---
title: Avertissement du compilateur (niveau 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199873"
---
# <a name="compiler-warning-level-1-c4190"></a>Avertissement du compilateur (niveau 1) C4190

'identificateur1 'a une liaison C spécifiée, mais retourne UDT’identificateur2 'qui est incompatible avec C

Une fonction ou un pointeur vers une fonction a un UDT (type défini par l’utilisateur, qui est une classe, une structure, une énumération ou une Union) en tant que type de retour et `extern` liaison « C ». Cela est légal si :

- Tous les appels à cette fonction se C++produisent à partir de.

- La définition de la fonction se trouve C++dans.

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
