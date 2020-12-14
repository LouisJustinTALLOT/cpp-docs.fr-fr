---
description: 'En savoir plus sur : erreur du compilateur C3824'
title: Erreur du compilateur C3824
ms.date: 11/04/2016
f1_keywords:
- C3824
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
ms.openlocfilehash: 5560ee8c845c57ae14de11b503ebc724dbcbb0dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249358"
---
# <a name="compiler-error-c3824"></a>Erreur du compilateur C3824

'membre' : ce type ne peut pas apparaître dans ce contexte (paramètre de fonction, type de retour ou membre statique)

Les pointeurs épinglés ne peuvent pas être des paramètres de fonction, des types de retour ou être déclarés **`static`** .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3824 :

```cpp
// C3824a.cpp
// compile with: /clr /c
void func() {
   static pin_ptr<int> a; // C3824
   pin_ptr<int> b; // OK
}
```
