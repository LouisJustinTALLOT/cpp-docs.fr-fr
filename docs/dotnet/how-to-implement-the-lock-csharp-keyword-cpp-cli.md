---
title: 'Comment : implémenter le mot clé c# lock (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lock statement
- lock C# keyword [C++]
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dba651a7bcbfb1e8d7a0d107fe2400e222b06111
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127914"
---
# <a name="how-to-implement-the-lock-c-keyword-ccli"></a>Comment : implémenter le mot clé C# lock (C++/CLI)
Cette rubrique illustre l’implémentation du langage c# `lock` mot clé dans Visual C++. 
  
 Vous pouvez également utiliser la `lock` classe dans la bibliothèque de prise en charge C++. Consultez [synchronisation (classe lock)](../dotnet/synchronization-lock-class.md) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
  
```  
// CS_lock_in_CPP.cpp  
// compile with: /clr  
using namespace System::Threading;  
ref class Lock {  
   Object^ m_pObject;  
public:  
   Lock( Object ^ pObject ) : m_pObject( pObject ) {  
      Monitor::Enter( m_pObject );  
   }  
   ~Lock() {  
      Monitor::Exit( m_pObject );  
   }  
};  
  
ref struct LockHelper {  
   void DoSomething();  
};  
  
void LockHelper::DoSomething() {  
   // Note: Reference type with stack allocation semantics to provide   
   // deterministic finalization  
  
   Lock lock( this );     
   // LockHelper instance is locked  
}  
  
int main()  
{  
   LockHelper lockHelper;  
   lockHelper.DoSomething();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité avec d’autres langages .NET (C++-CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)