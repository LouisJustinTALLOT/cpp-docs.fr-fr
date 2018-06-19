---
title: 'ODBC : Appel d’API ODBC directement les fonctions | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 55b95c5dd48631f9c724aebd163ce948c3469850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089712"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC : appel direct de fonctions API ODBC
Les classes de base de données fournissent une interface simple pour un [source de données](../../data/odbc/data-source-odbc.md) que ODBC. Par conséquent, les classes n’encapsulent pas toutes les API ODBC. Pour toutes les fonctionnalités qui se situe en dehors de la capacité des classes, vous devez appeler directement les fonctions API ODBC. Par exemple, vous devez appeler les fonctions de catalogue ODBC (**:: SQLColumns**, **:: SQLProcedures**, **:: SQLTables**, etc.) directement.  
  
> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes MFC DAO Data Access Object ().  
  
 Pour appeler une fonction API ODBC directement, vous devez prendre les mêmes étapes à que suivre si vous effectuez des appels sans la structure. Ils sont des étapes :  
  
-   Allouer du stockage pour les résultats de que l’appel est retourné.  
  
-   Passer d’une application ODBC **pas** ou **HSTMT** gérer, selon la signature de paramètre de la fonction. Utilisez le [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) macro pour récupérer le descripteur ODBC.  
  
     Variables membres **CDatabase::m_hdbc** et **CRecordset::m_hstmt** sont disponibles afin que vous n’avez pas besoin d’allouer et initialiser vous-même.  
  
-   Appelez peut-être des fonctions ODBC supplémentaires pour préparer ou suivre l’appel principal.  
  
-   Libération du stockage lorsque vous avez terminé.  
  
 Pour plus d’informations sur ces étapes, consultez le [connectivité ODBC (Open Database)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK dans la documentation MSDN.  
  
 Outre ces étapes, vous devez prendre des mesures supplémentaires pour vérifier les valeurs de retour de fonction, vous assurer que votre programme n’est pas en attente d’un appel asynchrone terminer et ainsi de suite. Vous pouvez simplifier ces dernières étapes à l’aide de la `AFX_SQL_ASYNC` et `AFX_SQL_SYNC` macros. Pour plus d’informations, consultez [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans les *référence MFC*.  

  
## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
