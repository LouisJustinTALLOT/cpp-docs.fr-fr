---
description: 'En savoir plus sur : erreur du compilateur C3868'
title: Erreur du compilateur C3868
ms.date: 11/04/2016
f1_keywords:
- C3868
helpviewer_keywords:
- C3868
ms.assetid: f0e45c2a-2149-4885-a03b-0d230069f03a
ms.openlocfilehash: c71a5321b99e5852a2dc7267dd098bfec08c5ad2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222812"
---
# <a name="compiler-error-c3868"></a>Erreur du compilateur C3868

'type' : les contraintes du paramètre générique’paramètre’diffèrent de celles de la déclaration

Plusieurs déclarations doivent avoir les mêmes contraintes génériques.  Pour plus d’informations, consultez [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3868.

```cpp
// C3868.cpp
// compile with: /clr /c
interface struct I1;

generic <typename T> ref struct MyStruct;
generic <typename U> where U : I1 ref struct MyStruct;   // C3868

// OK
generic <typename T> ref struct MyStruct2;
generic <typename U> ref struct MyStruct2;

generic <typename T> where T : I1 ref struct MyStruct3;
generic <typename U> where U : I1 ref struct MyStruct3;
```
