---
title: Avertissement du compilateur (niveau 3) C4359
ms.date: 11/04/2016
f1_keywords:
- C4359
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
ms.openlocfilehash: 5cb65bab1f6490d1c39b20bfba2b3ecc68da664d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198690"
---
# <a name="compiler-warning-level-3-c4359"></a>Avertissement du compilateur (niveau 3) C4359

'type' : l’alignement réel (8) est supérieur à la valeur spécifiée dans __declspec (align ())

L’alignement spécifié pour un type est inférieur à l’alignement du type de l’un de ses membres de données.  Pour plus d’informations, consultez [Aligner](../../cpp/align-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4359.

```cpp
// C4359.cpp
// compile with: /W3 /c
struct __declspec(align(8)) C8 { __int64 i; };
struct __declspec(align(4)) C4  { C8 m8; };   // C4359
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK
struct __declspec(align(16)) C16  { C8 m8; };   // OK
```
