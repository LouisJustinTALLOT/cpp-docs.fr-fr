---
description: 'En savoir plus sur : exceptions : exceptions de base de données'
title: 'Exceptions : exceptions de base de données'
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
ms.openlocfilehash: 3e45f887d51b4b81196cd08d11f426f4ee6d4481
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290646"
---
# <a name="exceptions-database-exceptions"></a>Exceptions : exceptions de base de données

Cet article explique comment gérer les exceptions de base de données. La plupart des informations contenues dans cet article s’appliquent si vous utilisez les classes MFC pour Open Database Connectivity (ODBC) ou les classes MFC pour les objets d’accès aux données (DAO). Le matériel spécifique à l’un ou l’autre modèle est explicitement marqué. Les sujets abordés sont les suivants :

- [Approches de la gestion des exceptions](#_core_approaches_to_exception_handling)

- [Exemple de gestion des exceptions de base de données](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a> Approches de la gestion des exceptions

L’approche est la même que vous utilisiez DAO (obsolète) ou ODBC.

Vous devez toujours écrire des gestionnaires d’exceptions pour gérer des conditions exceptionnelles.

L’approche la plus pragmatique pour intercepter les exceptions de base de données consiste à tester votre application avec des scénarios d’exception. Déterminez les exceptions probables qui peuvent se produire pour une opération dans votre code et forcez l’exception à se produire. Examinez ensuite la sortie de trace pour voir quelle exception est levée, ou examinez les informations d’erreur retournées dans le débogueur. Cela vous permet de savoir quels codes de retour s’affichent pour les scénarios d’exception que vous utilisez.

### <a name="error-codes-used-for-odbc-exceptions"></a>Codes d’erreur utilisés pour les exceptions ODBC

En plus des codes de retour définis par le Framework, dont les noms se présentent sous la forme **AFX_SQL_ERROR_XXX**, certains [CDBExceptions](reference/cdbexception-class.md) sont basés sur des codes de retour [ODBC](../data/odbc/odbc-basics.md) . Les codes de retour pour ces exceptions ont des noms de la forme **SQL_ERROR_XXX**.

Les codes de retour (à la fois définis par l’infrastructure et définis par ODBC) que les classes de base de données peuvent retourner sont documentés sous la [m_nRetCode](reference/cdbexception-class.md#m_nretcode) membre de données de la classe `CDBException` . Des informations supplémentaires sur les codes de retour définis par ODBC sont disponibles dans le [Guide de référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference).

### <a name="error-codes-used-for-dao-exceptions"></a>Codes d’erreur utilisés pour les exceptions DAO

Pour les exceptions DAO, des informations supplémentaires sont généralement disponibles. Vous pouvez accéder aux informations d’erreur par le biais de trois membres de données d’un objet [CDaoException](reference/cdaoexception-class.md) intercepté :

- [m_pErrorInfo](reference/cdaoexception-class.md#m_perrorinfo) contient un pointeur vers un objet [CDaoErrorInfo](reference/cdaoerrorinfo-structure.md) qui encapsule des informations d’erreur dans la collection DAO d’objets Error associés à la base de données.

- [m_nAfxDaoError](reference/cdaoexception-class.md#m_nafxdaoerror) contient un code d’erreur étendu provenant des classes DAO MFC. Ces codes d’erreur, dont les noms se présentent sous la forme **AFX_DAO_ERROR_XXX**, sont documentés sous le membre de données dans `CDaoException` .

- [m_scode](reference/cdaoexception-class.md#m_scode) contient un **SCODE** OLE de DAO, le cas échéant. Toutefois, vous devrez rarement utiliser ce code d’erreur. En général, des informations supplémentaires sont disponibles dans les deux autres membres de données. Consultez le membre de données pour plus d’informations sur les valeurs **SCODE** .

Des informations supplémentaires sur les erreurs DAO, le type d’objet d’erreur DAO et la collection d’erreurs DAO sont disponibles sous la classe [CDaoException](reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a> Exemple de Exception-Handling de base de données

L’exemple suivant tente de construire un objet dérivé de [CRecordset](reference/crecordset-class.md)sur le tas avec l' **`new`** opérateur, puis d’ouvrir le jeu d’enregistrements (pour une source de données ODBC). Pour obtenir un exemple similaire pour les classes DAO, consultez « exemple d’exception DAO » ci-dessous.

### <a name="odbc-exception-example"></a>Exemple d’exception ODBC

La fonction membre [Open](reference/crecordset-class.md#open) peut lever une exception (de type [CDBException](reference/cdbexception-class.md) pour les classes ODBC), de sorte que ce code entre l' `Open` appel avec un **`try`** bloc. Le **`catch`** bloc suivant intercepte un `CDBException` . Vous pouvez examiner l’objet exception lui-même, appelé `e` , mais dans ce cas, il suffit de savoir que la tentative de création d’un jeu d’enregistrements a échoué. Le **`catch`** bloc affiche une boîte de message et nettoie en supprimant l’objet Recordset.

[!code-cpp[NVC_MFCDatabase#36](codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Exemple d’exception DAO

L’exemple DAO est similaire à l’exemple pour ODBC, mais vous pouvez généralement récupérer plus de types d’informations. Le code suivant tente également d’ouvrir un Recordset. Si cette tentative lève une exception, vous pouvez examiner les données membres de l’objet exception pour obtenir des informations sur l’erreur. Comme pour l’exemple ODBC précédent, il est probablement suffisant de savoir que la tentative de création d’un jeu d’enregistrements a échoué.

[!code-cpp[NVC_MFCDatabase#37](codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ce code obtient une chaîne de message d’erreur du membre [m_pErrorInfo](reference/cdaoexception-class.md#m_perrorinfo) de l’objet exception. MFC remplit ce membre lorsqu’il lève l’exception.

Pour une description des informations d’erreur retournées par un `CDaoException` objet, consultez les classes [CDaoException](reference/cdaoexception-class.md) et [CDaoErrorInfo](reference/cdaoerrorinfo-structure.md).

Lorsque vous utilisez des bases de données Microsoft Jet (. mdb) et, dans la plupart des cas, lorsque vous travaillez avec ODBC, il n’y aura qu’un seul objet d’erreur. Dans les rares cas où vous utilisez une source de données ODBC et il y a plusieurs erreurs, vous pouvez parcourir la collection d’erreurs de DAO en fonction du nombre d’erreurs retournées par [CDaoException :: GetErrorCount](reference/cdaoexception-class.md#geterrorcount). Chaque fois que vous exécutez la boucle, appelez [CDaoException :: GetErrorInfo](reference/cdaoexception-class.md#geterrorinfo) pour recharger le `m_pErrorInfo` membre de données.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](exception-handling-in-mfc.md)
