---
title: L’extraction de données | Microsoft Docs
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
ms.openlocfilehash: b7aaff3ccd2756ecfbac1cf745aaac74b76a91f9
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48859950"
---
# <a name="fetching-data"></a>Récupération de données

Une fois que vous ouvrez la source de données, session et objets d’ensemble de lignes, vous pouvez extraire des données. Selon le type d’accesseur que vous utilisez, vous devrez peut-être lier les colonnes.

### <a name="to-fetch-data"></a>Pour extraire des données

1. Ouvrez l’ensemble de lignes en utilisant la **Open** commande.

1. Si vous utilisez `CManualAccessor`, liez les colonnes de sortie si vous ne le n'avez pas déjà fait. Pour lier les colonnes, appelez `GetColumnInfo`, puis créez un accesseur avec les liaisons, comme illustré dans l’exemple suivant :

    ```cpp
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

1. Écrire un `while` boucle pour récupérer les données. Dans la boucle, appelez `MoveNext` pour faire avancer le curseur et de tester la valeur de retour à S_OK, comme indiqué dans l’exemple suivant :

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. Dans le `while` boucle, vous pouvez extraire les données en fonction du type d’accesseur.

   - Si vous utilisez le [CAccessor](../../data/oledb/caccessor-class.md) (classe), vous devez avoir un enregistrement utilisateur qui contient les membres de données. Vous pouvez accéder vos données à l’aide de ces données membres, comme indiqué dans l’exemple suivant :

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Si vous utilisez le `CDynamicAccessor` ou `CDynamicParameterAccessor` (classe), vous pouvez extraire des données en utilisant les fonctions d’accès `GetValue` et `GetColumn`, comme illustré dans l’exemple suivant. Si vous souhaitez déterminer le type de données que vous utilisez, utilisez `GetType`.

        ```cpp
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

   - Si vous utilisez `CManualAccessor`, vous devez spécifier vos propres données membres, les lier et y accéder directement, comme indiqué dans l’exemple suivant :

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
