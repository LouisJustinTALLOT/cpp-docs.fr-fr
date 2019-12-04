---
title: Erreur du compilateur C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: a4b33782c0a1e5abb811210c9e7a28da7040c805
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755263"
---
# <a name="compiler-error-c3807"></a>Erreur du compilateur C3807

'type' : une classe avec l’attribut ComImport ne peut pas dériver de’type2 ', seule l’implémentation d’interface est autorisée

Un type dérivé de <xref:System.Runtime.InteropServices.ComImportAttribute> peut implémenter uniquement une interface.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3807.

```cpp
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```
