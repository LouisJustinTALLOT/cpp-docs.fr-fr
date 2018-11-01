---
title: Avertissement du compilateur (niveau 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601316"
---
# <a name="compiler-warning-level-1-c4055"></a>Avertissement du compilateur (niveau 1) C4055

> «*conversion*' : du pointeur donnée '*type1*'en pointeur de fonction'*type2*»

## <a name="remarks"></a>Notes

**Obsolète :** cet avertissement n’est pas généré par Visual Studio 2017 et versions ultérieures.

Un pointeur donnée est converti (peut-être de façon incorrecte) en un pointeur fonction. Il s’agit d’un avertissement de niveau 1 sous /Za et d’un avertissement de niveau 4 sous /Ze.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4055 :

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

Sous /Ze, il s’agit d’un avertissement de niveau 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
