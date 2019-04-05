---
title: Erreur du compilateur C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781404"
---
# <a name="compiler-error-c3612"></a>Erreur du compilateur C3612

'type' : une classe sealed ne peut pas être abstract

Types définis à l’aide de `value` sont scellées par défaut, et une classe est abstraite, sauf si elle implémente toutes les méthodes de sa base. Une classe abstraite sealed ne peut ni être une classe de base ni être instanciée.

Pour plus d’informations, consultez [les Classes et Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3612 :

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```