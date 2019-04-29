---
title: Erreur du compilateur C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: dbc7186edfce6cc12a38fb2fc1dda08ac4a181c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300724"
---
# <a name="compiler-error-c2951"></a>Erreur du compilateur C2951

déclarations de type sont uniquement autorisées à l’espace de noms global, ou portée de classe

Vous ne pouvez pas déclarer un générique ou la classe de modèle en dehors de global ou la portée espace de noms. Si vous effectuez vos déclarations génériques ou de modèle dans un fichier include, assurez-vous que le fichier include est dans une portée globale.

L’exemple suivant génère l’erreur C2951 :

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 peut également se produire lors de l’utilisation de génériques :

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```