---
title: Compilateur avertissement (niveau 1) C4537 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4537
dev_langs:
- C++
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 052d11d5bdf269d950abe1ef761adc055cbc6ce3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213361"
---
# <a name="compiler-warning-level-1-c4537"></a>Avertissement du compilateur (niveau 1) C4537

> «*objet*' : '*opérateur*' appliqué à un type non UDT

## <a name="remarks"></a>Notes

Une référence a été passée alors qu’un objet (type défini par l’utilisateur) était attendu. Une référence n’est pas un objet, mais le code assembleur inline n’est pas en mesure de faire la distinction. Le compilateur génère du code comme si *objet* était une instance.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4537 et montre comment la corriger :

```cpp
// C4537.cpp
// compile with: /W1 /c
// processor: x86
struct S {
    int member;
};

void f1(S &s) {
    __asm mov eax, s.member;   // C4537
    // try the following code instead
    // or, make the declaration "void f1(S s)"
    /*
    mov eax, s
    mov eax, [eax]s.member
    */
}
```