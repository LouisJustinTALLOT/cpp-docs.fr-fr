---
title: Erreur du compilateur C3063 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3063
dev_langs:
- C++
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9adea484416b85f027693b59acb343d4ca19cf6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021640"
---
# <a name="compiler-error-c3063"></a>Erreur du compilateur C3063

l’opérateur 'opérateur' : tous les opérandes doivent avoir le même type d’énumération

Lorsque vous utilisez des opérateurs sur les énumérateurs, les deux opérandes doivent être du type énumération. Pour plus d’informations, consultez [Comment : définir et consommer des énumérateurs dans C++ / c++ / CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3063 et montre comment la corriger :

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```