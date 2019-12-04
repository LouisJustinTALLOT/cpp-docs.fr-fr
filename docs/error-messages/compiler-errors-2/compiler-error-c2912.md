---
title: Erreur du compilateur C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: 254252bfd21aa28c87810f1e21b4864e2775a71b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761083"
---
# <a name="compiler-error-c2912"></a>Erreur du compilateur C2912

la spécialisation explicite 'déclaration' n'est pas une spécialisation d'un modèle de fonction

Vous ne pouvez pas spécialiser une fonction sans modèle.

L'exemple suivant génère l'erreur C2912 :

```cpp
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

Cette erreur sera également générée suite à la mise en conformité du compilateur dans Visual Studio .NET 2003 : pour chaque spécialisation explicite, vous devez choisir les paramètres de la spécialisation explicite, de sorte qu'ils correspondent aux paramètres du modèle principal.

```cpp
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```
