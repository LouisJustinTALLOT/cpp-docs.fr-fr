---
title: Avertissement du compilateur (niveau 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 73143e38b66471a41cc61f818f7618b9ddafcaa1
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966467"
---
# <a name="compiler-warning-level-1-c4376"></a>Avertissement du compilateur (niveau 1) C4376

le spécificateur d’accès’old_specifier : 'n’est plus pris en charge : utilisez’new_specifier : 'à la place

Pour plus d’informations sur la spécification de l’accessibilité des types et des membres dans les métadonnées, consultez [visibilité des types](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) et [visibilité des membres](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) dans [commentC++: définir et consommer des classes et des structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4376.

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```