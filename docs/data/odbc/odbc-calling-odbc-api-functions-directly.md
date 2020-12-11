---
description: 'En savoir plus sur : ODBC : appel direct de fonctions API ODBC'
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
ms.openlocfilehash: 3b82e0270242d59767e9d67e6eb7491a4607990f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161115"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC : appel direct de fonctions API ODBC

Les classes de base de données fournissent une interface plus simple à une [source de données](../../data/odbc/data-source-odbc.md) que ODBC. Par conséquent, les classes n’encapsulent pas toutes les API ODBC. Pour toute fonctionnalité qui n’est pas conforme aux capacités des classes, vous devez appeler directement les fonctions de l’API ODBC. Par exemple, vous devez appeler directement les fonctions de catalogue ODBC (, `::SQLColumns` `::SQLProcedures` , `::SQLTables` et autres).

> [!NOTE]
> Les sources de données ODBC sont accessibles par le biais des classes ODBC MFC, comme décrit dans cette rubrique, ou par le biais des classes d’objets d’accès aux données (DAO) MFC.

Pour appeler directement une fonction API ODBC, vous devez suivre les mêmes étapes que si vous effectuiez les appels sans le Framework. Il s’agit des étapes suivantes :

- Allouez un stockage pour les résultats retournées par l’appel.

- Passer un `HDBC` handle ou ODBC `HSTMT` , en fonction de la signature de paramètre de la fonction. Utilisez la macro [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) pour récupérer le descripteur ODBC.

   Les variables membres `CDatabase::m_hdbc` et `CRecordset::m_hstmt` sont disponibles afin que vous n’ayez pas à les allouer et à les initialiser vous-même.

- Appelez peut-être des fonctions ODBC supplémentaires pour préparer ou suivre l’appel principal.

- Libérez de l’espace de stockage lorsque vous avez terminé.

Pour plus d’informations sur ces étapes, consultez [Guide de référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference).

En plus de ces étapes, vous devez effectuer des étapes supplémentaires pour vérifier les valeurs de retour de fonction, vous assurer que votre programme n’attend pas la fin d’un appel asynchrone, et ainsi de suite. Vous pouvez simplifier ces dernières étapes à l’aide des macros AFX_SQL_ASYNC et AFX_SQL_SYNC. Pour plus d’informations, consultez [macros et globales MFC](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="see-also"></a>Voir aussi

[Notions de base relatives à ODBC](../../data/odbc/odbc-basics.md)
