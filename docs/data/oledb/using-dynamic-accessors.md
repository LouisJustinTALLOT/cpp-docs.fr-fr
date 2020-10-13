---
title: Utilisation d’accesseurs dynamiques
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4f42d6f20da819cf325cad06a04878b46e52352a
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008684"
---
# <a name="using-dynamic-accessors"></a>Utilisation d’accesseurs dynamiques

Les accesseurs dynamiques vous permettent d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (structure sous-jacente). La bibliothèque de modèles OLE DB fournit plusieurs classes pour vous aider.

L’exemple [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) montre comment utiliser les classes d’accesseur dynamique pour recevoir des informations sur les colonnes et créer des accesseurs de manière dynamique.

## <a name="using-cdynamicaccessor"></a>Utilisation de CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance du schéma de base de données (la structure sous-jacente de la base de données). `CDynamicAccessor` les méthodes obtiennent des informations sur les colonnes, telles que les noms de colonnes, le nombre et le type de données. Vous utilisez ces informations de colonne pour créer un accesseur de manière dynamique au moment de l’exécution. Les informations de colonne sont stockées dans une mémoire tampon qui est créée et gérée par cette classe. Obtient des données de la mémoire tampon à l’aide de la méthode [GetValue](./cdynamicaccessor-class.md#getvalue) .

## <a name="example-cdynamic-accessors"></a>Exemple : accesseurs CDynamic

```cpp
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

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) fonctionne comme [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), sauf d’une manière importante. En `CDynamicAccessor` cas de demande de données dans le format natif signalé par le fournisseur, `CDynamicStringAccessor` demande au fournisseur d’extraire toutes les données accessibles à partir du magasin de données en tant que données de chaîne. Le processus est particulièrement utile pour les tâches simples qui ne nécessitent pas de calcul de valeurs dans le magasin de données, telles que l’affichage ou l’impression du contenu du magasin de données.

Utilisez des `CDynamicStringAccessor` méthodes pour récupérer des informations sur les colonnes. Vous utilisez ces informations de colonne pour créer un accesseur de manière dynamique au moment de l’exécution. Les informations de colonne sont stockées dans une mémoire tampon créée et gérée par cette classe. Récupérez des données à partir de la mémoire tampon à l’aide de [CDynamicStringAccessor :: GetString](./cdynamicstringaccessor-class.md#getstring) ou stockez-les dans la mémoire tampon à l’aide de [CDynamicStringAccessor :: SetString](./cdynamicstringaccessor-class.md#setstring).

## <a name="example-cdynamicstringaccessor"></a>Exemple : CDynamicStringAccessor

```cpp
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

## <a name="using-cdynamicparameteraccessor"></a>Utilisation de CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) est semblable à [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), sauf que `CDynamicParameterAccessor` obtient les informations de paramètres à définir en appelant l’interface [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) . Le fournisseur doit prendre en charge `ICommandWithParameters` pour permettre au consommateur d’utiliser cette classe.

Les informations sur les paramètres sont stockées dans une mémoire tampon créée et gérée par cette classe. Récupérez les données de paramètre à partir de la mémoire tampon en utilisant [CDynamicParameterAccessor :: GetParam](./cdynamicparameteraccessor-class.md#getparam) et [CDynamicParameterAccessor :: GetParamType](./cdynamicparameteraccessor-class.md#getparamtype).

Pour obtenir un exemple montrant comment utiliser cette classe pour exécuter une SQL Server procédure stockée et obtenir les valeurs de paramètre de sortie, consultez l’exemple de code [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) dans le référentiel [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) sur GitHub.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor, classe](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor, classe](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor (classe)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer, exemple](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
