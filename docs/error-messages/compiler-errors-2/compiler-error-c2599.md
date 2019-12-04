---
title: Erreur du compilateur C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: c722335660653df7e533ec25d4708f42c16846ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740765"
---
# <a name="compiler-error-c2599"></a>Erreur du compilateur C2599

'enum' : la déclaration anticipée d’un type enum n’est pas autorisée

Le compilateur ne prend plus en charge la déclaration anticipée d’une énumération managée.

La déclaration anticipée d’un type enum n’est pas autorisée sous [/za](../../build/reference/za-ze-disable-language-extensions.md).

L’exemple suivant génère l’C2599 :

```cpp
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```
