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
ms.openlocfilehash: e966ce8d0f8b277c0edde2b0b9b345a11c6a964c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442493"
---
# <a name="cdataconnection-class"></a>CDataConnection, classe

Gère la connexion à la source de données.

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
|[CDataConnection](#cdataconnection)|Constructeur. Instancie et initialise un objet `CDataConnection`.|
|[Copy](#copy)|Crée une copie d’une connexion de données existante.|
|[Ouvrir](#open)|Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.|
|[OpenNewSession](#opennewsession)|Ouvre une nouvelle session sur la connexion actuelle.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[BOOL, opérateur](#op_bool)|Détermine si la session active est ouverte ou non.|
|[operator bool](#op_bool_ole)|Détermine si la session active est ouverte ou non.|
|[& CDataSource, opérateur](#op_cdata_amp)|Retourne une référence à l’objet `CDataSource` contenu.|
|[opérateur CDataSource *](#op_cdata_star)|Retourne un pointeur désignant l’objet `CDataSource` contenu.|
|[& opérateur CSession](#op_csession_amp)|Retourne une référence à l’objet `CSession` contenu.|
|[opérateur CSession *](#op_csession_star)|Retourne un pointeur désignant l’objet `CSession` contenu.|

## <a name="remarks"></a>Notes

`CDataConnection` est une classe utile pour créer des clients, car elle encapsule les objets nécessaires (source de données et session) et une partie du travail que vous devez effectuer lors de la connexion à une source de données

Sans `CDataConnection`, vous devez créer un objet `CDataSource`, appeler sa méthode [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) , puis créer une instance d’un objet [CSession](../../data/oledb/csession-class.md) , appeler sa méthode [Open](../../data/oledb/csession-open.md) , puis créer un objet [CCommand](../../data/oledb/ccommand-class.md) et appeler ses méthodes `Open`*.

Avec `CDataConnection`, il vous suffit de créer un objet de connexion, de lui transmettre une chaîne d’initialisation, puis d’utiliser cette connexion pour ouvrir les commandes. Si vous prévoyez d’utiliser votre connexion à la base de données à plusieurs reprises, il est judicieux de garder la connexion ouverte et `CDataConnection` offre un moyen pratique de le faire.

> [!NOTE]
>  Si vous créez une application de base de données qui doit gérer plusieurs sessions, vous devez utiliser [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnection"></a>CDataConnection :: CDataConnection

Instancie et initialise un objet `CDataConnection`.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Paramètres

*SD*<br/>
dans Référence à une connexion de données existante.

### <a name="remarks"></a>Notes

La première substitution crée un objet `CDataConnection` avec les paramètres par défaut.

Le deuxième remplacement crée un nouvel objet `CDataConnection` avec des paramètres équivalents à l’objet de connexion de données que vous spécifiez.

## <a name="copy"></a>CDataConnection :: Copy

Crée une copie d’une connexion de données existante.

### <a name="syntax"></a>Syntaxe

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Paramètres

*SD*<br/>
dans Référence à une connexion de données existante à copier.

## <a name="open"></a>CDataConnection :: Open

Ouvre une connexion à une source de données à l’aide d’une chaîne d’initialisation.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitString*<br/>
dans Chaîne d’initialisation de la source de données.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="opennewsession"></a>CDataConnection :: OpenNewSession

Ouvre une nouvelle session à l’aide de la source de données de l’objet de connexion actuel.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
[in/out] Référence au nouvel objet de session.

### <a name="remarks"></a>Notes

La nouvelle session utilise l’objet de source de données contenu de l’objet de connexion en cours comme parent et peut accéder à toutes les mêmes informations que la source de données.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="op_bool"></a>CDataConnection :: Operator BOOL

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Notes

Retourne la valeur **bool** (typedef MFC). **True** signifie que la session active est ouverte ; **False** signifie que la session active est fermée.

## <a name="op_bool_ole"></a>CDataConnection :: operator bool (OLE DB)

Détermine si la session active est ouverte ou non.

### <a name="syntax"></a>Syntaxe

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Notes

Retourne une **bool** valeur booléenneC++ (type de données). **true** signifie que la session active est ouverte ; **false** signifie que la session active est fermée.

## <a name="op_cdata_amp"></a>CDataConnection :: Operator CDataSource&amp;

Retourne une référence à l’objet `CDataSource` contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à l’objet `CDataSource` contenu, ce qui vous permet de passer un objet `CDataConnection` dans lequel une référence `CDataSource` est attendue.

### <a name="example"></a>Exemple

Si vous avez une fonction (comme `func` ci-dessous) qui prend une référence `CDataSource`, vous pouvez utiliser `CDataSource&` pour passer un objet `CDataConnection` à la place.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a>CDataConnection :: Operator CDataSource *

Retourne un pointeur désignant l’objet `CDataSource` contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers l’objet `CDataSource` contenu, ce qui vous permet de passer un objet `CDataConnection` où un pointeur `CDataSource` est attendu.

Pour obtenir un exemple d’utilisation, consultez [Operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) .

## <a name="op_csession_amp"></a>CDataConnection :: Operator CSession&amp;

Retourne une référence à l’objet `CSession` contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence à l’objet `CSession` contenu, ce qui vous permet de passer un objet `CDataConnection` dans lequel une référence `CSession` est attendue.

### <a name="example"></a>Exemple

Si vous avez une fonction (comme `func` ci-dessous) qui prend une référence `CSession`, vous pouvez utiliser `CSession&` pour passer un objet `CDataConnection` à la place.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a>CDataConnection :: Operator CSession *

Retourne un pointeur désignant l’objet `CSession` contenu.

### <a name="syntax"></a>Syntaxe

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Notes

Cet opérateur retourne un pointeur vers l’objet `CSession` contenu, ce qui vous permet de passer un objet `CDataConnection` où un pointeur `CSession` est attendu.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation, consultez [opérateur CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) .

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)