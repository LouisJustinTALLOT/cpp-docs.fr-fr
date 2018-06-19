---
title: Extraction de données | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab03da7c303552a715c6766af7829e74025866ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101199"
---
# <a name="fetching-data"></a>Récupération de données
Après avoir ouvert la source de données, de session et objets d’ensemble de lignes, vous pouvez extraire les données. Selon le type d’accesseur que vous utilisez, vous devrez peut-être lier les colonnes.  
  
### <a name="to-fetch-data"></a>Pour extraire des données  
  
1.  Ouvrir l’ensemble de lignes en utilisant le pilote **ouvrir** commande.  
  
2.  Si vous utilisez `CManualAccessor`, liez les colonnes de sortie si vous ne le n'avez pas déjà fait. Pour lier les colonnes, appelez `GetColumnInfo`, puis créez un accesseur avec les liaisons, comme illustré dans l’exemple suivant :  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  Écrire un `while` boucle pour récupérer les données. Dans la boucle, appelez `MoveNext` pour faire avancer le curseur et de tester la valeur de retour à S_OK, comme illustré dans l’exemple suivant :  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  Dans la `while` boucle, vous pouvez extraire les données en fonction du type d’accesseur.  
  
    -   Si vous utilisez la [CAccessor](../../data/oledb/caccessor-class.md) (classe), vous devez avoir un enregistrement d’utilisateur qui contient les membres de données. Vous pouvez accéder vos données à l’aide de ces données membres, comme indiqué dans l’exemple suivant :  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Si vous utilisez la `CDynamicAccessor` ou `CDynamicParameterAccessor` (classe), vous pouvez extraire les données en utilisant les fonctions d’accès `GetValue` et `GetColumn`, comme illustré dans l’exemple suivant. Si vous souhaitez déterminer le type de données que vous utilisez, utilisez `GetType`.  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   Si vous utilisez `CManualAccessor`, vous devez spécifier vos propres données membres, les lier et accéder directement, comme indiqué dans l’exemple suivant :  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)