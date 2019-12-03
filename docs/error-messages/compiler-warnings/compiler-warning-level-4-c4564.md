---
title: Avertissement du compilateur (niveau 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: f5db6bf366c86a716be33539feb0085ac03a9647
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683164"
---
# <a name="compiler-warning-level-4-c4564"></a>Avertissement du compilateur (niveau 4) C4564

la méthode’Method’de la classe’class’définit le paramètre par défaut non pris en charge’parameter'

Le compilateur a détecté une méthode avec un ou plusieurs paramètres avec des valeurs par défaut. La ou les valeurs par défaut des paramètres seront ignorées lorsque la méthode est appelée ; spécifiez explicitement des valeurs pour ces paramètres. Si vous ne spécifiez pas explicitement de valeurs pour ces paramètres C++ , le compilateur génère une erreur.

À partir de la dll suivante créée avec Visual Basic, qui autorise les paramètres par défaut sur les arguments de méthode :

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

Et l’exemple C++ suivant qui utilise le fichier. dll créé avec Visual Basic,

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```