---
title: Conversions standard et boxing implicite
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: b771f9e9c1dc05fcd2ead19f5202747d7c475a09
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774449"
---
# <a name="standard-conversions-and-implicit-boxing"></a>Conversions standard et boxing implicite

Une conversion standard sera choisie par le compilateur via une conversion qui nécessite une conversion boxing.

## <a name="example"></a>Exemple

```
// clr_implicit_boxing_Std_conversion.cpp
// compile with: /clr
int f3(int ^ i) {   // requires boxing
   return 1;
}

int f3(char c) {   // no boxing required, standard conversion
   return 2;
}

int main() {
   int i = 5;
   System::Console::WriteLine(f3(i));
}
```

```Output
2
```

## <a name="see-also"></a>Voir aussi

[Boxing](../extensions/boxing-cpp-component-extensions.md)
