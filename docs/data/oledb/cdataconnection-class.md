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
ms.openlocfilehash: c456f4bf5891f550fcd9523fa376333d66e079a6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509099"
---
# <a name="cdataconnection-class"></a>CDataConnection, classe

Gère la connexion à la source de données.

## <a name="syntax"></a>Syntax

```cpp
class CDataConnection
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[CDataConnection](#cdataconnection)|Constructeur. Instancie et initialise un `CDataConnection` objet.|
|[Copier](#copy)|Crée une copie d’une connexion de données existante.|
|[Ouvrir](#open)|Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.|
|[OpenNewSession](#opennewsession)|Ouvre une nouvelle session sur la connexion actuelle.|

### <a name="operators"></a>Opérateurs

| Nom | Description |
|-|-|
|[BOOL, opérateur](#op_bool)|Détermine si la session active est ouverte ou non.|
|[bool, opérateur](#op_bool_ole)|Détermine si la session active est ouverte ou non.|
|[&CDataSource, opérateur ](#op_cdata_amp)|Retourne une référence à l' `CDataSource` objet contenu.|
|[opérateur CDataSource *](#op_cdata_star)|Retourne un pointeur vers l' `CDataSource` objet contenu.|
|[&opérateur CSession ](#op_csession_amp)|Retourne une référence à l' `CSession` objet contenu.|
|[opérateur CSession*](#op_csession_star)|Retourne un pointeur vers l' `CSession` objet contenu.|

## <a name="remarks"></a>Remarques

`CDataConnection` est une classe utile pour créer des clients, car elle encapsule des objets nécessaires (source de données et session) et une partie du travail que vous devez effectuer lors de la connexion à une source de données

Sans `CDataConnection` , vous devez créer un `CDataSource` objet, appeler sa méthode [OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring) , puis créer une instance d’un objet [CSession](../../data/oledb/csession-class.md) , appeler sa méthode [Open](./csession-class.md#open) , puis créer un objet [CCommand](../../data/oledb/ccommand-class.md) et appeler ses `Open` méthodes *.

Avec `CDataConnection` , il vous suffit de créer un objet de connexion, de lui transmettre une chaîne d’initialisation, puis d’utiliser cette connexion pour ouvrir les commandes. Si vous envisagez d’utiliser votre connexion à la base de données à plusieurs reprises, il est judicieux de garder la connexion ouverte et de vous `CDataConnection` offrir un moyen pratique de le faire.

> [!NOTE]
> Si vous créez une application de base de données qui doit gérer plusieurs sessions, vous devez utiliser [OpenNewSession](#opennewsession).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a> CDataConnection :: CDataConnection

Instancie et initialise un `CDataConnection` objet.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Paramètres

*SD*<br/>
dans Référence à une connexion de données existante.

### <a name="remarks"></a>Remarques

La première substitution crée un nouvel `CDataConnection` objet avec les paramètres par défaut.

Le deuxième remplacement crée un `CDataConnection` objet avec des paramètres équivalant à l’objet de connexion de données que vous spécifiez.

## <a name="cdataconnectioncopy"></a><a name="copy"></a> CDataConnection :: Copy

Crée une copie d’une connexion de données existante.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Paramètres

*SD*<br/>
dans Référence à une connexion de données existante à copier.

## <a name="cdataconnectionopen"></a><a name="open"></a> CDataConnection :: Open

Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitString*<br/>
dans Chaîne d’initialisation de la source de données.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a> CDataConnection :: OpenNewSession

Ouvre une nouvelle session à l’aide de la source de données de l’objet de connexion actuel.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
[in/out] Référence au nouvel objet de session.

### <a name="remarks"></a>Remarques

La nouvelle session utilise l’objet de source de données contenu de l’objet de connexion en cours comme parent et peut accéder à toutes les mêmes informations que la source de données.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a> CDataConnection :: Operator BOOL

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur **bool** (typedef MFC). **True** signifie que la session active est ouverte ; **False** signifie que la session active est fermée.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a> CDataConnection :: operator bool (OLE DB)

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Notes

Retourne une **`bool`** valeur (type de données C++). **`true`** signifie que la session active est ouverte ; **`false`** signifie que la session active est fermée.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a> CDataConnection :: Operator CDataSource&amp;

Retourne une référence à l' `CDataSource` objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à l' `CDataSource` objet contenu, ce qui vous permet de passer un `CDataConnection` objet où une `CDataSource` référence est attendue.

### <a name="example"></a>Exemple

Si vous disposez d’une fonction (comme `func` ci-dessous) qui prend une `CDataSource` référence, vous pouvez utiliser `CDataSource&` pour passer un objet à la `CDataConnection` place.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a> CDataConnection :: Operator CDataSource *

Retourne un pointeur vers l' `CDataSource` objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers l' `CDataSource` objet contenu, ce qui vous permet de passer un `CDataConnection` objet où un `CDataSource` pointeur est attendu.

Pour obtenir un exemple d’utilisation, consultez [Operator CDataSource&](#op_cdata_amp) .

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a> CDataConnection :: Operator CSession&amp;

Retourne une référence à l' `CSession` objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à l' `CSession` objet contenu, ce qui vous permet de passer un `CDataConnection` objet où une `CSession` référence est attendue.

### <a name="example"></a>Exemple

Si vous disposez d’une fonction (comme `func` ci-dessous) qui prend une `CSession` référence, vous pouvez utiliser `CSession&` pour passer un objet à la `CDataConnection` place.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a> CDataConnection :: Operator CSession *

Retourne un pointeur vers l' `CSession` objet contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers l' `CSession` objet contenu, ce qui vous permet de passer un `CDataConnection` objet où un `CSession` pointeur est attendu.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation, consultez [opérateur CSession&](#op_csession_amp) .

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
