---
description: 'En savoir plus sur : erreur du compilateur C2811'
title: Erreur du compilateur C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 02b4770b08bdfc9ee15386874ebba2265716536d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194850"
---
# <a name="compiler-error-c2811"></a>Erreur du compilateur C2811

'type1 ' : ne peut pas hériter de’type2 ', une classe ref ne peut hériter que d’une classe ref ou d’une classe interface

Vous avez tenté d’utiliser une classe non managée comme classe de base pour une classe managée.

L’exemple suivant génère l’C2811 :

```cpp
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```
