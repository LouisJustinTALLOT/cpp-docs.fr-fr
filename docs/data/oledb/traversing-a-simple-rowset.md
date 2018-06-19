---
title: Parcours d’un ensemble de lignes Simple | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data access [C++], rowsets
- rowsets [C++], accessing
- simple rowsets
- OLE DB consumers [C++], database attributes
- accessors [C++], rowsets
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a29d7a226d12f9c464d91ec356ae8a1a02091f1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102949"
---
# <a name="traversing-a-simple-rowset"></a>Parcours d'un jeu de lignes simple
L’exemple suivant montre un accès simple et rapide de la base de données qui n’implique pas de commandes. Le code de consommateur suivant, dans un projet ATL, extrait des enregistrements à partir d’une table appelée *artistes* Microsoft Access, une base de données à l’aide du fournisseur Microsoft OLE DB pour ODBC. Le code crée un [CTable](../../data/oledb/ctable-class.md) objet de table avec un accesseur basé sur la classe d’enregistrement utilisateur `CArtists`. Ouvre une connexion, ouvre une session sur la connexion et la table s’ouvre sur la session.  
  
```  
#include <atldbcli.h>  
  
CDataSource connection;  
CSession session;  
CTable<CAccessor<CArtists>> artists;  
  
// Open the connection, session, and table, specifying authentication   
// using Windows NT integrated security. Hard-coding a password is a major  
// security weakness.  
connection.Open(CLSID_MSDASQL, "NWind", NULL, NULL, DBPROP_AUTH_INTEGRATED);  

session.Open(connection);  

artists.Open(session, "Artists");  
  
// Get data from the rowset  
while (artists.MoveNext() == S_OK)  
{  
   cout << artists.m_szFirstName;  
   cout << artists.m_szLastName;  
}  
```  
  
 L’enregistrement d’utilisateur, `CArtists`, ressemble à ceci :  
  
```  
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
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du consommateur OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)