---
title: Erreur du compilateur C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755978"
---
# <a name="compiler-error-c2951"></a>Erreur du compilateur C2951

les déclarations de type sont autorisées uniquement au niveau global, de l’espace de noms ou de la portée de classe

Vous ne pouvez pas déclarer une classe générique ou de modèle en dehors de la portée globale ou de l’espace de noms. Si vous effectuez vos déclarations génériques ou de modèle dans un fichier include, assurez-vous que le fichier include se trouve au niveau de la portée globale.

L’exemple suivant génère l’C2951 :

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
