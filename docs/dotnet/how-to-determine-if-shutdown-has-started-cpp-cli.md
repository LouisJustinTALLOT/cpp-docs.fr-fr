---
title: 'Comment : déterminer si l’arrêt a commencé (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbcc2b1efa54808b25238bde4de3dcc21d2ba687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137700"
---
# <a name="how-to-determine-if-shutdown-has-started-ccli"></a>Comment : déterminer si le processus d'arrêt a commencé (C++/CLI)
L’exemple de code suivant montre comment déterminer si l’application ou le .NET Framework s’arrête. Cela est utile pour accéder à des éléments statiques dans le .NET Framework, car, lors de l’arrêt, ces constructions sont finalisées par le système et ne peut pas être utilisées de manière fiable. En vérifiant la <xref:System.Environment.HasShutdownStarted%2A> propriété tout d’abord, vous pouvez éviter tout problème potentiel par ne pas l’accès à ces éléments.  
  
## <a name="example"></a>Exemple  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)