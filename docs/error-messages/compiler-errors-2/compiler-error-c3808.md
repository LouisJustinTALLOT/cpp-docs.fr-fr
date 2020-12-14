---
description: 'En savoir plus sur : erreur du compilateur C3808'
title: Erreur du compilateur C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e5d31e884de0b04caba7c52e8d6abc01b3d21a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315151"
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
