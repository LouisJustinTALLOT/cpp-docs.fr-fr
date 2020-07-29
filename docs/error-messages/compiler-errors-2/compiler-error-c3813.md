---
title: Erreur du compilateur C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 88aca16363af22a6671832264889b1a26e43d460
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223367"
---
# <a name="compiler-error-c3813"></a>Erreur du compilateur C3813

une déclaration de propriété ne peut figurer qu'au sein d'une définition de type managé ou WinRT

Une [propriété](../../dotnet/how-to-use-properties-in-cpp-cli.md) ne peut être déclarée que dans un type managé ou Windows Runtime. Les types natifs ne prennent pas en charge le **`property`** mot clé.

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
