---
title: Erreur du compilateur C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 5c11133fbf28cfb98de1367955c00c899e8b1042
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214527"
---
# <a name="compiler-error-c3646"></a>Erreur du compilateur C3646

> 'specifier' : spécificateur de substitution inconnu

## <a name="remarks"></a>Notes

Le compilateur a trouvé un jeton à l’emplacement où il devait trouver un spécificateur de substitution, mais le jeton n’a pas été reconnu par le compilateur.

Par exemple, si le *spécificateur* non reconnu est **_NOEXCEPT**, remplacez-le par le mot clé **`noexcept`** .

Pour plus d’informations, consultez [spécificateurs de substitution](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3646 et montre un moyen de le corriger :

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```
