---
description: 'En savoir plus sur : émission d’une requête paramétrable'
title: Émission d'une requête paramétrée
ms.date: 10/19/2018
helpviewer_keywords:
- parameter queries, running using CCommand class
ms.assetid: aedb0fce-52a4-4c97-a5c9-b2114be6c3b0
ms.openlocfilehash: 2d3f03a359fe3ce079239fdcb9603b2d30299c33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317231"
---
# <a name="issuing-a-parameterized-query"></a>Émission d'une requête paramétrée

L’exemple suivant présente une requête paramétrable simple qui extrait des enregistrements avec un champ d’âge (supérieur à 30) à partir d’une table dans une base de données Microsoft Access. Pour prendre en charge le paramètre, l’enregistrement de l’utilisateur doit avoir un mappage supplémentaire. Dans un projet ATL, le code suivant utilise la `CCommand` classe au lieu de la `CTable` classe utilisée dans l’exemple précédent, en [parcourant un ensemble de lignes simple](../../data/oledb/traversing-a-simple-rowset.md).

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CCommand<CAccessor<CArtists>> artists;
    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    // Set the parameter for the query
    artists.m_nAge = 30;
    artists.Open(session, "select * from artists where age > ?");

    // Get data from the rowset
    while (artists.MoveNext() == S_OK)
    {
        cout << artists.m_szFirstName;
        cout << artists.m_szLastName;
    }

    return 0;
}
```

L’enregistrement utilisateur, `CArtists` , ressemble à cet exemple :

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de consommateurs OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
