---
title: Erreur du compilateur C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: 872c3a66d4738c1a69990dffdbbc59cee9e90002
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395467"
---
# <a name="compiler-error-c2599"></a>Erreur du compilateur C2599

'enum' : une déclaration anticipée de type enum n’est pas autorisée

Le compilateur prend en charge n’est plus la déclaration anticipée d’une énumération managée.

Une déclaration anticipée d’un type enum n’est pas autorisée sous [/Za](../../build/reference/za-ze-disable-language-extensions.md).

L’exemple suivant génère l’erreur C2599 :

```
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