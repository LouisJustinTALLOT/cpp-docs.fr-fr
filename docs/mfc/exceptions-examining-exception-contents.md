---
title: "Exceptions : examen du contenu des exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "catch (blocs), fonctions MFC (exceptions)"
  - "CException (classe), classe (exceptions)"
  - "gestion des exceptions, MFC"
  - "lever des exceptions, exceptions (contenu)"
  - "try-catch (gestion des exceptions), exceptions (contenu)"
  - "try-catch (gestion des exceptions), fonctions MFC (exceptions)"
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exceptions : examen du contenu des exceptions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Although a **catch** block's argument can be of almost any data type, the MFC functions throw exceptions of types derived from the class `CException`.  To catch an exception thrown by an MFC function, then, you write a **catch** block whose argument is a pointer to a `CException` object \(or an object derived from `CException`, such as `CMemoryException`\).  Depending on the exact type of the exception, you can examine the data members of the exception object to gather information about the specific cause of the exception.  
  
 For example, the `CFileException` type has the `m_cause` data member, which contains an enumerated type that specifies the cause of the file exception.  Some examples of the possible return values are **CFileException::fileNotFound** and **CFileException::readOnly**.  
  
 The following example shows how to examine the contents of a `CFileException`.  Other exception types can be examined similarly.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/CPP/exceptions-examining-exception-contents_1.cpp)]  
  
 For more information, see [Exceptions: Freeing Objects in Exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md) and [Exceptions: Catching and Deleting Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)