---
title: "Comment&#160;: impl&#233;menter le mot cl&#233; C# lock (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock (mot clé C#) (C++)"
  - "lock (instruction)"
ms.assetid: 436fe544-ffb7-49b9-9798-90794e9974de
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: impl&#233;menter le mot cl&#233; C# lock (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cette rubrique indique comment implémenter le mot clé C\# `lock` en Visual C\+\+.  Pour plus d'informations, consultez [lock, instruction](../Topic/lock%20Statement%20\(C%23%20Reference\).md).  
  
 Vous pouvez également utiliser la classe `lock` dans la bibliothèque de prise en charge C\+\+.  Pour plus d'informations, consultez [Synchronisation \(classe lock\)](../dotnet/synchronization-lock-class.md).  
  
## Exemple  
  
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
  
## Voir aussi  
 [Interopérabilité avec d'autres langages .NET](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)