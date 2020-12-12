---
description: 'En savoir plus sur : utilisation de plusieurs accesseurs sur un ensemble de lignes'
title: Utilisation de plusieurs accesseurs dans un jeu de lignes
ms.date: 10/24/2018
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
ms.openlocfilehash: 2fa8ca7737872b16abb5bfdf6a7ef6b8a38c5f85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319129"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Utilisation de plusieurs accesseurs dans un jeu de lignes

Il existe trois scénarios de base dans lesquels vous devez utiliser plusieurs accesseurs :

- **Ensembles de lignes de lecture/écriture multiples.** Dans ce scénario, vous disposez d’une table avec une clé primaire. Vous souhaitez pouvoir lire toutes les colonnes de la ligne, y compris la clé primaire. Vous pouvez également être en mesure d’écrire des données dans toutes les colonnes à l’exception de la clé primaire (car vous ne pouvez pas écrire dans la colonne de clé primaire). Dans ce cas, vous configurez deux accesseurs :

  - L’accesseur 0 contient toutes les colonnes.

  - L’accesseur 1 contient toutes les colonnes à l’exception de la clé primaire.

- **Niveau de performance.** Dans ce scénario, une ou plusieurs colonnes ont une grande quantité de données, par exemple, des fichiers graphiques, audio ou vidéo. Chaque fois que vous passez à une ligne, vous ne souhaitez probablement pas récupérer la colonne avec le fichier de données volumineux, car cela ralentirait les performances de votre application.

  Vous pouvez configurer des accesseurs distincts dans lesquels le premier accesseur contient toutes les colonnes à l’exception de celle contenant des données volumineuses, et il récupère automatiquement les données de ces colonnes. le premier accesseur est l’accesseur automatique. Le deuxième accesseur récupère uniquement la colonne contenant des données volumineuses, mais il ne récupère pas automatiquement les données de cette colonne. Vous pouvez avoir d’autres méthodes qui mettent à jour ou récupèrent les données volumineuses à la demande.

  - L’accesseur 0 est un accesseur automatique ; elle récupère toutes les colonnes à l’exception de celles contenant des données volumineuses.

  - L’accesseur 1 n’est pas un accesseur automatique ; Il récupère la colonne contenant des données volumineuses.

  Utilisez l’argument auto pour spécifier si l’accesseur est un accesseur automatique.

- **Plusieurs colonnes ISequentialStream.** Dans ce scénario, vous avez plus d’une colonne contenant des `ISequentialStream` données. Toutefois, chaque accesseur est limité à un `ISequentialStream` flux de données. Pour résoudre ce problème, configurez plusieurs accesseurs, chacun d’entre eux ayant un `ISequentialStream` pointeur.

Normalement, vous créez des accesseurs à l’aide des macros [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) et [END_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#end_accessor) . Vous pouvez également utiliser l’attribut [db_accessor](../../windows/attributes/db-accessor.md) . (Les accesseurs sont décrits plus en détail dans les [enregistrements utilisateur](../../data/oledb/user-records.md).) Les macros ou l’attribut spécifient si un accesseur est un accesseur automatique ou non automatique :

- Dans un accesseur automatique, déplacez les méthodes telles que `MoveFirst` ,, `MoveLast` `MoveNext` et `MovePrev` récupérez automatiquement des données pour toutes les colonnes spécifiées. L’accesseur 0 doit être l’accesseur automatique.

- Dans un accesseur non automatique, la récupération ne se produit pas tant que vous n’appelez pas explicitement une méthode telle que `Update` , `Insert` , `Fetch` ou `Delete` . Dans les scénarios décrits ci-dessus, il est possible que vous ne souhaitiez pas récupérer toutes les colonnes à chaque déplacement. Vous pouvez placer une ou plusieurs colonnes dans un accesseur séparé et en faire un accesseur non automatique, comme indiqué ci-dessous.

L’exemple suivant utilise plusieurs accesseurs pour lire et écrire dans la table jobs de la base de données SQL Server pubs à l’aide de plusieurs accesseurs. Cet exemple est l’utilisation la plus courante de plusieurs accesseurs. consultez le scénario « plusieurs ensembles de lignes en lecture/écriture » ci-dessus.

La classe d’enregistrement utilisateur est la suivante. Il configure deux accesseurs : l’accesseur 0 contient uniquement la colonne de clé primaire (ID) et l’accesseur 1 contient d’autres colonnes.

```cpp
class CJobs
{
public:
    enum {
        sizeOfDescription = 51
    };

    short nID;
    char szDescription[ sizeOfDescription ];
    short nMinLvl;
    short nMaxLvl;

    DWORD dwID;
    DWORD dwDescription;
    DWORD dwMinLvl;
    DWORD dwMaxLvl;

BEGIN_ACCESSOR_MAP(CJobs, 2)
    // Accessor 0 is the automatic accessor
    BEGIN_ACCESSOR(0, true)
        COLUMN_ENTRY_STATUS(1, nID, dwID)
    END_ACCESSOR()
    // Accessor 1 is the non-automatic accessor
    BEGIN_ACCESSOR(1, true)
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)
    END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

Le code principal est le suivant. L’appel `MoveNext` de récupère automatiquement les données de l’ID de colonne de clé primaire à l’aide de l’accesseur 0. Notez que la `Insert` méthode proche de la fin utilise l’accesseur 1 pour éviter d’écrire dans la colonne de clé primaire.

```cpp
int main(int argc, char* argv[])
{
    // Initialize COM
    ::CoInitialize(NULL);

    // Create instances of the data source and session
    CDataSource source;
    CSession session;
    HRESULT hr = S_OK;

    // Set initialization properties
    CDBPropSet dbinit(DBPROPSET_DBINIT);
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));

    hr = source.Open("SQLOLEDB.1", &dbinit);
    if (hr == S_OK)
    {
        hr = session.Open(source);
        if (hr == S_OK)
        {
            // Ready to fetch/access data
            CTable<CAccessor<CJobs>> jobs;

            // Set properties for making the rowset a read/write cursor
            CDBPropSet dbRowset(DBPROPSET_ROWSET);
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);
            dbRowset.AddProperty(DBPROP_UPDATABILITY,
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |
                DBPROPVAL_UP_DELETE);

            hr = jobs.Open(session, "jobs", &dbRowset);
            if (hr == S_OK)
            {
                // Calling MoveNext automatically retrieves ID
                // (using accessor 0)
                while(jobs.MoveNext() == S_OK)
                   printf_s("Description = %s\n", jobs.szDescription);

                hr = jobs.MoveFirst();
                if (hr == S_OK)
                {
                    jobs.nID = 25;
                    strcpy_s(&jobs.szDescription[0],
                             jobs.sizeOfDescription,
                             "Developer");
                    jobs.nMinLvl = 10;
                    jobs.nMaxLvl = 20;

                    jobs.dwDescription = DBSTATUS_S_OK;
                    jobs.dwID = DBSTATUS_S_OK;
                    jobs.dwMaxLvl = DBSTATUS_S_OK;
                    jobs.dwMinLvl = DBSTATUS_S_OK;

                    // Insert method uses accessor 1
                    // (to avoid writing to the primary key column)
                    hr = jobs.Insert(1);
                }
                jobs.Close();
            }
            session.Close();
        }
        source.Close();
    }

    // Uninitialize COM
    ::CoUninitialize();
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)<br/>
[Enregistrements utilisateur](../../data/oledb/user-records.md)
