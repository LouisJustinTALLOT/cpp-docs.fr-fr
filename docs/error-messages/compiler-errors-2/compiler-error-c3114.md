---
title: Erreur du compilateur C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: c5a4feae5c8805a27c020b532fd58e0562e46b6b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775591"
---
# <a name="compiler-error-c3114"></a>Erreur du compilateur C3114

'argument' : argument d’attribut nommé non valide

Pour un membre de données de classe attribut soit un argument nommé valide, elle ne doit pas être marquée comme `static`, `const`, ou `literal`. Si une propriété, la propriété ne doit pas être `static` et doit avoir get et accesseurs set.

Pour plus d’informations, consultez [propriété](../../extensions/property-cpp-component-extensions.md) et [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3114.

```
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```