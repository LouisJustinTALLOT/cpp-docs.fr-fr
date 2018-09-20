---
title: 'Comment : encapsuler une classe Native pour une utilisation par c# | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++], Visual C# and
- classes [C++], Visual C# and
ms.assetid: 988819ae-cc6a-4453-8ff5-be369210d962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1952f48f9866f3ddefa203a2f5495d93e68ee577
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420372"
---
# <a name="how-to-wrap-native-class-for-use-by-c"></a>Comment : inclure une classe native dans un wrapper pour une utilisation par C#

Cet exemple montre comment encapsuler une classe C++ native, donc il peut être utilisé dans du code créé en c# ou autre langage .NET.

## <a name="example"></a>Exemple

```
// wrap_native_class_for_mgd_consumption.cpp
// compile with: /clr /LD
#include <windows.h>
#include <vcclr.h>
#using <System.dll>

using namespace System;

class UnmanagedClass {
public:
   LPCWSTR GetPropertyA() { return 0; }
   void MethodB( LPCWSTR ) {}
};

public ref class ManagedClass {
public:
   // Allocate the native object on the C++ Heap via a constructor
   ManagedClass() : m_Impl( new UnmanagedClass ) {}

   // Deallocate the native object on a destructor
   ~ManagedClass() {
      delete m_Impl;
   }

protected:
   // Deallocate the native object on the finalizer just in case no destructor is called
   !ManagedClass() {
      delete m_Impl;
   }

public:
   property String ^  get_PropertyA {
      String ^ get() {
         return gcnew String( m_Impl->GetPropertyA());
      }
   }

   void MethodB( String ^ theString ) {
      pin_ptr<const WCHAR> str = PtrToStringChars(theString);
      m_Impl->MethodB(str);
   }

private:
   UnmanagedClass * m_Impl;
};
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)