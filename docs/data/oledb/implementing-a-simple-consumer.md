---
title: Implémentation d'un consommateur simple
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 2d59989f8afd180b39153eed1ad0a20435aad9d4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923911"
---
# <a name="implementing-a-simple-consumer"></a>Implémentation d'un consommateur simple

::: moniker range="msvc-160"

L’Assistant Consommateur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures. Vous pouvez toujours ajouter la fonctionnalité manuellement. Pour plus d’informations, consultez [Création d’un consommateur sans utiliser l’Assistant](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=msvc-150"

Les rubriques suivantes montrent comment modifier les fichiers créés par l’ **Assistant Application MFC** et l’ **Assistant Consommateur OLE DB ATL** pour créer un consommateur simple. Cet exemple comporte les parties suivantes :

- [Récupération des données avec le consommateur](#retrieve) montre comment implémenter le code dans le consommateur qui lit toutes les données, ligne par ligne, à partir d’une table de base de données.

- [Ajout de la prise en charge de signet au consommateur](#bookmark) montre comment ajouter la prise en charge des signets au consommateur.

> [!NOTE]
> Vous pouvez utiliser l’application consommateur décrite dans cette section pour tester les exemples de fournisseur `MyProv` et `Provider`.

> [!NOTE]
> Pour générer une application consommateur pour tester `MyProv` (le même fournisseur que celui décrit dans [Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md)), vous devez inclure la prise en charge des signets comme décrit dans [Ajout de la prise en charge de signet au consommateur](#bookmark).

## <a name="retrieving-data-with-the-consumer"></a><a name="retrieve" ></a> Récupération des données avec le consommateur

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Pour modifier l’application de console afin d’utiliser le consommateur OLE DB

1. Dans `MyCons.cpp`, modifiez le code principal en insérant le texte en gras comme suit :

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="adding-bookmark-support-to-the-consumer"></a><a name="bookmark" ></a> Ajout de prise en charge de signet au consommateur

Un signet est une colonne qui identifie de façon unique les lignes dans le tableau. Il s’agit en général la colonne clé, mais ce n’est pas toujours le cas (ce point est spécifique au fournisseur). Cette section vous montre comment ajouter la prise en charge des signets. Pour ce faire, vous devez effectuer les étapes suivantes dans la classe d’enregistrement utilisateur :

- Instanciez les signets. Il s’agit d’objets de type [CBookmark](../../data/oledb/cbookmark-class.md).

- Demandez une colonne de signet à partir du fournisseur en définissant la propriété `DBPROP_IRowsetLocate`.

- Ajoutez une entrée de signet dans le mappage de colonnes à l’aide de la macro [BOOKMARK_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#bookmark_entry).

Grâce aux étapes précédentes, vous disposez de la prise en charge des signets et d’un objet signet avec lequel vous pouvez travailler. Cet exemple de code montre un signet comme suit :

- Ouvrez un fichier en écriture.

- Sortez les données d’ensemble de lignes dans le fichier ligne par ligne.

- Déplacez le curseur de l’ensemble de lignes vers le signet en appelant [MoveToBookmark](./crowset-class.md#movetobookmark).

- Sortez la ligne marquée par un signet et ajoutez-la à la fin du fichier.

> [!NOTE]
> Si vous utilisez cette application consommateur pour tester l’exemple d’application de fournisseur `Provider`, ignorez la prise en charge de signet décrite dans cette section.

### <a name="to-instantiate-the-bookmark"></a>Pour instancier le signet

1. L’accesseur doit contenir un objet de type [CBookmark](../../data/oledb/cbookmark-class.md). Le paramètre *nSize* spécifie la taille de la mémoire tampon du signet en octets (généralement 4 pour les plateformes 32 bits et 8 pour les plateformes 64 bits). Ajoutez la déclaration suivante pour les membres de données de colonne dans la classe d’enregistrement utilisateur :

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>Pour demander une colonne de signet à partir du fournisseur

1. Ajoutez le code suivant dans la classe d’enregistrement utilisateur en suivant la méthode `GetRowsetProperties` :

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Pour ajouter une entrée de signet dans le mappage de colonnes

1. Ajoutez l’entrée suivante au mappage de colonne dans la classe d’enregistrement :

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>Pour ajouter un signet dans votre code principal

1. Dans le fichier `MyCons.cpp` de l’application de console que vous avez créée précédemment, modifiez le code principal comme suit. Pour utiliser des signets, le code principal doit instancier son propre objet signet (`myBookmark`). Il s’agit d’un signet différent de celui de l’accesseur (`m_bookmark`).

    ```cpp
    ///////////////////////////////////////////////////////////////////////
    // MyCons.cpp : Defines the entry point for the console application.
    //

    #include "stdafx.h"
    #include "Products.h"
    #include <iostream>
    #include <fstream>
    using namespace std;

    int _tmain(int argc, _TCHAR* argv[])
    {
       HRESULT hr = CoInitialize(NULL);

       // Instantiate rowset
       CProducts rs;

       hr = rs.OpenAll();
       hr = rs.MoveFirst();

       // Cast CURRENCY m_UnitPrice to a long value
       LONGLONG lPrice = rs.m_UnitPrice.int64;

       // Open file output.txt for writing in overwrite mode
       ofstream outfile( "C:\\output.txt", ios::out );

       if (!outfile)      // Test for invalid file
          return -1;

       // Instantiate a bookmark object myBookmark for the main code
       CBookmark<4> myBookmark;
       int nCounter = 0;

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "initial row dump" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          // Output the column information for each row
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       rs.CloseAll();
       CoUninitialize();

       return 0;
    }
    ```

Pour plus d’informations sur les signets, consultez [Utilisation des signets](../../data/oledb/using-bookmarks.md). Des exemples de signets sont également affichés dans [Mise à jour des ensembles de lignes](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Création d’un consommateur OLE DB à l’aide d’un Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
