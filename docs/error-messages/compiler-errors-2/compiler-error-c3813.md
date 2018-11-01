---
title: Erreur du compilateur C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470588"
---
# <a name="compiler-error-c3813"></a>Erreur du compilateur C3813

une déclaration de propriété ne peut figurer qu'au sein d'une définition de type managé ou WinRT

Un [propriété](../../dotnet/how-to-use-properties-in-cpp-cli.md) peut uniquement être déclaré dans managé ou Windows Runtime type. Les types natifs ne prennent pas en charge le mot clé `property`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3813 et montre comment la corriger :

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```