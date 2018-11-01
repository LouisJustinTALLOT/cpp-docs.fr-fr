---
title: Erreur du compilateur C3722
ms.date: 11/04/2016
f1_keywords:
- C3722
helpviewer_keywords:
- C3722
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
ms.openlocfilehash: d3c721490e0af32d91fcc51412e3c02b6a2d7f67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450997"
---
# <a name="compiler-error-c3722"></a>Erreur du compilateur C3722

un événement générique n’est pas autorisé.

Le compilateur autorise uniquement les fonctions, structures et classes génériques.  Pour plus d’informations, consultez la page [Génériques](../../windows/generics-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3722 :

```
// C3722.cpp
// compile with: /clr
generic <typename T>
public delegate void MyEventHandler(System::Object^ sender, System::EventArgs^ e, T optional);

generic <class T>
public ref struct MyButton {
   generic<typename U>
   event MyEventHandler<U>^ Click;   // C3722
};
```