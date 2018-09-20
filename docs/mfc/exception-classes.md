---
title: Classes d’exceptions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.exception
dev_langs:
- C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd666f96ed694b57bf02eb3ad239783828b69e48
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439261"
---
# <a name="exception-classes"></a>Classes d'exceptions

La bibliothèque de classes fournit un mécanisme de gestion des exceptions basé sur la classe `CException`. L’infrastructure d’application utilise des exceptions dans son code ; Vous pouvez également les utiliser dans les vôtres. Pour plus d’informations, consultez l’article [Exceptions](../mfc/exception-handling-in-mfc.md). Vous pouvez dériver vos propres types d’exceptions à partir de `CException`.

MFC fournit une classe d’exception à partir de laquelle vous pouvez dériver votre propre exception, ainsi que des classes d’exception pour toutes les exceptions, qu'il prend en charge.

[CException](../mfc/reference/cexception-class.md)<br/>
Classe de base des exceptions.

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Une exception de l’archive.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Une exception résultant d’une défaillance dans une opération de base de données DAO.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Une exception résultant d’une défaillance lors du traitement de base de données ODBC.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Une exception orienté fichier.

[CMemoryException](../mfc/reference/cmemoryexception-class.md)<br/>
Une exception de mémoire insuffisante.

[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)<br/>
Une exception résultant à l’aide d’une fonctionnalité non prise en charge.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Une exception résultant d’une défaillance lors du traitement de OLE. Cette classe est utilisée par les conteneurs et les serveurs.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Une exception résultant d’une erreur lors de l’automatisation. Exceptions de Automation sont générées par les serveurs automation et interceptées par les clients automation.

[CResourceException](../mfc/reference/cresourceexception-class.md)<br/>
Une exception résultant d’un échec de chargement d’une ressource de Windows.

[CUserException](../mfc/reference/cuserexception-class.md)<br/>
Une exception utilisée pour arrêter une opération initiée par l’utilisateur. En règle générale, l’utilisateur a été averti du problème avant que cette exception est levée.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

