---
title: LNK4227 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b56617ee355654dfbb198252ea37cdb344950cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302108"
---
# <a name="linker-tools-warning-lnk4227"></a>Avertissement des outils Éditeur de liens LNK4227  
  
> Avertissement d’opération de métadonnées (*HRESULT*) : *message_avertissement*  
  
L’éditeur de liens a détecté des différences de métadonnées lors de la fusion :  
  
-   Un ou plusieurs assemblys référencés avec l’assembly en cours de génération.  
  
-   Un ou plusieurs fichiers de code source une compilation.  
  
Par exemple, LNK4227 peut être dû si vous avez deux fonctions globales portant le même nom mais les informations sur les paramètres déclarés différemment (autrement dit, les déclarations ne sont pas cohérentes dans tous les compilands). Utilisez ildasm.exe /TEXT /METADATA *object_file* sur chaque fichier .obj pour voir comment les types sont différents.  
  
LNK4227 est également utilisé pour signaler des problèmes qui proviennent d’un autre outil. Recherchez le message d’avertissement pour plus d’informations.  
  
Les problèmes de métadonnées doivent être corrigées pour résoudre l’avertissement.  
  
## <a name="example"></a>Exemple  
  
LNK4227 est généré lorsqu’un assembly référencé a été signé différemment de l’assembly qui y fait référence.  
  
L’exemple suivant génère l’erreur LNK4227 :  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 Et puis  
  
```cpp  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
## <a name="example"></a>Exemple  
  
LNK4227 peut également être générée lorsque des numéros de version dans un format incorrect sont passés aux attributs de l’assembly.  Le ' *' notation est spécifique à la `AssemblyVersionAttribute`.  Pour résoudre cet avertissement, utilisez uniquement les nombres dans les attributs de version autre que `AssemblyVersionAttribute`.  
  
L’exemple suivant génère l’erreur LNK4227 :  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```