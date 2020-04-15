---
title: CDataConnection, classe
ms.date: 03/27/2019
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
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368615"
---
# <a name="cdataconnection-class"></a>CDataConnection, classe

Gère la connexion avec la source de données.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataConnection
```

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CDataConnection (en)](#cdataconnection)|Constructeur. Instantanéise et initialise `CDataConnection` un objet.|
|[Copier](#copy)|Crée une copie d’une connexion de données existante.|
|[Ouvrir](#open)|Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.|
|[OpenNewSession](#opennewsession)|Ouvre une nouvelle session sur la connexion actuelle.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur BOOL](#op_bool)|Détermine si la session en cours est ouverte ou non.|
|[bool opérateur](#op_bool_ole)|Détermine si la session en cours est ouverte ou non.|
|[l’opérateur CDataSource&](#op_cdata_amp)|Renvoie une référence `CDataSource` à l’objet contenu.|
|[opérateur CDataSourceMD](#op_cdata_star)|Renvoie un pointeur à l’objet contenu. `CDataSource`|
|[l’opérateur CSession&](#op_csession_amp)|Renvoie une référence `CSession` à l’objet contenu.|
|[opérateur CSession*](#op_csession_star)|Renvoie un pointeur à l’objet contenu. `CSession`|

## <a name="remarks"></a>Notes

`CDataConnection`est une classe utile pour créer des clients parce qu’elle résume les objets nécessaires (source de données et session) et une partie du travail que vous devez faire lors de la connexion à une source de données

Sans, `CDataConnection`vous devez `CDataSource` créer un objet, appeler sa méthode [OpenFromInitializationString,](../../data/oledb/cdatasource-openfrominitializationstring.md) puis créer une instance d’un objet [CSession,](../../data/oledb/csession-class.md) appeler sa méthode [Ouverte,](../../data/oledb/csession-open.md) puis créer un objet [CCommand](../../data/oledb/ccommand-class.md) et appeler ses `Open`méthodes.

Avec `CDataConnection`, vous avez seulement besoin de créer un objet de connexion, lui passer une chaîne d’initialisation, puis utiliser cette connexion pour ouvrir des commandes. Si vous prévoyez d’utiliser votre connexion à la base de données `CDataConnection` à plusieurs reprises, il est une bonne idée de garder la connexion ouverte, et fournit un moyen pratique de le faire.

> [!NOTE]
> Si vous créez une application de base de données qui doit gérer plusieurs sessions, vous devrez utiliser [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection::CDataConnection

Instantanéise et initialise `CDataConnection` un objet.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Paramètres

*Ds*<br/>
[dans] Une référence à une connexion de données existante.

### <a name="remarks"></a>Notes

Le premier remplacement crée `CDataConnection` un nouvel objet avec des paramètres par défaut.

Le deuxième remplacement crée `CDataConnection` un nouvel objet avec des paramètres équivalents à l’objet de connexion de données que vous spécifiez.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection::Copie

Crée une copie d’une connexion de données existante.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Paramètres

*Ds*<br/>
[dans] Une référence à une connexion de données existante à copier.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection::Ouvert

Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitString*<br/>
[dans] La chaîne d’initialisation pour la source de données.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection::OpenNewSession

Ouvre une nouvelle session à l’aide de la source de données de l’objet de connexion actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Paramètres

*Session*<br/>
[dans/out] Une référence au nouvel objet de session.

### <a name="remarks"></a>Notes

La nouvelle session utilise l’objet source de données contenu de l’objet de connexion actuel comme parent, et peut accéder à toutes les mêmes informations que la source de données.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection::opérateur BOOL

Détermine si la session en cours est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur **BOOL** (MFC typdef). **TRUE** signifie que la session en cours est ouverte; **FALSE** signifie que la session en cours est terminée.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection::opérateur bool (OLE DB)

Détermine si la session en cours est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Notes

Retourne une valeur **bool** (type de données CD). **signifie vrai** que la session en cours est ouverte; **faux** signifie que la session en cours est fermée.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection::opérateur CDataSource&amp;

Renvoie une référence `CDataSource` à l’objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur renvoie une `CDataSource` référence à l’objet `CDataConnection` contenu, `CDataSource` vous permettant de passer un objet où une référence est attendue.

### <a name="example"></a>Exemple

Si vous avez une `func` fonction (comme `CDataSource` ci-dessous) `CDataSource&` qui prend `CDataConnection` une référence, vous pouvez utiliser pour passer un objet à la place.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection::opérateur CDataSource

Renvoie un pointeur à l’objet contenu. `CDataSource`

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur renvoie un `CDataSource` pointeur à l’objet contenu, vous permettant de passer un `CDataConnection` objet où un `CDataSource` pointeur est attendu.

Voir [l’opérateur CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) pour un exemple d’utilisation.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection::opérateur CSession&amp;

Renvoie une référence `CSession` à l’objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Notes

Cet opérateur renvoie une `CSession` référence à l’objet `CDataConnection` contenu, `CSession` vous permettant de passer un objet où une référence est attendue.

### <a name="example"></a>Exemple

Si vous avez une `func` fonction (comme `CSession` ci-dessous) `CSession&` qui prend `CDataConnection` une référence, vous pouvez utiliser pour passer un objet à la place.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection::opérateur CSession

Renvoie un pointeur à l’objet contenu. `CSession`

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur renvoie un `CSession` pointeur à l’objet contenu, vous permettant de passer un `CDataConnection` objet où un `CSession` pointeur est attendu.

### <a name="example"></a>Exemple

Voir [l’opérateur CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) pour un exemple d’utilisation.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB Consumer Templates Référence](../../data/oledb/ole-db-consumer-templates-reference.md)
