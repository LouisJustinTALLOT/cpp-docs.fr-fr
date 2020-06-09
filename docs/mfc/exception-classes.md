---
title: Classes d'exceptions
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: 907b34b12ffdaa70c4377a1012a66662fbba12d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619522"
---
# <a name="exception-classes"></a>Classes d'exceptions

La bibliothèque de classes fournit un mécanisme de gestion des exceptions basé sur la classe `CException` . L’infrastructure d’application utilise des exceptions dans son code. vous pouvez également les utiliser dans les vôtres. Pour plus d’informations, consultez l’article [exceptions](exception-handling-in-mfc.md). Vous pouvez dériver vos propres types d’exception à partir de `CException` .

MFC fournit une classe d’exception à partir de laquelle vous pouvez dériver votre propre exception, ainsi que des classes d’exception pour toutes les exceptions qu’elle prend en charge.

[CException](reference/cexception-class.md)<br/>
Classe de base des exceptions.

[CArchiveException](reference/carchiveexception-class.md)<br/>
Une exception d’archive.

[CDaoException](reference/cdaoexception-class.md)<br/>
Exception résultant d’une défaillance dans une opération de base de données DAO.

[CDBException](reference/cdbexception-class.md)<br/>
Exception résultant d’un échec dans le traitement de la base de données ODBC.

[CFileException](reference/cfileexception-class.md)<br/>
Une exception orientée fichier.

[CMemoryException](reference/cmemoryexception-class.md)<br/>
Une exception de mémoire insuffisante.

[CNotSupportedException](reference/cnotsupportedexception-class.md)<br/>
Exception résultant de l’utilisation d’une fonctionnalité non prise en charge.

[COleException](reference/coleexception-class.md)<br/>
Exception résultant d’un échec dans le traitement OLE. Cette classe est utilisée par les conteneurs et les serveurs.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
Exception résultant d’une erreur lors de l’automatisation. Les exceptions Automation sont levées par les serveurs Automation et interceptées par les clients Automation.

[CResourceException](reference/cresourceexception-class.md)<br/>
Exception résultant de l’échec du chargement d’une ressource Windows.

[CUserException](reference/cuserexception-class.md)<br/>
Exception utilisée pour arrêter une opération lancée par l’utilisateur. En général, l’utilisateur a été averti du problème avant que cette exception ne soit levée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
