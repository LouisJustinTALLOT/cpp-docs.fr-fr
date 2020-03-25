---
title: Erreur du compilateur C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: d099c4a0f6e1ea77a25213e3873b8a0814e28dcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201993"
---
# <a name="compiler-error-c2821"></a>Erreur du compilateur C2821

le premier paramètre formel de’operator new’doit être’unsigned int'

Le premier paramètre formel de l' [opérateur New](../../standard-library/new-operators.md#op_new) doit être un `int`non signé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2821 :

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
