---
title: 'Exceptions : Exceptions de base de données | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83b3f4f54f467ca7f4fbd2a179fdbf01d54dfa89
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930236"
---
# <a name="exceptions-database-exceptions"></a>Exceptions : exceptions de base de données
Cet article explique comment gérer les exceptions de base de données. La plupart des éléments de cet article s’applique si vous travaillez avec les classes MFC pour la connectivité ODBC (Open Database) ou les classes MFC pour les objets DAO (Data Access). Matériel spécifique à un ou l’autre modèle est marquée explicitement. Les rubriques traitées ici sont les suivantes :  
  
-   [Approches de la gestion des exceptions](#_core_approaches_to_exception_handling)  
  
-   [Un exemple de gestion des exceptions de base de données](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> Approches de la gestion des exceptions  
 L’approche est la même si vous travaillez avec DAO ou ODBC.  
  
 Vous devez toujours écrire des gestionnaires d’exceptions pour gérer des conditions exceptionnelles.  
  
 L’approche la plus pragmatique pour intercepter les exceptions de base de données est à tester votre application avec des scénarios d’exception. Déterminer les exceptions susceptibles de qui peuvent se produire pour une opération dans votre code et forcer l’exception se produise. Puis examinez la sortie de trace pour voir l’exception est levée, ou examiner les informations d’erreur retourné dans le débogueur. Cela vous permet de savoir quels s’affiche pour les scénarios d’exception que vous utilisez des codes de retour.  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>Codes d’erreur utilisés pour les Exceptions ODBC  
 En plus des codes de retour définies par l’infrastructure, qui ont des noms au format **AFX_SQL_ERROR_XXX**, certaines [CDBExceptions](../mfc/reference/cdbexception-class.md) sont basées sur [ODBC](../data/odbc/odbc-basics.md) codes de retour. Les codes de retour pour ces exceptions ont des noms au format **SQL_ERROR_XXX**.  
  
 Les codes de retour : à la fois définies par l’infrastructure et définie par ODBC — que les classes de base de données peuvent retourner sont décrits dans le [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) membre de données de la classe `CDBException`. Des informations supplémentaires sur les codes de retour définis par ODBC sont disponibles dans le SDK ODBC *de référence du programmeur* dans MSDN Library.  
  
### <a name="error-codes-used-for-dao-exceptions"></a>Codes d’erreur utilisés pour les Exceptions DAO  
 Pour les exceptions DAO, plus d’informations est généralement disponible. Vous pouvez accéder à des informations d’erreur entre les membres de données de trois d’une interceptée [CDaoException](../mfc/reference/cdaoexception-class.md) objet :  
  
-   [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contient un pointeur vers un [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) objet qui encapsule des informations d’erreur dans la collection DAO des objets d’erreur associé à la base de données.  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contient un code d’erreur étendu à partir des classes DAO MFC. Ces codes d’erreur, qui ont des noms au format **AFX_DAO_ERROR_XXX**, sont décrits dans le membre de données dans `CDaoException`.  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contient OLE **SCODE** de DAO, le cas échéant. Vous devrez rarement toutefois de fonctionner avec ce code d’erreur. Généralement les informations supplémentaires sont disponibles dans les autres deux membres de données. Le membre de données pour plus d’informations, consultez **SCODE** valeurs.  
  
 Des informations supplémentaires sur les erreurs DAO, le type d’objet DAO Error et la collection d’erreurs de DAO sont disponibles sous la classe [CDaoException](../mfc/reference/cdaoexception-class.md).  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> Un exemple de gestion des exceptions de base de données  
 L’exemple suivant tente de construire un [CRecordset](../mfc/reference/crecordset-class.md)-dérivée de l’objet sur le segment de mémoire avec la **nouveau** (opérateur), puis ouvrez le jeu d’enregistrements (pour une source de données ODBC). Pour obtenir un exemple similaire pour les classes DAO, consultez « Exemple d’Exception DAO » ci-dessous.  
  
### <a name="odbc-exception-example"></a>Exemple d’Exception ODBC  
 Le [ouvrir](../mfc/reference/crecordset-class.md#open) fonction membre peut lever une exception (de type [CDBException](../mfc/reference/cdbexception-class.md) pour les classes ODBC), par conséquent cette code crochets le `Open` appeler avec un **essayez** bloc. Les **catch** bloc intercepte un `CDBException`. Vous pouvez examiner l’objet exception lui-même, appelé `e`, mais dans ce cas, il est suffisant de savoir que la tentative de création d’un jeu d’enregistrements a échoué. Le **catch** bloc affiche une boîte de message et nettoie en supprimant l’objet recordset.  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>Exemple d’Exception DAO  
 L’exemple DAO est similaire à l’exemple pour ODBC, mais vous pouvez généralement récupérer des types d’informations. Le code suivant tente également ouvrir un jeu d’enregistrements. Si cette tentative lève une exception, vous pouvez examiner un membre de données de l’objet exception pour plus d’informations d’erreur. Comme l’exemple ODBC précédent, il est probablement insuffisante connaître l’échec de création d’un jeu d’enregistrements.  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 Ce code obtient la chaîne de message d’erreur à partir de la [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) membre de l’objet exception. MFC remplit ce membre lorsqu’il lève l’exception.  
  
 Pour en savoir plus sur les informations d’erreur retournées par un `CDaoException` d’objets, consultez les classes [CDaoException](../mfc/reference/cdaoexception-class.md) et [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).  
  
 Lorsque vous travaillez avec des bases de données Microsoft Jet (.mdb) et dans la plupart des cas lorsque vous travaillez avec ODBC, il y aura qu’un seul objet d’erreur. Dans les rares cas lorsque vous utilisez une source de données ODBC et il existe plusieurs erreurs, vous pouvez parcourir en boucle collection d’erreurs DAO en fonction du nombre d’erreurs renvoyées par [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Chaque fois que la boucle, appelez [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pour recharger la `m_pErrorInfo` membre de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../mfc/exception-handling-in-mfc.md)

