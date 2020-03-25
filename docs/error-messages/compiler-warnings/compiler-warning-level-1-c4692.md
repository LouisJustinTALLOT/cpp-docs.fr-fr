---
title: Avertissement du compilateur (niveau 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: 0e8e951d5ea50cc755d26616cf23e48c27b2ca84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175361"
---
# <a name="compiler-warning-level-1-c4692"></a>Avertissement du compilateur (niveau 1) C4692

'fonction' : la signature de membre non privée contient un type natif privé d'assembly 'type_natif'

Un type qui est visible à l’extérieur de l’assembly contient une fonction membre dont la signature contient un type natif qui n’est pas visible à l’extérieur de l’assembly. Par conséquent, la fonction membre ne doit pas être appelée si son type conteneur est instancié à l’extérieur de l’assembly.

Pour plus d’informations, consultez [type Visibility](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4692.

```cpp
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```
