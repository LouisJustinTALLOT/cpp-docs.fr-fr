---
title: Erreur du compilateur C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e854764dc3f8d3ede79965302b62055b91df0a4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165624"
---
# <a name="compiler-error-c3808"></a>Erreur du compilateur C3808

> '*type*' : une classe avec l’attribut ComImport ne peut pas définir le membre'*member*', seules les fonctions abstract ou dllimport sont autorisées

## <a name="remarks"></a>Notes

Un type dérivé de <xref:System.Runtime.InteropServices.ComImportAttribute> ne peut pas définir de *membre*.

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3808.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```
