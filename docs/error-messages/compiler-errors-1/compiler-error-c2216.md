---
title: Erreur du compilateur C2216
ms.date: 11/04/2016
f1_keywords:
- C2216
helpviewer_keywords:
- C2216
ms.assetid: 250f6bdc-a5e1-495f-a1e8-6e8e7021ad9d
ms.openlocfilehash: 66c29c0e296a0eb13ef36ddb543b26af504b3230
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476802"
---
# <a name="compiler-error-c2216"></a>Erreur du compilateur C2216

'keyword1' ne peut pas s’utiliser avec 'keyword2'

Deux mots clés qui s’excluent mutuellement ont été utilisés ensemble.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2216.

```
// C2216.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   static int staticConst2 = 10;   // C2216
};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2216.

```
// C2216b.cpp
// compile with: /clr /c
public ref class X {
   extern property int i { int get(); }   // C2216 extern not allowed on property
   typedef property int i2;   // C2216 typedef not allowed on property
};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2216.

```
// C2216c.cpp
// compile with: /clr /c
public interface struct I {
   double f();
   double g();
   double h();
};

public ref struct R : I {
   virtual double f() new override { return 0.0; }   // C2216
   virtual double g() new { return 0.0; }   // OK
   virtual double h() override { return 0.0; }   // OK
};
```