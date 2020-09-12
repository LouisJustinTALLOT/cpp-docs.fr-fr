---
title: Avertissement du compilateur (niveau 1) C4055
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 47883f60c3205125a8ee88b804c1d622b3ba0b41
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041027"
---
# <a name="compiler-warning-level-1-c4055"></a>Avertissement du compilateur (niveau 1) C4055

> '*conversion*' : du pointeur de données'*type1*'vers le pointeur fonction'*type2*'

## <a name="remarks"></a>Remarques

**Obsolète :** Cet avertissement n’est pas généré par Visual Studio 2017 et les versions ultérieures.

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
