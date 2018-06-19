---
title: 'Comment : déterminer l’état interactif des utilisateurs (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, user interactive state
- user interactive state
ms.assetid: 9f52323e-38b8-4a41-9b1d-052012ad839b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4649a6e7ce4833b55f38e636b87bb53f646e85cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127303"
---
# <a name="how-to-determine-the-user-interactive-state-ccli"></a>Comment : déterminer l'état interactif d'un utilisateur (C++/CLI)
L’exemple de code suivant montre comment déterminer si le code est exécuté dans un contexte utilisateur interactif. Si <xref:System.Environment.UserInteractive%2A> est false, le code s’exécute comme un processus de service ou à partir d’à l’intérieur d’une application Web, auquel cas vous devez interagir avec l’utilisateur.  
  
## <a name="example"></a>Exemple  
  
```  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)