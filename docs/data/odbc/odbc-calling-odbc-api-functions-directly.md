---
title: 'ODBC : appel direct de fonctions API ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368670"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC : appel direct de fonctions API ODBC

Les classes de base de données fournissent une interface plus simple à une [source de données](../../data/odbc/data-source-odbc.md) que ODBC. Par conséquent, les classes n’encapsulent pas toute l’API ODBC. Pour toute fonctionnalité qui ne correspond pas aux capacités des classes, vous devez appeler directement les fonctions API D’ODBC. Par exemple, vous devez appeler les fonctions `::SQLProcedures` `::SQLTables`du catalogue ODBC (,`::SQLColumns`, , et d’autres) directement.

> [!NOTE]
> Les sources de données de l’ODBC sont accessibles par l’intermédiaire des classes MFC ODBC, telles que décrites dans ce sujet, ou par l’intermédiaire des classes MFC Data Access Object (DAO).

Pour appeler directement une fonction API ODBC, vous devez prendre les mêmes mesures que vous prendrez si vous faisiez les appels sans le cadre. Ils étapes sont les suivantes:

- Allouer le stockage pour tous les résultats de l’appel retourne.

- Passez un `HDBC` ODBC `HSTMT` ou une poignée, selon la signature paramètre de la fonction. Utilisez la macro [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) pour récupérer la poignée ODBC.

   Les `CDatabase::m_hdbc` variables `CRecordset::m_hstmt` des membres et sont disponibles de sorte que vous n’avez pas besoin d’allouer et d’initialiser ceux-ci vous-même.

- Peut-être appeler des fonctions supplémentaires ODBC pour préparer ou suivre l’appel principal.

- Deallocate stockage lorsque vous avez terminé.

Pour plus d’informations sur ces étapes, voir le SDK [De connectivité à base de données ouverte (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) dans la documentation MSDN.

En plus de ces étapes, vous devez prendre des mesures supplémentaires pour vérifier les valeurs de retour de fonction, s’assurer que votre programme n’est pas en attente d’un appel asynchrone pour terminer, et ainsi de suite. Vous pouvez simplifier ces dernières étapes en utilisant les macros AFX_SQL_ASYNC et AFX_SQL_SYNC. Pour plus d’informations, voir [Macros et Globals](../../mfc/reference/mfc-macros-and-globals.md) dans la *référence MFC*.

## <a name="see-also"></a>Voir aussi

[ODBC Basics](../../data/odbc/odbc-basics.md)
