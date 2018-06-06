---
title: Erreur du compilateur C2434 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45f9ccdef84713883c53dab0e7caf3b1519628de
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704225"
---
# <a name="compiler-error-c2434"></a>Erreur du compilateur C2434

> '*symbole*' : un symbole déclaré avec __declspec (Process) ne peut pas être initialisé dynamiquement en/clr : pure en mode

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