---
title: Erreur du compilateur C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166332"
---
# <a name="compiler-error-c2434"></a>Erreur du compilateur C2434

> «*symbole*' : un symbole déclaré avec __declspec (Process) ne peut pas être initialisé dynamiquement en/clr : pur mode

## <a name="remarks"></a>Notes

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Il n’est pas possible d’initialiser dynamiquement une variable par processus sous **/CLR : pure**. Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [processus](../../cpp/process.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C2434. Pour résoudre ce problème, utilisez des constantes pour initialiser `process` variables.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```