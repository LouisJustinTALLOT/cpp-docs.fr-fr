---
description: 'En savoir plus sur : parcours d’un ensemble de lignes simple'
title: Parcours d'un jeu de lignes simple
ms.date: 10/19/2018
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
ms.openlocfilehash: f2e0c1f9647e168d8de2a10eaea6425bf9ad5a88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272628"
---
# <a name="traversing-a-simple-rowset"></a>Parcours d'un jeu de lignes simple

L’exemple suivant montre un accès rapide et facile à la base de données qui n’implique pas de commandes. Dans un projet ATL, le code de consommateur suivant récupère les enregistrements d’une table appelée *Artists* dans une base de données Microsoft Access à l’aide du fournisseur Microsoft OLE DB pour ODBC. Le code crée un objet de table [CTable](../../data/oledb/ctable-class.md) avec un accesseur basé sur la classe d’enregistrement utilisateur `CArtists` . Il ouvre une connexion, ouvre une session sur la connexion et ouvre la table dans la session.

```cpp
#include <atldbcli.h>
#include <iostream>

using namespace std;

int main()
{
    CDataSource connection;
    CSession session;
    CTable<CAccessor<CArtists>> artists;

    LPCSTR clsid; // Initialize CLSID_MSDASQL here
    LPCTSTR pName = L"NWind";

    // Open the connection, session, and table, specifying authentication
    // using Windows NT integrated security. Hard-coding a password is a major
    // security weakness.
    connection.Open(clsid, pName, NULL, NULL, DBPROP_AUTH_INTEGRATED);

    session.Open(connection);

    artists.Open(session, "Artists");

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
};
```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de consommateurs OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
