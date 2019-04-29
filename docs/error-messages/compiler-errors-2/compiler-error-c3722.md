---
title: Erreur du compilateur C3722
ms.date: 11/04/2016
f1_keywords:
- C3722
helpviewer_keywords:
- C3722
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
ms.openlocfilehash: e9a8c9cc26aeedf49484bb1f7357a76d0eb42bb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328255"
---
# <a name="compiler-error-c3722"></a>Erreur du compilateur C3722

un événement générique n’est pas autorisé.

Le compilateur autorise uniquement les fonctions, structures et classes génériques.  Pour plus d’informations, consultez la page [Génériques](../../extensions/generics-cpp-component-extensions.md).

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