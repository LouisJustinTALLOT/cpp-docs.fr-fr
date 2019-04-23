---
title: Avertissement du compilateur (niveau 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: bf51994c210bd751e0d29bec169dfc4366784486
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779425"
---
# <a name="compiler-warning-level-1-c4490"></a>Avertissement du compilateur (niveau 1) C4490

'override' : utilisation incorrecte du spécificateur de substitution ; 'fonction' ne correspond pas à une méthode de classe ref de base

Un spécificateur de substitution a été utilisé incorrectement. Par exemple, vous ne substituez pas une fonction d’interface, vous l’implémenter.

Pour plus d’informations, consultez [des spécificateurs de substitution](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4490 :.

```
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```