---
description: 'En savoir plus sur : erreur du compilateur C2951'
title: Erreur du compilateur C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: 7f3030764cdd36d40fbd78a8c3768c7dc1085c21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322105"
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
