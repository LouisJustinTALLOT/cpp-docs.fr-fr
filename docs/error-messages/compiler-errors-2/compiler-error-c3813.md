---
description: 'En savoir plus sur : erreur du compilateur C3813'
title: Erreur du compilateur C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: ae7157166083a4a86d9a5b170cbff3e127c87abb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180992"
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
