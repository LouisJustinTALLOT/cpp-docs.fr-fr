---
description: 'En savoir plus sur : erreur du compilateur C2434'
title: Erreur du compilateur C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: e24eb3fdf2ae60dadc270bed1bdda251acfc70a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189962"
---
# <a name="compiler-error-c2434"></a>Erreur du compilateur C2434

> '*symbol*' : un symbole déclaré avec __declspec (process) ne peut pas être initialisé dynamiquement en mode/clr : pure

## <a name="remarks"></a>Notes

Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Il n’est pas possible d’initialiser dynamiquement une variable par processus sous **/clr : pure**. Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [processus](../../cpp/process.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2434. Pour résoudre ce problème, utilisez des constantes pour initialiser des `process` variables.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
