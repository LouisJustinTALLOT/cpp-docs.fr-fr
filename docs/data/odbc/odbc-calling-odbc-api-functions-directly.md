---
title: 'ODBC : Appel d’API ODBC directement les fonctions | Microsoft Docs'
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
ms.openlocfilehash: 386bc03234ccb29b293a413944f221189f466c80
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336593"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC : appel direct de fonctions API ODBC
Les classes de base de données fournissent une interface simple pour un [source de données](../../data/odbc/data-source-odbc.md) que ODBC. Par conséquent, les classes n’encapsulent pas toutes les API ODBC. Pour toutes les fonctionnalités qui se situe en dehors des capacités de classes, vous devez appeler directement les fonctions API ODBC. Par exemple, vous devez appeler les fonctions de catalogue ODBC (`::SQLColumns`, `::SQLProcedures`, `::SQLTables`, etc.) directement.  
  
> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes de données Access objet DAO (MFC).  
  
 Pour appeler une fonction API ODBC directement, vous devez prendre les mêmes étapes que vous prendriez si vous effectuez des appels sans l’infrastructure. Ils est comme suit :  
  
-   Allouer le stockage pour l’appel retourne tous les résultats.  
  
-   Passer d’une application ODBC `HDBC` ou `HSTMT` gérer, en fonction de la signature de paramètre de la fonction. Utilisez le [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) macro pour récupérer le descripteur ODBC.  
  
     Variables membres `CDatabase::m_hdbc` et `CRecordset::m_hstmt` sont disponibles afin que vous n’avez pas besoin d’allouer et initialiser ces vous-même.  
  
-   Peut-être appeler des fonctions ODBC supplémentaires pour préparer ou suivre l’appel principal.  
  
-   Libérer le stockage lorsque vous avez terminé.  
  
 Pour plus d’informations sur ces étapes, consultez le [Open Database Connectivity (ODBC)](https://msdn.microsoft.com/library/ms710252.aspx) SDK dans la documentation MSDN.  
  
 Outre ces étapes, vous devez effectuer des étapes supplémentaires pour vérifier les valeurs de retour de fonction, assurez-vous que votre programme n’est pas en attente d’un appel asynchrone à terminer et ainsi de suite. Vous pouvez simplifier ces dernières étapes en utilisant les macros AFX_SQL_ASYNC et AFX_SQL_SYNC. Pour plus d’informations, consultez [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans le *référence MFC*.  

## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
