---
title: Erreur du compilateur C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 13a3ebeb6e7783687abc73cd0dcc018abe827809
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200471"
---
# <a name="compiler-error-c3646"></a>Erreur du compilateur C3646

> 'specifier' : spécificateur de substitution inconnu

## <a name="remarks"></a>Notes

Le compilateur a trouvé un jeton à l’emplacement où il devait trouver un spécificateur de substitution, mais le jeton n’a pas été reconnu par le compilateur.

Par exemple, si le *spécificateur* non reconnu est **_NOEXCEPT**, remplacez-le par le mot clé **noexcept**.

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
