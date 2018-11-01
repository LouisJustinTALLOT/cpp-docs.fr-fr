---
title: auto_gcroot::attach
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_gcroot.attach
- auto_gcroot::attach
- msclr::auto_gcroot::attach
- msclr.auto_gcroot.attach
helpviewer_keywords:
- auto_gcroot::attach
ms.assetid: 996ede65-bcb5-41f2-bfbf-507f8a578241
ms.openlocfilehash: b4c2b3d2c9eb8554b342fb459946aa898ee4a406
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516101"
---
# <a name="autogcrootattach"></a>auto_gcroot::attach

Attacher `auto_gcroot` à un objet.

## <a name="syntax"></a>Syntaxe

```cpp
auto_gcroot<_element_type> & attach(
   _element_type _right
);
auto_gcroot<_element_type> & attach(
   auto_gcroot<_element_type> & _right
);
template<typename _other_type>
auto_gcroot<_element_type> & attach(
   auto_gcroot<_other_type> & _right
);
```

#### <a name="parameters"></a>Paramètres

*à d_roite*<br/>
L’objet à attacher, ou un `auto_gcroot` contenant l’objet à attacher.

## <a name="return-value"></a>Valeur de retour

`auto_gcroot` actuel.

## <a name="remarks"></a>Notes

Si `_right` est un `auto_gcroot`, il libère la propriété de son objet avant de l’objet est attaché au cours `auto_gcroot`.

## <a name="example"></a>Exemple

```cpp
// msl_auto_gcroot_attach.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "in ClassA constructor:" + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor:" + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String ^ s) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main() {
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );
   a->PrintHello();
   a.attach( gcnew ClassA( "second" ) ); // attach same type
   a->PrintHello();
   ClassA^ ha = gcnew ClassA( "third" );
   a.attach( ha ); // attach raw handle
   a->PrintHello();
   auto_gcroot<ClassB^> b( gcnew ClassB("fourth") );
   b->PrintHello();
   a.attach( b ); // attach derived type
   a->PrintHello();
}
```

```Output
in ClassA constructor:first
Hello from first A!
in ClassA constructor:second
in ClassA destructor:first
Hello from second A!
in ClassA constructor:third
in ClassA destructor:second
Hello from third A!
in ClassA constructor:fourth
Hello from fourth B!
in ClassA destructor:third
Hello from fourth A!
in ClassA destructor:fourth
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[auto_gcroot Members](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::operator=](../dotnet/auto-gcroot-operator-assign.md)<br/>
[auto_gcroot::release](../dotnet/auto-gcroot-release.md)