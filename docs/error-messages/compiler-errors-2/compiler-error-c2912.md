---
description: 'En savoir plus sur : erreur du compilateur C2912'
title: Erreur du compilateur C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: 405c4acb5da6aa83e4b5d45e2297f1259a0d932e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270522"
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
