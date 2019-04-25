---
title: Avertissement du compilateur (niveau 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 2f97be4e1aaa5143df685cb95935d350e6f02534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161080"
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