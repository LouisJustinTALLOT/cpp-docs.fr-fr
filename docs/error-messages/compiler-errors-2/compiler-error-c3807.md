---
description: 'En savoir plus sur : erreur du compilateur C3807'
title: Erreur du compilateur C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: ffa8b52b13ae7245b62cd5aa8d7fec9285754b73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260096"
---
# <a name="compiler-error-c3807"></a>Erreur du compilateur C3807

'type' : une classe avec l’attribut ComImport ne peut pas dériver de’type2 ', seule l’implémentation d’interface est autorisée

Un type dérivé de <xref:System.Runtime.InteropServices.ComImportAttribute> ne peut implémenter qu’une interface.

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
