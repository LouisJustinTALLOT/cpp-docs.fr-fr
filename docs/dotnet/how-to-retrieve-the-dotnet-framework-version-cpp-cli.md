---
title: 'Comment : récupérer la Version du .NET Framework (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework, version
- Version property, retrieving .NET Framework version
ms.assetid: fc786fbc-c915-4b15-bcad-0d68cf2c44bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f8bc471cda452bd387478a75dd047631c0359ed1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128769"
---
# <a name="how-to-retrieve-the-net-framework-version-ccli"></a>Comment : récupérer la version du .NET Framework (C++/CLI)
L’exemple de code suivant montre comment déterminer la version du .NET Framework actuellement installée avec le <xref:System.Environment.Version%2A> propriété, qui est un pointeur vers un <xref:System.Version> objet qui contient les informations de version.  
  
## <a name="example"></a>Exemple  
  
```  
// dotnet_ver.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   Version^ version = Environment::Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write(".NET Framework version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
            build, major, minor, revision);  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)