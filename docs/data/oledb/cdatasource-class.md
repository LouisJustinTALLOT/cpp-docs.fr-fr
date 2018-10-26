---
title: CDataSource, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5f6224b86d7df7af223c441361832984ff6a85c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058672"
---
# <a name="cdatasource-class"></a>CDataSource, classe

Correspond à un objet de source de données OLE DB, qui représente une connexion via un fournisseur de source de données.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataSource
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Fermer](#close)|Ferme la connexion.|
|[GetInitializationString](#getinitializationstring)|Récupère la chaîne d’initialisation de la source de données qui est actuellement ouverte.|
|[GetProperties](#getproperties)|Obtient les valeurs des propriétés actuellement définies pour la source de données connectée.|
|[GetProperty](#getproperty)|Obtient la valeur d’une propriété unique actuellement définie pour la source de données connectée.|
|[Ouvrir](#open)|Crée une connexion à un fournisseur (source de données) à l’aide un `CLSID`, `ProgID`, ou un `CEnumerator` moniker fournie par l’appelant.|
|[OpenFromFileName](#openfromfilename)|Ouvre une source de données à partir d'un fichier spécifié par le nom de fichier fourni par l'utilisateur.|
|[OpenFromInitializationString](#openfrominitializationstring)|Ouvre la source de données spécifiée par une chaîne d’initialisation.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Permet à l’utilisateur sélectionner un fichier de liaison de données créée précédemment pour ouvrir la source de données correspondante.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Ouvre un objet de source de données à l’aide de la boîte de dialogue liaison de données.|

## <a name="remarks"></a>Notes

Une ou plusieurs sessions de base de données peuvent être créées pour une seule connexion. Ces sessions sont représentées par `CSession`. Vous devez appeler [CDataSource::Open](../../data/oledb/cdatasource-open.md) pour ouvrir la connexion avant de créer une session avec `CSession::Open`.

Pour obtenir un exemple montrant comment utiliser `CDataSource`, consultez le [CatDB](../../visual-cpp-samples.md) exemple.

## <a name="close"></a> CDataSource::Close

Ferme la connexion en libérant le `m_spInit` pointeur.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a> CDataSource::GetInitializationString

Récupère la chaîne d’initialisation d’une source de données qui est actuellement ouverte.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString, 
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Paramètres

*pInitializationString*<br/>
[out] Pointeur vers la chaîne d’initialisation.

*bIncludePassword*<br/>
[in] **true** si la chaîne inclut un mot de passe ; sinon **false**.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La chaîne d’initialisation qui en résulte peut être utilisée pour le rouvrir plus tard cette connexion de source de données.

## <a name="getproperties"></a> CDataSource::GetProperties

Retourne les informations de propriété demandées pour l’objet de source de données connectée.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperties(ULONG ulPropIDSets, 
   constDBPROPIDSET* pPropIDSet, 
   ULONG* pulPropertySets, 
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour obtenir une propriété unique, utilisez [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="getproperty"></a> CDataSource::GetProperty

Retourne la valeur d’une propriété spécifiée pour l’objet de source de données connectée.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperty(const GUID& guid, 
   DBPROPID propid, 
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
[in] Un GUID qui identifie la propriété pour laquelle retourner la propriété.

*ID de propriété*<br/>
[in] ID de propriété pour la propriété à retourner.

*pVariant*<br/>
[out] Un pointeur vers le variant où `GetProperty` retourne la valeur de la propriété.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Pour obtenir plusieurs propriétés, utilisez [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="open"></a> CDataSource::Open

Ouvre une connexion à une source de données à l’aide un `CLSID`, `ProgID`, ou `CEnumerator` moniker ou invite l’utilisateur avec une boîte de dialogue de recherche.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID, 
   DBPROPSET* pPropSet = NULL, 
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID, 
   LPCTSTR pName,LPCTSTR pUserName = NULL, 
   LPCTSTR pPassword = NULL, 
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le `CLSID` du fournisseur de données.

*pPropSet*<br/>
[in] Un pointeur vers un tableau de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](/previous-versions/windows/desktop/ms713696) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.

*nPropertySets*<br/>
[in] Le nombre de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures passées dans le *pPropSet* argument.

*pName*<br/>
[in] Nom de la base de données à laquelle se connecter.

*pUserName*<br/>
[in] Nom de l'utilisateur.

*pPassword*<br/>
[in] Mot de passe de l'utilisateur.

*nInitMode*<br/>
[in] Mode d'initialisation de la base de données. Consultez [propriétés d’initialisation](/previous-versions/windows/desktop/ms723127)dans le *de référence du programmeur OLE DB* dans le SDK Windows pour obtenir la liste des modes d’initialisation valides. Si *nInitMode* est égal à zéro, aucune initialisation mode est inclus dans le jeu de propriétés utilisé pour ouvrir la connexion.

*szProgID*<br/>
[in] Identificateur de programme.

*enumerator*<br/>
[in] Un [CEnumerator](../../data/oledb/cenumerator-class.md) objet utilisé pour obtenir un moniker de l’ouverture de la connexion lorsque l’appelant ne spécifie pas un `CLSID`.

*hWnd*<br/>
[in] Handle de fenêtre devant être le parent de la boîte de dialogue. À l’aide de la surcharge de fonction qui utilise le *hWnd* paramètre appellent automatiquement les composants de Service ; consultez la section Notes pour plus d’informations.

*dwPromptOptions*<br/>
[in] Détermine le style de la boîte de dialogue de recherche à afficher. Consultez Msdasc.h pour connaître les valeurs possibles.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

La surcharge de méthode qui utilise le *hWnd* paramètre ouvre un objet de source de données avec les composants de service d’oledb32.dll ; cette DLL contient l’implémentation de fonctionnalités de composants de Service, telles que la concentration des ressources, automatique Inscription de transaction et ainsi de suite. Pour plus d’informations, consultez « Services OLE DB » dans la référence du programmeur OLE DB à [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

Les surcharges de méthode qui n’utilisent pas le *hWnd* paramètre ouvrir un objet de source de données sans utiliser les composants de service dans oledb32.dll. Un [CDataSource](../../data/oledb/cdatasource-class.md) objet ouvert avec ces surcharges de fonction ne pourra pas utiliser toutes les fonctionnalités des composants de Service.

### <a name="example"></a>Exemple

Le code suivant montre comment ouvrir une source de données Jet 4.0 avec les modèles OLE DB. Même si vous traitez la source de données Jet comme une source de données OLE DB, Toutefois, votre appel à `Open` a besoin de deux jeux de propriétés : une pour DBPROPSET_DBINIT et l’autre pour DBPROPSET_JETOLEDB_DBINIT, afin que vous puissiez définir DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

Ouvre une source de données à partir d'un fichier spécifié par le nom de fichier fourni par l'utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Paramètres

*szFileName*<br/>
[in] Nom d'un fichier, généralement un fichier de connexion de source de données au format .UDL.

Pour plus d’informations sur les fichiers de liaison de données (fichiers .udl), consultez [Data Link API Overview](/previous-versions/windows/desktop/ms718102) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l’aide des composants de service d’oledb32.dll ; cette DLL contient l’implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l’inscription de transaction automatique, etc. Pour plus d’informations, consultez « Services OLE DB » dans la référence du programmeur OLE DB à [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openfrominitializationstring"></a> CDataSource::OpenFromInitializationString

Ouvre une source de données spécifiée par la chaîne d’initialisation fourni par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString, 
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitializationString*<br/>
[in] La chaîne d’initialisation.

*fPromptForInfo*<br/>
[in] Si cet argument a la valeur **true**, puis `OpenFromInitializationString` définira la propriété DBPROP_INIT_PROMPT sur DBPROMPT_COMPLETEREQUIRED, ce qui indique que l’utilisateur invité uniquement si plus d’informations est nécessaire. Cela est utile pour les situations dans lesquelles la chaîne d’initialisation spécifie une base de données qui requiert un mot de passe, mais la chaîne ne contient pas le mot de passe. L’utilisateur demandera un mot de passe (ou toute autre information manquante) lorsque vous tentez de vous connecter à la base de données.

La valeur par défaut est **false**, qui spécifie que l’utilisateur ne soit jamais demandées (ensembles DBPROP_INIT_PROMPT sur DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l’aide des composants de service d’oledb32.dll ; cette DLL contient l’implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l’inscription de transaction automatique, etc.

## <a name="openwithpromptfilename"></a> CDataSource::OpenWithPromptFileName

Cette méthode présente une invite à l'utilisateur sous la forme d'une boîte de dialogue, puis ouvre une source de données correspondant au fichier spécifié par l'utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ), 
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE, 
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Paramètres

*hWnd*<br/>
[in] Handle de fenêtre devant être le parent de la boîte de dialogue.

*dwPromptOptions*<br/>
[in] Détermine le style de la boîte de dialogue de recherche à afficher. Consultez Msdasc.h pour connaître les valeurs possibles.

*szInitialDirectory*<br/>
[in] Répertoire initial à afficher dans la boîte de dialogue de recherche.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l’aide des composants de service d’oledb32.dll ; cette DLL contient l’implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l’inscription de transaction automatique, etc. Pour plus d’informations, consultez « Services OLE DB » dans la référence du programmeur OLE DB à [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openwithservicecomponents"></a> CDataSource::OpenWithServiceComponents

Ouvre un objet source de données à l'aide des composants de service d'oledb32.dll.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le `CLSID` d’un fournisseur de données.

*szProgID*<br/>
[in] ID de programme d'un fournisseur de données.

*pPropset*<br/>
[in] Un pointeur vers un tableau de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](/previous-versions/windows/desktop/ms713696) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows. Si l'objet source de données est initialisé, les propriétés doivent appartenir au groupe de propriétés Source de données. Si la même propriété est spécifiée plusieurs fois dans *pPropset*, puis de la valeur utilisée est spécifique au fournisseur. Si *ulPropSets* est égal à zéro, ce paramètre est ignoré.

*ulPropSets*<br/>
[in] Le nombre de [DBPROPSET](/previous-versions/windows/desktop/ms714367) structures passées dans le *pPropSet* argument. S’il s’agit de zéro, le fournisseur ignore *pPropset*.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l’aide des composants de service d’oledb32.dll ; cette DLL contient l’implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l’inscription de transaction automatique, etc. Pour plus d’informations, consultez « Services OLE DB » dans la référence du programmeur OLE DB à [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)