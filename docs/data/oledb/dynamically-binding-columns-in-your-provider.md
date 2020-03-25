---
title: Liaison dynamique des colonnes dans votre fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- columns [C++], dynamic column binding
- dynamic column binding
- providers [C++], dynamic column binding
ms.assetid: 45e811e3-f5a7-4627-98cc-bf817c4e556e
ms.openlocfilehash: 8a0b4c399bf25137be86d95102da9723c3116d51
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210975"
---
# <a name="dynamically-binding-columns-in-your-provider"></a>Liaison dynamique des colonnes dans votre fournisseur

Assurez-vous que vous avez vraiment besoin d’une liaison de colonne dynamique. Vous en aurez peut-être besoin pour les raisons suivantes :

- Vos colonnes d’ensemble de lignes ne sont pas définies au moment de la compilation.

- Vous prenez en charge un élément tel que Bookmark qui ajoute des colonnes.

## <a name="to-implement-dynamic-column-binding"></a>Pour implémenter une liaison de colonne dynamique

1. Supprimez les `PROVIDER_COLUMN_MAP`s de votre code.

1. Dans l’enregistrement utilisateur (votre structure), ajoutez la déclaration suivante :

    ```cpp
    static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
    ```

1. Implémentez la fonction `GetColumnInfo`. Cette fonction définit la manière dont les informations sont stockées. Vous devrez peut-être obtenir des propriétés ou d’autres informations pour cette fonction. Vous souhaiterez peut-être créer une macro, similaire à la macro [COLUMN_ENTRY](../../data/oledb/column-entry.md) , pour ajouter vos propres informations.

   L’exemple suivant illustre une fonction `GetColumnInfo`.

    ```cpp
    // Check the property flag for bookmarks, if it is set, set the zero
    // ordinal entry in the column map with the bookmark information.
    CAgentRowset* pRowset = (CAgentRowset*) pThis;
    CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

    CDBPropIDSet set(DBPROPSET_ROWSET);
    set.AddPropertyID(DBPROP_BOOKMARKS);
    DBPROPSET* pPropSet = NULL;
    ULONG ulPropSet = 0;
    HRESULT hr;

    if (spRowsetProps)
       hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

    if (pPropSet)
    {
       CComVariant var = pPropSet->rgProperties[0].vValue;
       CoTaskMemFree(pPropSet->rgProperties);
       CoTaskMemFree(pPropSet);

       if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
       {
          ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), DBTYPE_BYTES,
             0, 0, GUID_NULL, CAgentMan, dwBookmark, DBCOLUMNFLAGS_ISBOOKMARK)
          ulCols++;
       }
    }

    // Next, set up the other columns.
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szCommand)
    ulCols++;
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szText)
    ulCols++;

    ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szCommand2)
    ulCols++;
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szText2)
    ulCols++;

    if (pcCols != NULL)
       *pcCols = ulCols;

    return _rgColumns;
    }
    ```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
