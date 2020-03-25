---
title: Erreur du compilateur C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: c16ce501e25040a7ac7672a9ea131b4fe89570f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165611"
---
# <a name="compiler-error-c3813"></a>Erreur du compilateur C3813

une déclaration de propriété ne peut figurer qu'au sein d'une définition de type managé ou WinRT

Une [propriété](../../dotnet/how-to-use-properties-in-cpp-cli.md) ne peut être déclarée que dans un type managé ou Windows Runtime. Les types natifs ne prennent pas en charge le mot clé `property`.

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
