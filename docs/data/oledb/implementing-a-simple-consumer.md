---
title: Implémentation d’un consommateur Simple | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 681aa3ef5a1434ab191854f23a9e7bc908b65728
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082415"
---
# <a name="implementing-a-simple-consumer"></a>Implémentation d'un consommateur simple

Les rubriques suivantes montrent comment modifier les fichiers créés par l’Assistant Application MFC et l’Assistant Consommateur OLE DB pour créer un consommateur simple. Cet exemple comporte les parties suivantes :  
  
- « Récupération de données avec le consommateur » montre comment implémenter le code dans le consommateur qui lit toutes les données, ligne par ligne, à partir d’une table de base de données.  
  
- « Ajout de signet prennent en charge pour le consommateur » explique comment ajouter la prise en charge de signet au consommateur.  
  
- « Ajout de prise en charge XML au consommateur » montre comment modifier le code de consommateur pour exporter les données de l’ensemble de lignes récupérées en tant que données XML.  
  
> [!NOTE]
>  Vous pouvez utiliser l’application consommateur décrite dans cette section pour tester les exemples de fournisseurs MyProv et Provider.  
  
> [!NOTE]
>  Pour créer une application consommateur pour tester MyProv (le même fournisseur décrit dans [amélioration du fournisseur en lecture seule Simple](../../data/oledb/enhancing-the-simple-read-only-provider.md)), vous devez inclure la prise en charge de signet comme décrit dans « Ajout de la prise en charge de signet au consommateur ».  
  
> [!NOTE]
>  Pour générer une application consommateur pour tester le fournisseur, omettez la prise en charge de signet décrite dans « Ajout de signet prennent en charge au consommateur » et passez à « Ajout de la prise en charge XML au consommateur ».  
  
## <a name="retrieving-data-with-the-consumer"></a>Récupération des données avec le consommateur  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Pour modifier l’application de console pour utiliser le consommateur OLE DB  
  
1. Dans MyCons.cpp, modifiez le code principal en insérant le texte en gras comme suit :  
  
    ```cpp  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
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
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Ajout de prise en charge de signet au consommateur  

Un signet est une colonne qui identifie de façon unique les lignes dans la table. En général, c’est la colonne clé, mais pas toujours ; Il est spécifique au fournisseur. Cette section vous montre comment ajouter la prise en charge du signet. Pour ce faire, vous devez effectuer les opérations suivantes dans la classe d’enregistrement utilisateur :  
  
- Instanciez les signets. Il s’agit d’objets de type [CBookmark](../../data/oledb/cbookmark-class.md).  
  
- Demander une colonne de signet à partir du fournisseur en définissant le `DBPROP_IRowsetLocate` propriété.  
  
- Ajouter une entrée de signet dans le mappage de colonnes à l’aide de la [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) macro.  
  
Les étapes précédentes vous donnent de prise en charge du signet et un objet signet avec lequel travailler. Cet exemple de code montre un signet comme suit :  
  
- Ouvrez un fichier en écriture.  
  
- Données d’ensemble de lignes de sortie dans le fichier ligne par ligne.  
  
- Déplacer le curseur de l’ensemble de lignes vers le signet en appelant [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).  
  
- La ligne marquée par un signet, ajouter à la fin du fichier de sortie.  
  
> [!NOTE]
>  Si vous utilisez cette application consommateur pour tester l’application fournisseur exemple provider, abandonnez la prise en charge de signet décrite dans cette section.  
  
#### <a name="to-instantiate-the-bookmark"></a>Pour instancier le signet  
  
1. L’accesseur doit contenir un objet de type [CBookmark](../../data/oledb/cbookmark-class.md). Le *nSize* paramètre spécifie la taille de la mémoire tampon de signet en octets (généralement, 4 pour les plateformes 32 bits) et 8 pour les plateformes 64 bits. Ajoutez la déclaration suivante pour les membres de données de colonne dans la classe d’enregistrement utilisateur :  
  
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
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>Pour demander une colonne de signet à partir du fournisseur  
  
1. Ajoutez le code suivant dans le `GetRowsetProperties` méthode dans la classe d’enregistrement utilisateur :  
  
    ```cpp  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Pour ajouter une entrée de signet dans le mappage de colonnes  
  
1. Ajoutez l’entrée suivante au mappage de colonnes dans la classe d’enregistrement utilisateur :  
  
    ```cpp  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Pour ajouter un signet dans votre code principal  
  
1. Dans le fichier MyCons.cpp à partir de l’application de console que vous avez créé précédemment, modifiez le code principal comme suit. Pour utiliser des signets, le code principal doit instancier son propre objet signet (`myBookmark`) ; il s’agit d’un signet différent de celui de l’accesseur (`m_bookmark`).  
  
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
             myBookmark = rs.bookmark;  
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
  
Pour plus d’informations sur les signets, consultez [à l’aide de signets](../../data/oledb/using-bookmarks.md). Exemples de signets sont également affichées dans [ensembles de lignes de la mise à jour](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Ajout de prise en charge XML au consommateur  

Comme indiqué dans [accès aux données XML](../../data/oledb/accessing-xml-data.md), il existe deux façons de récupérer des données XML à partir d’une source de données : à l’aide de [CStreamRowset](../../data/oledb/cstreamrowset-class.md) ou à l’aide de [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). Cet exemple utilise `CStreamRowset`, qui est plus efficace, mais nécessite que vous disposiez de SQL Server 2000 est en cours d’exécution sur l’ordinateur sur lequel vous exécutez cet exemple d’application.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Pour modifier la classe de commande d’hériter de CStreamRowset  
  
1. Dans l’application consommateur que vous avez créé précédemment, modifiez votre `CCommand` déclaration pour spécifier `CStreamRowset` en tant que l’ensemble de lignes de classe comme suit :  
  
    ```cpp  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Pour modifier le code principal pour récupérer et de sortie des données XML  
  
1. Dans le fichier MyCons.cpp à partir de l’application de console que vous avez créé précédemment, modifiez le code principal comme suit :  
  
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
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
          HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  

[Création d’un consommateur OLE DB en utilisant l’Assistant](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)