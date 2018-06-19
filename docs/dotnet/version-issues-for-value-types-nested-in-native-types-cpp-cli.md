---
title: Problèmes de version pour les Types valeur imbriqués dans les Types natifs (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c4f2598594930f49c1217c937c9142b3f84a47e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168839"
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>Problèmes de version pour les types valeur imbriqués dans les types natifs (C++/CLI)
Envisagez d’un composant d’assembly signé (nom fort) utilisé pour générer un assembly client. Le composant contient un type valeur qui est utilisé dans le client en tant que le type d’un membre d’une union native, une classe ou un tableau. Si une version future du composant modifie la taille ou la disposition du type valeur, le client doit être recompilé.  
  
 Créez un fichier de clé avec [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant est le composant.  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple est le client :  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>Commentaires  
 Toutefois, si vous ajoutez un autre membre `struct S` dans nested_value_types.cpp, (par exemple, `double d;`) et recompilez le composant sans avoir à recompiler le client, le résultat est une exception non gérée (de type <xref:System.IO.FileLoadException?displayProperty=fullName>).  
  
## <a name="see-also"></a>Voir aussi  
 [Types managés (C++-CLI)](../dotnet/managed-types-cpp-cli.md)