---
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
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366629"
---
# <a name="exceptions-database-exceptions"></a>Exceptions : exceptions de base de données

Cet article explique comment gérer les exceptions de base de données. La plupart du matériel de cet article s’applique si vous travaillez avec les classes MFC pour la connectivité open Database (ODBC) ou les classes MFC pour les objets d’accès aux données (DAO). Le matériel spécifique à l’un ou l’autre modèle est explicitement marqué. Les sujets abordés sont les suivants :

- [Approches de manipulation des exceptions](#_core_approaches_to_exception_handling)

- [Un exemple de manipulation d’exception de base de données](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>Approches de la manipulation des exceptions

L’approche est la même que vous travailliez avec DAO (obsolète) ou ODBC.

Vous devez toujours écrire des gestionnaires d’exception pour gérer des conditions exceptionnelles.

L’approche la plus pragmatique pour attraper les exceptions de base de données est de tester votre application avec des scénarios d’exception. Déterminez les exceptions probables qui pourraient se produire pour une opération dans votre code, et forcez l’exception à se produire. Examinez ensuite la sortie de trace pour voir quelle exception est jetée, ou examinez les informations d’erreur retournées dans le débagé. Cela vous permet de savoir quels codes de retour vous verrez pour les scénarios d’exception que vous utilisez.

### <a name="error-codes-used-for-odbc-exceptions"></a>Codes d’erreur utilisés pour les exceptions ODBC

En plus des codes de retour définis par le cadre, qui ont des noms du formulaire **AFX_SQL_ERROR_XXX**, certaines [CDBExceptions](../mfc/reference/cdbexception-class.md) sont basées sur les codes de retour [ODBC.](../data/odbc/odbc-basics.md) Les codes de retour pour de telles exceptions ont des noms du formulaire **SQL_ERROR_XXX**.

Les codes de retour — définis par le cadre et définis par la BDBC `CDBException`— que les classes de base de données peuvent retourner sont documentés dans le cadre de la [m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode) membre des données de classe . Des informations supplémentaires sur les codes de retour définis par ODBC sont disponibles dans la *référence du programmeur* SDK de l’ODBC dans la bibliothèque MSDN.

### <a name="error-codes-used-for-dao-exceptions"></a>Codes d’erreur utilisés pour les exceptions DAO

Pour les exceptions DAO, plus d’informations sont généralement disponibles. Vous pouvez accéder aux informations d’erreur via trois membres de données d’un objet [CDaoException](../mfc/reference/cdaoexception-class.md) capturé :

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) contient un pointeur sur un objet [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) qui encapsule les informations d’erreur dans la collection d’objets d’erreur de DAO associés à la base de données.

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror) contient un code d’erreur étendu des classes MFC DAO. Ces codes d’erreur, qui **AFX_DAO_ERROR_XXX**ont des noms du formulaire AFX_DAO_ERROR_XXX `CDaoException`, sont documentés sous le membre des données dans .

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode) contient un **SCODE** OLE de DAO, le cas échéant. Vous aurez rarement besoin de travailler avec ce code d’erreur, cependant. Habituellement, plus d’informations sont disponibles dans les deux autres membres de données. Consultez le membre des données pour en savoir plus sur les valeurs **SCODE.**

Des informations supplémentaires sur les erreurs DAO, le type d’objet DAO Error et la collection DAO Errors sont disponibles sous la classe [CDaoException](../mfc/reference/cdaoexception-class.md).

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>Un exemple de manipulation d’exception de base de données

L’exemple suivant tente de construire un objet dérivé du [CRecordset](../mfc/reference/crecordset-class.md)sur le tas avec le **nouvel** opérateur, puis d’ouvrir le jeu d’enregistrement (pour une source de données ODBC). Pour un exemple similaire pour les classes DAO, voir "DAO Exception Exemple" ci-dessous.

### <a name="odbc-exception-example"></a>Exemple d’exception ODBC

La fonction de membre [Open](../mfc/reference/crecordset-class.md#open) pourrait jeter une exception (de type [CDBException](../mfc/reference/cdbexception-class.md) `Open` pour les classes ODBC), de sorte que ce code porte l’appel avec un bloc **d’essai.** Le bloc **de** capture `CDBException`subséquent attrapera un . Vous pouvez examiner l’objet `e`d’exception lui-même, appelé , mais dans ce cas, il suffit de savoir que la tentative de créer un ensemble d’enregistrements a échoué. Le bloc **de capture** affiche une boîte de message et nettoie en supprimant l’objet de l’enregistrement.

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>Exemple d’exception DAO

L’exemple DAO est similaire à l’exemple pour ODBC, mais vous pouvez généralement récupérer plus de types d’informations. Le code suivant tente également d’ouvrir un tableau d’enregistrement. Si cette tentative lance une exception, vous pouvez examiner un membre des données de l’objet d’exception pour obtenir des informations d’erreur. Comme avec l’exemple précédent ODBC, il est probablement suffisant de savoir que la tentative de créer un record a échoué.

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

Ce code reçoit une chaîne de message d’erreur de la [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo) membre de l’objet d’exception. MFC remplit ce membre lorsqu’il lance l’exception.

Pour une discussion des informations `CDaoException` d’erreur retournées par un objet, voir les classes [CDaoException](../mfc/reference/cdaoexception-class.md) et [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md).

Lorsque vous travaillez avec les bases de données Microsoft Jet (.mdb), et dans la plupart des cas lorsque vous travaillez avec ODBC, il n’y aura qu’un seul objet d’erreur. Dans les rares cas où vous utilisez une source de données ODBC et qu’il y a plusieurs erreurs, vous pouvez boucler la collection d’erreurs de DAO en fonction du nombre d’erreurs retournées par [CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount). Chaque fois que vous traversez la boucle, appelez [CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo) pour remplir le membre des `m_pErrorInfo` données.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../mfc/exception-handling-in-mfc.md)
