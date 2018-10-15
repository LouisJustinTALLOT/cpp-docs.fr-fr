---
title: 'Comment : déclarer et utiliser des pointeurs intérieurs et des tableaux managés (C++ / c++ / CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, interior
- arrays [C++], managed
ms.assetid: e61a2c09-a7d0-4867-91ea-6b8788a01079
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0c34b43451f8e62583450998efa8e74000807b4
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328114"
---
# <a name="how-to-declare-and-use-interior-pointers-and-managed-arrays-ccli"></a>Comment : déclarer et utiliser des pointeurs intérieurs et des tableaux managés (C++/CLI)

C++ suivant / c++ / CLI montre comment vous pouvez déclarer et utiliser un pointeur intérieur vers un tableau.

> [!IMPORTANT]
> Cette fonctionnalité de langage est pris en charge par le `/clr` option du compilateur, mais pas par le `/ZW` option du compilateur.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// interior_ptr_arrays.cpp
// compile with: /clr
#define SIZE 10

int main() {
   // declare the array
   array<int>^ arr = gcnew array<int>(SIZE);

   // initialize the array
   for (int i = 0 ; i < SIZE ; i++)  
      arr[i] = i + 1;

   // create an interior pointer into the array
   interior_ptr<int> ipi = &arr[0];

   System::Console::WriteLine("1st element in arr holds: {0}", arr[0]);
   System::Console::WriteLine("ipi points to memory address whose value is: {0}", *ipi);

   ipi++;
   System::Console::WriteLine("after incrementing ipi, it points to memory address whose value is: {0}", *ipi);
}
```

```Output
1st element in arr holds: 1
ipi points to memory address whose value is: 1
after incrementing ipi, it points to memory address whose value is: 2
```

## <a name="see-also"></a>Voir aussi

[interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)