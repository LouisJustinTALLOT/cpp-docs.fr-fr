---
description: 'En savoir plus sur : erreur du compilateur C3269'
title: Erreur du compilateur C3269
ms.date: 11/04/2016
f1_keywords:
- C3269
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
ms.openlocfilehash: 041a0af061e4ddd1a691c396cdd15e86085124c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113696"
---
# <a name="compiler-error-c3269"></a>Erreur du compilateur C3269

'fonction' : une fonction membre d’un managé ou d’un WinRTtype ne peut pas être déclarée avec'... '

Les fonctions membres de classe managée ou WinRT ne peuvent pas déclarer des listes de paramètres de longueur variable.

L'exemple suivant génère l'erreur C3269 et montre comment la corriger :

```cpp
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
