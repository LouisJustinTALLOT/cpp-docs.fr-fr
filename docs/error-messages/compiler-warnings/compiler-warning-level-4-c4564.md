---
title: Compilateur avertissement (niveau 4) C4564 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea8d392251c8168490d7841ad590731b5a08e7f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031832"
---
# <a name="compiler-warning-level-4-c4564"></a>Avertissement du compilateur (niveau 4) C4564

la méthode 'méthode' de la classe 'class' définit un paramètre non pris en charge par défaut 'parameter'

Le compilateur a détecté une méthode avec un ou plusieurs paramètres avec valeurs par défaut. L’ou les valeurs par défaut pour les paramètres seront ignorée lors de la méthode est appelée ; spécifier explicitement des valeurs pour ces paramètres. Si vous ne spécifiez pas explicitement de valeurs pour ces paramètres, le compilateur C++ génère une erreur.

Soit la DLL ci-dessous créée avec Visual Basic, ce qui permet des paramètres par défaut sur les arguments de méthode :

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

Et l’exemple C++ suivant qui utilise le fichier .dll créés avec Visual Basic,

```
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