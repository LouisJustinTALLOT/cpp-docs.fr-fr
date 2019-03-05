---
title: 'Exceptions : Exceptions de base de données'
ms.date: 11/04/2016
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
ms.openlocfilehash: 2f7f3bff9f28968361ecfa7374a235a727443004
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285553"
---
# <a name="exceptions-database-exceptions"></a>Exceptions : Exceptions de base de données

Cet article explique comment gérer les exceptions de base de données. La plupart des informations présentées dans cet article s’applique si vous travaillez avec les classes MFC pour Open Database Connectivity (ODBC) ou les classes MFC pour les objets DAO (Data Access). Matériel spécifique à un ou l’autre modèle est explicitement marqué. Les rubriques traitées ici sont les suivantes :

- [Approches de gestion des exceptions](#_core_approaches_to_exception_handling)

- [Un exemple de gestion des exceptions de base de données](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a> Approches de gestion des exceptions

L’approche est la même si vous travaillez avec DAO ou ODBC.

Vous devez toujours écrire des gestionnaires d’exceptions pour gérer des conditions exceptionnelles.

L’approche la plus pragmatique pour intercepter des exceptions de base de données consiste à tester votre application avec des scénarios d’exception. Déterminer les exceptions susceptibles de qui peuvent se produire pour une opération dans votre code et forcer l’exception se produise. Puis examiner la sortie de trace pour voir quelle exception est levée, ou examiner les informations d’erreur retourné dans le débogueur. Cela vous permet de savoir quels s’affiche pour les scénarios d’exception que vous utilisez des codes de retour.

### <a name="error-codes-used-for-odbc-exceptions"></a>Codes d’erreur utilisés pour les Exceptions d’ODBC

En plus des codes de retour définies par l’infrastructure, qui ont des noms au format **AFX_SQL_ERROR_XXX**, certaines [CDBExceptions](../mfc/reference/cdbexception-class.md) sont basées sur [ODBC](../data/odbc/odbc-basics.md) codes de retour. Les codes de retour pour ces exceptions ont des noms au format **SQL_ERROR_XXX**.

Les codes de retour, à la fois définies par l’infrastructure et définie par ODBC — que les classes de base de données peuvent retourner sont documentés sous le [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) membre de données de la classe `CDBException`. Des informations supplémentaires sur les codes de retour définis par ODBC sont disponibles dans le SDK ODBC *de référence du programmeur* dans MSDN Library.

### <a name="error-codes-used-for-dao-exceptions"></a>Codes d’erreur utilisés pour les Exceptions DAO

Pour les exceptions DAO, plus d’informations sont généralement disponibles. Vous pouvez accéder à des informations d’erreur entre les membres de données de trois d’un interceptée [CDaoException](../mfc/reference/cdaoexception-class.md) objet :

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contient un pointeur vers un [objet CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) objet qui encapsule des informations sur l’erreur dans la collection DAO d’objets d’erreur associé à la base de données.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contient un code d’erreur étendu à partir des classes DAO MFC. Ces codes d’erreur, qui ont des noms au format **AFX_DAO_ERROR_XXX**, sont documentés sous le membre de données dans `CDaoException`.

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contient OLE **SCODE** de DAO, le cas échéant. Vous devez rarement travailler avec ce code d’erreur, toutefois. Généralement les informations supplémentaires sont disponibles dans les autres membres de données de deux. Consultez le membre de données pour en savoir plus **SCODE** valeurs.

Informations supplémentaires sur les erreurs DAO, le type d’objet DAO Error et la collection d’erreurs de DAO sont disponibles sous la classe [CDaoException](../mfc/reference/cdaoexception-class.md).

##  <a name="_core_a_database_exception.2d.handling_example"></a> Un exemple de gestion des exceptions de base de données

L’exemple suivant tente de construire un [CRecordset](../mfc/reference/crecordset-class.md)-objet dans le tas avec dérivé le **nouveau** opérateur, puis ouvrez le jeu d’enregistrements (pour une source de données ODBC). Pour obtenir un exemple similaire pour les classes DAO, consultez « Exemple d’Exception DAO » ci-dessous.

### <a name="odbc-exception-example"></a>Exemple d’Exception ODBC

Le [Open](../mfc/reference/crecordset-class.md#open) fonction membre pouvait lever une exception (de type [CDBException](../mfc/reference/cdbexception-class.md) pour les classes ODBC), par conséquent, ce code crochets le `Open` appeler avec une **essayez** bloc. Les informations suivantes **catch** bloc interceptera un `CDBException`. Vous pouvez examiner l’objet exception lui-même, appelé `e`, mais dans ce cas, il est suffisant de savoir que la tentative de création d’un jeu d’enregistrements a échoué. Le **catch** bloc affiche une boîte de message et nettoie en supprimant l’objet recordset.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Exemple d’Exception DAO

L’exemple DAO est similaire à l’exemple pour ODBC, mais vous pouvez généralement récupérer plusieurs types d’informations. Le code suivant tente également ouvrir un jeu d’enregistrements. Si cette tentative lève une exception, vous pouvez examiner un membre de données de l’objet d’exception des informations d’erreur. Comme avec l’exemple ODBC précédent, il est probablement suffisant de savoir que la tentative de création d’un jeu d’enregistrements a échoué.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ce code obtient une chaîne de message d’erreur à partir de la [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) membre de l’objet exception. MFC remplit ce membre lorsqu’il lève l’exception.

Pour une discussion sur les informations d’erreur retournées par un `CDaoException` d’objets, consultez les classes [CDaoException](../mfc/reference/cdaoexception-class.md) et [objet CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Lorsque vous travaillez avec des bases de données Microsoft Jet (.mdb) et dans la plupart des cas lorsque vous travaillez avec ODBC, il y aura qu’un seul objet d’erreur. Dans les rares cas lorsque vous utilisez une source de données ODBC et il existe plusieurs erreurs, vous pouvez itérer sur la collection d’erreurs DAO en fonction du nombre d’erreurs renvoyées par [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Chaque fois que la boucle, appelez [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pour recharger le `m_pErrorInfo` membre de données.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
