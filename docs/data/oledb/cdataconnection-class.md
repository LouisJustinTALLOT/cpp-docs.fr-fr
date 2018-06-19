---
title: CDataConnection, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 945fed5edd59da93aabb1d22e4830417fc4a2518
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096793"
---
# <a name="cdataconnection-class"></a>CDataConnection, classe
Gère la connexion avec la source de données.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|Constructeur. Instancie et initialise un `CDataConnection` objet.|  
|[Copier](../../data/oledb/cdataconnection-copy.md)|Crée une copie d’une connexion de données existante.|  
|[Ouvrir](../../data/oledb/cdataconnection-open.md)|Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|Ouvre une nouvelle session sur la connexion actuelle.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur BOOL](../../data/oledb/cdataconnection-operator-bool.md)|Détermine si la session active est ouverte ou non.|  
|[operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|Détermine si la session active est ouverte ou non.|  
|[opérateur CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|Retourne une référence à la relation contenant-contenu `CDataSource` objet.|  
|[opérateur CDataSource *](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|Retourne un pointeur vers la relation contenant-contenu `CDataSource` objet.|  
|[opérateur CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)|Retourne une référence à la relation contenant-contenu `CSession` objet.|  
|[opérateur CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)|Retourne un pointeur vers la relation contenant-contenu `CSession` objet.|  
  
## <a name="remarks"></a>Notes  
 `CDataConnection` classe est utile pour la création de clients, car elle encapsule les objets nécessaires (source de données et session) et la partie du travail, que vous devez effectuer lors de la connexion à une source de données  
  
 Sans `CDataConnection`, vous devez créer un `CDataSource` de l’objet, appelez sa [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) (méthode), puis créez une instance d’un [CSession](../../data/oledb/csession-class.md) de l’objet, appelez sa [ Ouvrir](../../data/oledb/csession-open.md) (méthode), puis créer un [CCommand](../../data/oledb/ccommand-class.md) objet et appeler ses **ouvrir*** méthodes.  
  
 Avec `CDataConnection`, vous pouvez créer un objet de connexion, lui passer une chaîne d’initialisation, puis utiliser cette connexion pour ouvrir les commandes. Si vous prévoyez d’utiliser votre connexion à la base de données à plusieurs reprises, il est judicieux de conserver la connexion ouverte, et `CDataConnection` offre un moyen pratique pour ce faire.  
  
> [!NOTE]
>  Si vous créez une application de base de données qui doit gérer plusieurs sessions, vous devrez utiliser [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)