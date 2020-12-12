---
description: 'En savoir plus sur : récupération de données'
title: Extraction de données
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 4d98a3d804688447f8f7073d20371a098b2bfa11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287526"
---
# <a name="fetching-data"></a>Extraction de données

Une fois que vous avez ouvert les objets de source de données, de session et d’ensemble de lignes, vous pouvez extraire des données. Selon le type d’accesseur que vous utilisez, vous devrez peut-être lier des colonnes.

## <a name="to-fetch-data"></a>Pour extraire des données

1. Ouvrez l’ensemble de lignes à l’aide de la commande **ouvrir** appropriée.

1. Si vous utilisez `CManualAccessor` , liez les colonnes de sortie si vous ne l’avez pas déjà fait. L’exemple suivant est extrait de l’exemple [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) . Pour lier les colonnes, appelez `GetColumnInfo` , puis créez un accesseur avec les liaisons, comme indiqué dans l’exemple suivant :

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

1. Écrire une **`while`** boucle pour récupérer les données. Dans la boucle, appelez `MoveNext` pour avancer le curseur et tester la valeur de retour par rapport à S_OK, comme indiqué dans l’exemple suivant :

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. Dans la **`while`** boucle, vous pouvez extraire les données en fonction de votre type d’accesseur.

   - Si vous utilisez la classe [CAccessor](../../data/oledb/caccessor-class.md) , vous devez avoir un enregistrement utilisateur qui contient des données membres. Vous pouvez accéder à vos données à l’aide de ces membres de données, comme indiqué dans l’exemple suivant :

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Si vous utilisez la `CDynamicAccessor` `CDynamicParameterAccessor` classe ou, vous pouvez extraire des données à l’aide des fonctions d’accès `GetValue` et `GetColumn` , comme indiqué dans l’exemple suivant. Si vous souhaitez déterminer le type de données que vous utilisez, utilisez `GetType` .

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

   - Si vous utilisez `CManualAccessor` , vous devez spécifier vos propres membres de données, les lier vous-même et y accéder directement, comme indiqué dans l’exemple suivant :

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de consommateurs OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
