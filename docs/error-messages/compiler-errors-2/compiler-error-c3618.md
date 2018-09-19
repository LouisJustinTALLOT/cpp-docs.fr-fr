---
title: Erreur du compilateur C3618 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3618
dev_langs:
- C++
helpviewer_keywords:
- C3618
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28371c211238aaabdadcb6c2b21284beb672dbe9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111633"
---
# <a name="compiler-error-c3618"></a>Erreur du compilateur C3618

'fonction' : Impossible de définir une méthode marquée DllImport

Une méthode marquée avec <xref:System.Runtime.InteropServices.DllImportAttribute> est défini dans le texte spécifié. DLL.

## <a name="example"></a>Exemple

L’exemple suivant génère C3618.

```
// C3618.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED
void Func();

void Func() {}   // C3618, remove this function definition to resolve
```