---
title: Avertissement du compilateur (niveau 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: d013990d0d56c028f48928d1b48c2e0a66b393af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221264"
---
# <a name="compiler-warning-level-1-c4692"></a>Avertissement du compilateur (niveau 1) C4692

'fonction' : la signature de membre non privée contient un type natif privé d'assembly 'type_natif'

Un type qui est visible en dehors de l’assembly contient une fonction membre dont la signature contient un type natif qui n’est pas visible en dehors de l’assembly. Par conséquent, la fonction membre ne doit pas être appelée si son type conteneur est instancié en dehors de l’assembly.

Pour plus d’informations, consultez [tapez visibilité](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4692.

```
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