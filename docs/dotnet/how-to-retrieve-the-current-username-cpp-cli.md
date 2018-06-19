---
title: 'Comment : récupérer le nom d’utilisateur en cours (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- current user names
- user names, retrieving
- UserName string
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48b48b2d6ad84a85ca100c45a87f5d5037de684f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127820"
---
# <a name="how-to-retrieve-the-current-username-ccli"></a>Comment : récupérer le nom d'utilisateur actuel (C++/CLI)
L’exemple de code suivant illustre la récupération du nom d’utilisateur en cours (le nom de l’utilisateur connecté à Windows). Le nom est stocké dans le <xref:System.Environment.UserName%2A> chaîne, qui est défini dans le <xref:System.Environment> espace de noms.  
  
## <a name="example"></a>Exemple  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)