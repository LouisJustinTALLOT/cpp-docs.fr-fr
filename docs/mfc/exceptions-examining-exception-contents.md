---
title: 'Exceptions : Examen du contenu des exceptions | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c7453b92ce14fbbcd20ea0f9a8bd8a7a2b5b6d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932232"
---
# <a name="exceptions-examining-exception-contents"></a>Exceptions : examen du contenu des exceptions
Bien qu’un **catch** l’argument du bloc peut être de presque n’importe quel type de données, les fonctions MFC lèvent des exceptions de types dérivés de la classe `CException`. Pour intercepter une exception levée par une fonction MFC, puis, vous écrivez un **catch** dont l’argument est un pointeur de bloc pour un `CException` objet (ou un objet dérivé `CException`, tel que `CMemoryException`). Selon le type exact de l’exception, vous pouvez examiner les membres de données de l’objet exception pour recueillir des informations sur la cause spécifique de l’exception.  
  
 Par exemple, le `CFileException` type a la `m_cause` membre de données qui contient un type énuméré qui spécifie la cause de l’exception du fichier. Quelques exemples de ces valeurs de retour sont `CFileException::fileNotFound` et `CFileException::readOnly`.  
  
 L’exemple suivant montre comment examiner le contenu d’un `CFileException`. Autres types d’exceptions peuvent être examinées de la même façon.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Pour plus d’informations, consultez [Exceptions : libération d’objets dans les Exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md) et [Exceptions : interception et suppression des Exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

