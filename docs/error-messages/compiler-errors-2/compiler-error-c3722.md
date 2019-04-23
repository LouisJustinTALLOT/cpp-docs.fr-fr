---
title: Erreur du compilateur C3722
ms.date: 11/04/2016
f1_keywords:
- C3722
helpviewer_keywords:
- C3722
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
ms.openlocfilehash: e9a8c9cc26aeedf49484bb1f7357a76d0eb42bb5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778395"
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