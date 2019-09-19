---
title: 'Exceptions : Exceptions de base de données'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
ms.openlocfilehash: c279c5b788cc7bd8a68fe36128c116d8df91c2eb
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095817"
---
# <a name="exceptions-database-exceptions"></a>Exceptions : Exceptions de base de données

Cet article explique comment gérer les exceptions de base de données. La plupart des informations contenues dans cet article s’appliquent si vous utilisez les classes MFC pour Open Database Connectivity (ODBC) ou les classes MFC pour les objets d’accès aux données (DAO). Le matériel spécifique à l’un ou l’autre modèle est explicitement marqué. Les rubriques traitées ici sont les suivantes :

- [Approches de la gestion des exceptions](#_core_approaches_to_exception_handling)

- [Exemple de gestion des exceptions de base de données](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a>Approches de la gestion des exceptions

L’approche est la même que vous utilisiez DAO (obsolète) ou ODBC.

Vous devez toujours écrire des gestionnaires d’exceptions pour gérer des conditions exceptionnelles.

L’approche la plus pragmatique pour intercepter les exceptions de base de données consiste à tester votre application avec des scénarios d’exception. Déterminez les exceptions probables qui peuvent se produire pour une opération dans votre code et forcez l’exception à se produire. Examinez ensuite la sortie de trace pour voir quelle exception est levée, ou examinez les informations d’erreur retournées dans le débogueur. Cela vous permet de savoir quels codes de retour s’affichent pour les scénarios d’exception que vous utilisez.

### <a name="error-codes-used-for-odbc-exceptions"></a>Codes d’erreur utilisés pour les exceptions ODBC

En plus des codes de retour définis par le Framework, dont les noms se présentent sous la forme **AFX_SQL_ERROR_XXX**, certains [CDBExceptions](../mfc/reference/cdbexception-class.md) sont basés sur des codes de retour [ODBC](../data/odbc/odbc-basics.md) . Les codes de retour pour ces exceptions ont des noms au format **SQL_ERROR_XXX**.

Les codes de retour (à la fois définis par l’infrastructure et définis par ODBC) que les classes de base de données peuvent retourner sont documentés sous le membre de données [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) de la classe `CDBException`. Des informations supplémentaires sur les codes de retour définis par ODBC sont disponibles dans le *Guide de référence du programmeur* ODBC SDK de MSDN Library.

### <a name="error-codes-used-for-dao-exceptions"></a>Codes d’erreur utilisés pour les exceptions DAO

Pour les exceptions DAO, des informations supplémentaires sont généralement disponibles. Vous pouvez accéder aux informations d’erreur par le biais de trois membres de données d’un objet [CDaoException](../mfc/reference/cdaoexception-class.md) intercepté :

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contient un pointeur vers un objet [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) qui encapsule les informations d’erreur dans la collection DAO d’objets Error associés à la base de données.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contient un code d’erreur étendu des classes DAO MFC. Ces codes d’erreur, dont les noms se présentent sous la forme **AFX_DAO_ERROR_XXX**, sont documentés sous `CDaoException`le membre de données dans.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contient un **SCODE** OLE de DAO, le cas échéant. Toutefois, vous devrez rarement utiliser ce code d’erreur. En général, des informations supplémentaires sont disponibles dans les deux autres membres de données. Consultez le membre de données pour plus d’informations sur les valeurs **SCODE** .

Des informations supplémentaires sur les erreurs DAO, le type d’objet d’erreur DAO et la collection d’erreurs DAO sont disponibles sous la classe [CDaoException](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a>Exemple de gestion des exceptions de base de données

L’exemple suivant tente de construire un objet dérivé de [CRecordset](../mfc/reference/crecordset-class.md)sur le tas à l’aide de l’opérateur **New** , puis d’ouvrir le jeu d’enregistrements (pour une source de données ODBC). Pour obtenir un exemple similaire pour les classes DAO, consultez « exemple d’exception DAO » ci-dessous.

### <a name="odbc-exception-example"></a>Exemple d’exception ODBC

La fonction membre [Open](../mfc/reference/crecordset-class.md#open) peut lever une exception (de type [CDBException](../mfc/reference/cdbexception-class.md) pour les classes ODBC). ce `Open` code entre en parenthèses avec un bloc **try** . Le bloc **catch** suivant intercepte un `CDBException`. Vous pouvez examiner l’objet exception lui-même `e`, appelé, mais dans ce cas, il suffit de savoir que la tentative de création d’un jeu d’enregistrements a échoué. Le bloc **catch** affiche une boîte de message et nettoie en supprimant l’objet Recordset.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Exemple d’exception DAO

L’exemple DAO est similaire à l’exemple pour ODBC, mais vous pouvez généralement récupérer plus de types d’informations. Le code suivant tente également d’ouvrir un Recordset. Si cette tentative lève une exception, vous pouvez examiner les données membres de l’objet exception pour obtenir des informations sur l’erreur. Comme pour l’exemple ODBC précédent, il est probablement suffisant de savoir que la tentative de création d’un jeu d’enregistrements a échoué.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ce code obtient une chaîne de message d’erreur du membre [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) de l’objet exception. MFC remplit ce membre lorsqu’il lève l’exception.

Pour une description des informations d’erreur retournées `CDaoException` par un objet, consultez les classes [CDaoException](../mfc/reference/cdaoexception-class.md) et [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Lorsque vous utilisez des bases de données Microsoft Jet (. mdb) et, dans la plupart des cas, lorsque vous travaillez avec ODBC, il n’y aura qu’un seul objet d’erreur. Dans les rares cas où vous utilisez une source de données ODBC et il y a plusieurs erreurs, vous pouvez parcourir la collection d’erreurs de DAO en fonction du nombre d’erreurs retournées par [CDaoException :: GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Chaque fois que vous exécutez la boucle, appelez [CDaoException :: GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pour `m_pErrorInfo` recharger le membre de données.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
