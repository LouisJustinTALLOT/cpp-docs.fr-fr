---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4537'
title: Avertissement du compilateur (niveau 1) C4537
ms.date: 08/27/2018
f1_keywords:
- C4537
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
ms.openlocfilehash: 39219361445832f51160311733c77d3becd8bc5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294767"
---
# <a name="compiler-warning-level-1-c4537"></a>Avertissement du compilateur (niveau 1) C4537

> '*Object*' : '*Operator*'appliqué à un type non UDT

## <a name="remarks"></a>Notes

Une référence a été passée là où un objet (type défini par l’utilisateur) était attendu. Une référence n’est pas un objet, mais le code assembleur inline n’est pas en mesure de faire la distinction. Le compilateur génère du code comme si l' *objet* était une instance.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4537 et montre comment la corriger :

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
