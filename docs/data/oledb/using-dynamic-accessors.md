---
title: "Utilisation d’accesseurs dynamiques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a585605b4b89d55e136aa349e697e0c19c93974f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="using-dynamic-accessors"></a>Utilisation d’accesseurs dynamiques
Accesseurs dynamiques permettent d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente). La bibliothèque de modèles OLE DB fournit plusieurs classes pour ce faire.  
  
 Le [DynamicConsumer](http://msdn.microsoft.com/en-us/2ccc4c61-6749-4e83-aa81-00f8009c0dc3) montre comment utiliser les classes d’accesseurs dynamiques pour obtenir des informations sur les colonnes et créer des accesseurs de manière dynamique.  
  
## <a name="using-cdynamicaccessor"></a>Utilisation de CDynamicAccessor  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente de la base de données). `CDynamicAccessor` méthodes d’obtiennent des informations de colonne telles que les noms de colonne, nombre et type de données. Ces informations de colonne vous permet de créer un accesseur dynamique au moment de l’exécution. Les informations de colonne sont stockées dans une mémoire tampon qui est créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide de la [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) (méthode).  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// Using_Dynamic_Accessors.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main(int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize(NULL );  
  
    CDataSource ds;  
    CSession ss;  
  
    CTable<CDynamicAccessor> rs;  
  
    // The following is an example initialization string:  
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"  
      L"Integrated Security=SSPI;Persist Security Info=False;"  
      L"Initial Catalog=Loginname;Data Source=your_data_source;"  
      L"Use Procedure for Prepare=1;Auto Translate=True;"  
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"  
      L"Use Encryption for Data=False;"  
      L"Tag with column collation when possible=False");  
  
    hr = ss.Open(ds );  
    hr = rs.Open(ss, "Shippers" );  
  
    hr = rs.MoveFirst();  
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )  
        {  
            DBTYPE type;  
            rs.GetColumnType(i, &type );  
            printf_s( "Column %d [%S] is of type %d\n",  
                      i, rs.GetColumnName(i ), type );   
  
            switch(type )  
            {  
                case DBTYPE_WSTR:  
                    printf_s( "value is %S\n",  
                              (WCHAR*)rs.GetValue(i ) );  
                break;  
                case DBTYPE_STR:  
                    printf_s( "value is %s\n",  
                              (CHAR*)rs.GetValue(i ) );  
                default:  
                    printf_s( "value is %d\n",  
                              *(long*)rs.GetValue(i ) );  
            }  
        }  
        hr = rs.MoveNext();  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
    return 0;  
}  
```  
  
## <a name="using-cdynamicstringaccessor"></a>Utilisation de CDynamicStringAccessor  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) fonctionne comme [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), sauf sur un point important. Alors que `CDynamicAccessor` demande des données dans le format natif indiqué par le fournisseur, `CDynamicStringAccessor` demande que le fournisseur récupère toutes les données accessibles à partir du magasin de données en tant que données de type chaîne. Cela est particulièrement utile pour les tâches simples qui ne nécessitent pas de calcul de valeurs dans le magasin de données, telles que l’affichage ou l’impression du contenu du magasin de données.  
  
 Utilisez `CDynamicStringAccessor` méthodes pour obtenir des informations de colonne. Ces informations de colonne vous permet de créer un accesseur dynamique au moment de l’exécution. Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des données à partir de la mémoire tampon à l’aide de [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) ou stockez-le dans la mémoire tampon à l’aide de [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// Using_Dynamic_Accessors_b.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main(int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize(NULL );  
    if (hr != S_OK)  
    {  
        exit (-1);  
    }  
  
    CDataSource ds;  
    CSession ss;  
  
    CTable<CDynamicStringAccessor> rs;  
  
    // The following is an example initialization string:  
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"  
      L"Integrated Security=SSPI;Persist Security Info=False;"  
      L"Initial Catalog=Loginname;Data Source=your_data_source;"  
      L"Use Procedure for Prepare=1;Auto Translate=True;"  
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"  
      L"Use Encryption for Data=False;"  
      L"Tag with column collation when possible=False");  
  
    hr = ss.Open(ds );  
    hr = rs.Open(ss, "Shippers" );  
  
    hr = rs.MoveFirst();  
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )  
        {  
            printf_s( "column %d value is %s\n",   
                      i, rs.GetString(i ) );  
        }  
        hr = rs.MoveNext();  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
   return 0;  
  
}  
```  
  
## <a name="using-cdynamicparameteraccessor"></a>À l’aide de CDynamicParameterAccessor  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) est similaire à [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), sauf que `CDynamicParameterAccessor` Obtient des informations sur les paramètres à définir en appelant le [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx) interface. Le fournisseur doit prendre en charge `ICommandWithParameters` pour permettre au consommateur d’utiliser cette classe.  
  
 Les informations sur les paramètres sont stockées dans une mémoire tampon créée et gérée par cette classe. Obtenir des données de paramètre à partir de la mémoire tampon à l’aide de [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) et [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).  
  
 Pour accéder à un exemple montrant comment utiliser cette classe pour exécuter une procédure stockée SQL Server et obtenir les valeurs de paramètre de sortie, consultez l’article de la Base de connaissances Q058860 relatif à l’exécution d’une procédure stockée via CDynamicParameterAccessor. Articles de la Base de connaissances sont disponibles dans la documentation de Visual Studio de MSDN Library ou à [http://support.microsoft.com](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’accesseurs](../../data/oledb/using-accessors.md)   
 [CDynamicAccessor (classe)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [DynamicConsumer, exemple](http://msdn.microsoft.com/en-us/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)