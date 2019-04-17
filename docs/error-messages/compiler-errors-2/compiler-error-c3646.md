---
title: Erreur du compilateur C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769028"
---
# <a name="compiler-error-c3646"></a>Erreur du compilateur C3646

> 'spécificateur' : spécificateur de substitution inconnu

## <a name="remarks"></a>Notes

Le compilateur a détecté un jeton à la position où il devrait y avoir un spécificateur de substitution, mais le jeton n’a pas été reconnu par le compilateur.

Par exemple, si le non reconnu *spécificateur* est **_NOEXCEPT**, remplacez-le par le mot clé **noexcept**.

Pour plus d’informations, consultez [des spécificateurs de substitution](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3646 et illustre une méthode permettant de résoudre le problème :

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```