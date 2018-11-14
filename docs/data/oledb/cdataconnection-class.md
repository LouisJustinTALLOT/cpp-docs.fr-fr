---
title: CDataConnection, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 8a419a19c04b579c72df9938151f9ada657178f2
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326535"
---
# <a name="cdataconnection-class"></a>CDataConnection, classe

Gère la connexion avec la source de données.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CDataConnection](#cdataconnection)|Constructeur. Instancie et initialise un `CDataConnection` objet.|
|[Copier](#copy)|Crée une copie d’une connexion de données existante.|
|[Ouvrir](#open)|Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.|
|[OpenNewSession](#opennewsession)|Ouvre une nouvelle session sur la connexion actuelle.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur BOOL](#op_bool)|Détermine si la session active est ouverte ou non.|
|[operator bool](#op_bool_ole)|Détermine si la session active est ouverte ou non.|
|[opérateur CDataSource &](#op_cdata_amp)|Retourne une référence à la relation contenant-contenu `CDataSource` objet.|
|[opérateur CDataSource *](#op_cdata_star)|Retourne un pointeur vers la relation contenant-contenu `CDataSource` objet.|
|[opérateur CSession &](#op_csession_amp)|Retourne une référence à la relation contenant-contenu `CSession` objet.|
|[opérateur CSession *](#op_csession_star)|Retourne un pointeur vers la relation contenant-contenu `CSession` objet.|

## <a name="remarks"></a>Notes

`CDataConnection` classe est utile pour créer des clients, car elle encapsule les objets nécessaires (source de données et session) et la partie du travail, que vous devez effectuer lors de la connexion à une source de données

Sans `CDataConnection`, vous devez créer un `CDataSource` d’objet, appelez sa [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) (méthode), puis créez une instance d’un [CSession](../../data/oledb/csession-class.md) de l’objet, appelez sa [ Ouvrez](../../data/oledb/csession-open.md) (méthode), puis créer un [CCommand](../../data/oledb/ccommand-class.md) objet et appelez ses `Open`* méthodes.

Avec `CDataConnection`, il vous suffit de créer un objet de connexion, de passer une chaîne d’initialisation, puis utiliser cette connexion pour ouvrir les commandes. Si vous prévoyez d’utiliser votre connexion à la base de données à plusieurs reprises, il est judicieux de conserver la connexion ouverte, et `CDataConnection` offre un moyen pratique pour ce faire.

> [!NOTE]
>  Si vous créez une application de base de données qui doit gérer plusieurs sessions, vous devrez utiliser [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="#cdataconnection"></a> CDataConnection::CDataConnection

Instancie et initialise un `CDataConnection` objet.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Paramètres

*service d’annuaire*<br/>
[in] Une référence à une connexion de données existante.

### <a name="remarks"></a>Notes

Le premier remplacement crée un nouveau `CDataConnection` objet avec les paramètres par défaut.

Le deuxième remplacement crée un nouveau `CDataConnection` objet avec les paramètres équivalents à l’objet de connexion de données que vous spécifiez.

## <a name="#copy"></a> CDataConnection::Copy

Crée une copie d’une connexion de données existante.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Paramètres

*service d’annuaire*<br/>
[in] Une référence à une connexion de données existante à copier.

## <a name="#open"></a> CDataConnection::Open

Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitString*<br/>
[in] La chaîne d’initialisation pour la source de données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="#opennewsession"></a> CDataConnection::OpenNewSession

Ouvre une nouvelle session à l’aide de la source de données de l’objet de connexion en cours.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
[entrée/sortie] Une référence à l’objet de la nouvelle session.

### <a name="remarks"></a>Notes

La nouvelle session utilise un objet de source de données de relation contenant-contenu de l’objet de connexion en cours en tant que son parent et peut accéder à tous les mêmes informations que la source de données.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="op_bool"></a> CDataConnection::operator BOOL

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Notes

Retourne **BOOL** (MFC typedef) valeur. **TRUE** signifie que la session active est ouverte ; **FALSE** signifie que la session active est fermée.

## <a name="op_bool_ole"></a> CDataConnection::operator bool (OLE DB)

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Notes

Retourne un **bool** valeur (type de données C++). **true** signifie que la session active est ouverte ; **false** signifie que la session active est fermée.

## <a name="op_cdata_amp"></a> CDataConnection::operator CDataSource&amp;

Retourne une référence à la relation contenant-contenu `CDataSource` objet.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à la relation contenant-contenu `CDataSource` objet, ce qui vous permet de transmettre un `CDataConnection` objet où un `CDataSource` référence est attendue.

### <a name="example"></a>Exemple

Si vous disposez d’une fonction (tel que `func` ci-dessous) qui prend un `CDataSource` référence, vous pouvez utiliser `CDataSource&` à passer un `CDataConnection` à la place de l’objet.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> CDataConnection::operator CDataSource *

Retourne un pointeur vers la relation contenant-contenu `CDataSource` objet.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers la relation contenant-contenu `CDataSource` objet, ce qui vous permet de transmettre un `CDataConnection` objet où un `CDataSource` pointeur est attendu.

Consultez [opérateur CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) pour un exemple d’utilisation.

## <a name="op_csession_amp"></a> CDataConnection::operator CSession&amp;

Retourne une référence à la relation contenant-contenu `CSession` objet.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à la relation contenant-contenu `CSession` objet, ce qui vous permet de transmettre un `CDataConnection` objet où un `CSession` référence est attendue.

### <a name="example"></a>Exemple

Si vous disposez d’une fonction (tel que `func` ci-dessous) qui prend un `CSession` référence, vous pouvez utiliser `CSession&` à passer un `CDataConnection` à la place de l’objet.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> CDataConnection::operator CSession *

Retourne un pointeur vers la relation contenant-contenu `CSession` objet.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers la relation contenant-contenu `CSession` objet, ce qui vous permet de transmettre un `CDataConnection` objet où un `CSession` pointeur est attendu.

### <a name="example"></a>Exemple

Consultez [opérateur CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) pour un exemple d’utilisation.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)