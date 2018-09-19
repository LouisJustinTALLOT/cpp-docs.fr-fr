---
title: Erreur du compilateur C2821 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2821
dev_langs:
- C++
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52525062a07c7c55dd323109be87667d9e0847d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098223"
---
# <a name="compiler-error-c2821"></a>Erreur du compilateur C2821

premier paramètre formel de 'operator new' doit être 'unsigned int'

Le premier paramètre formel de le [opérateur new](../../standard-library/new-operators.md#op_new) doit être non signée `int`.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2821 :

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```