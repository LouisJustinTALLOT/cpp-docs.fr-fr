---
title: Erreur du compilateur C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404212"
---
# <a name="compiler-error-c3063"></a>Erreur du compilateur C3063

l’opérateur 'opérateur' : tous les opérandes doivent avoir le même type d’énumération

Lorsque vous utilisez des opérateurs sur les énumérateurs, les deux opérandes doivent être du type énumération. Pour plus d'informations, voir [Procédure : Définir et consommer des énumérateurs dans C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

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