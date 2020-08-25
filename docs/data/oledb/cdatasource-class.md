---
title: CDataSource, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 2ce5090d7e1c74607a82ddbb79afebe185a1dca7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838345"
---
# <a name="cdatasource-class"></a>CDataSource, classe

Correspond à un objet de source de données OLE DB, qui représente une connexion via un fournisseur à une source de données.

## <a name="syntax"></a>Syntaxe

```cpp
class CDataSource
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

| Nom | Description |
|-|-|
|[Close](#close)|Ferme la connexion.|
|[GetInitializationString](#getinitializationstring)|Récupère la chaîne d’initialisation de la source de données qui est actuellement ouverte.|
|[GetProperties](#getproperties)|Obtient les valeurs des propriétés actuellement définies pour la source de données connectée.|
|[GetProperty](#getproperty)|Obtient la valeur d’une propriété unique actuellement définie pour la source de données connectée.|
|[Ouvrir](#open)|Crée une connexion à un fournisseur (source de données) à l’aide d’un, d’un `CLSID` `ProgID` ou d’un `CEnumerator` moniker fourni par l’appelant.|
|[OpenFromFileName](#openfromfilename)|Ouvre une source de données à partir d'un fichier spécifié par le nom de fichier fourni par l'utilisateur.|
|[OpenFromInitializationString](#openfrominitializationstring)|Ouvre la source de données spécifiée par une chaîne d’initialisation.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Permet à l’utilisateur de sélectionner un fichier de liaison de données créé précédemment pour ouvrir la source de données correspondante.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Ouvre un objet source de données à l’aide de la boîte de dialogue liaison de données.|

## <a name="remarks"></a>Notes

Une ou plusieurs sessions de base de données peuvent être créées pour une seule connexion. Ces sessions sont représentées par `CSession` . Vous devez appeler [CDataSource :: Open](../../data/oledb/cdatasource-open.md) pour ouvrir la connexion avant de créer une session avec `CSession::Open` .

Pour obtenir un exemple d’utilisation de `CDataSource` , consultez l’exemple [CatDB](../../overview/visual-cpp-samples.md) .

## <a name="cdatasourceclose"></a><a name="close"></a> CDataSource :: Close

Ferme la connexion en relâchant le `m_spInit` pointeur.

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a> CDataSource :: GetInitializationString

Récupère la chaîne d’initialisation d’une source de données qui est actuellement ouverte.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Paramètres

*pInitializationString*<br/>
à Pointeur vers la chaîne d’initialisation.

*bIncludePassword*<br/>
[in] **`true`** Si la chaîne contient un mot de passe ; Sinon, **`false`** .

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

La chaîne d’initialisation résultante peut être utilisée pour rouvrir ultérieurement cette connexion à la source de données.

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a> CDataSource :: GetProperties

Retourne les informations de propriété demandées pour l’objet de source de données connecté.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [IDBProperties :: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour obtenir une seule propriété, utilisez [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a> CDataSource :: GetProperty

Retourne la valeur d’une propriété spécifiée pour l’objet de source de données connecté.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Paramètres

*guid*<br/>
dans GUID identifiant le jeu de propriétés pour lequel la propriété doit être retournée.

*propid*<br/>
dans ID de propriété de la propriété à retourner.

*pVariant*<br/>
à Pointeur vers le variant où `GetProperty` retourne la valeur de la propriété.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Pour afficher plusieurs propriétés, utilisez [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="cdatasourceopen"></a><a name="open"></a> CDataSource :: Open

Ouvre une connexion à une source de données à l’aide d’un `CLSID` `ProgID` `CEnumerator` moniker, ou ou invite l’utilisateur à utiliser une boîte de dialogue de localisateur.

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
dans `CLSID` Du fournisseur de données.

*pPropSet*<br/>
dans Pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Consultez [jeux de propriétés et groupes de propriétés](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

*nPropertySets*<br/>
dans Nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passées dans l’argument *pPropSet* .

*pName*<br/>
[in] Nom de la base de données à laquelle se connecter.

*pUserName*<br/>
[in] Nom de l'utilisateur.

*pPassword*<br/>
[in] Mot de passe de l'utilisateur.

*nInitMode*<br/>
[in] Mode d'initialisation de la base de données. Pour obtenir la liste des modes d’initialisation valides, consultez [propriétés d’initialisation](/previous-versions/windows/desktop/ms723127(v=vs.85))dans le Guide de *Référence du programmeur OLE DB* dans le SDK Windows. Si *nInitMode* est égal à zéro, aucun mode d’initialisation n’est inclus dans le jeu de propriétés utilisé pour ouvrir la connexion.

*szProgID*<br/>
[in] Identificateur de programme.

*énumérateur*<br/>
dans Objet [CEnumerator](../../data/oledb/cenumerator-class.md) utilisé pour obtenir un moniker pour ouvrir la connexion lorsque l’appelant ne spécifie pas de `CLSID` .

*hWnd*<br/>
[in] Handle de fenêtre devant être le parent de la boîte de dialogue. L’utilisation de la surcharge de fonction qui utilise le paramètre *HWND* appellera automatiquement les composants de service ; Pour plus d’informations, consultez la section Notes.

*dwPromptOptions*<br/>
[in] Détermine le style de la boîte de dialogue de recherche à afficher. Consultez Msdasc.h pour connaître les valeurs possibles.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

La surcharge de méthode qui utilise le paramètre *HWND* ouvre un objet source de données avec les composants de service dans oledb32.dll ; Cette DLL contient l’implémentation de fonctionnalités de composants de service, telles que le regroupement de ressources, l’inscription de transaction automatique, etc. Pour plus d’informations, consultez la référence OLE DB dans le [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

Les surcharges de méthode qui n’utilisent pas le paramètre *HWND* ouvrent un objet de source de données sans utiliser les composants de service dans oledb32.dll. Un objet [CDataSource](../../data/oledb/cdatasource-class.md) ouvert avec ces surcharges de fonction ne peut pas utiliser les fonctionnalités des composants de service.

### <a name="example"></a>Exemple

Le code suivant montre comment ouvrir une source de données Jet 4.0 avec les modèles OLE DB. Même si vous traitez la source de données Jet comme une source de données OLE DB, Toutefois, votre appel à `Open` a besoin de deux jeux de propriétés : un pour DBPROPSET_DBINIT et l’autre pour DBPROPSET_JETOLEDB_DBINIT, afin que vous puissiez définir DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a> CDataSource :: OpenFromFileName

Ouvre une source de données à partir d'un fichier spécifié par le nom de fichier fourni par l'utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Paramètres

*szFileName*<br/>
[in] Nom d'un fichier, généralement un fichier de connexion de source de données au format .UDL.

Pour plus d’informations sur les fichiers de liaison de données (fichiers. udl), consultez [vue d’ensemble](/previous-versions/windows/desktop/ms718102(v=vs.85)) de l’API de liaison de données dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l'aide des composants de service d'oledb32.dll ; cette DLL contient l'implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l'inscription de transaction automatique, etc. Pour plus d’informations, consultez la référence OLE DB dans le [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a> CDataSource :: OpenFromInitializationString

Ouvre une source de données spécifiée par la chaîne d’initialisation fournie par l’utilisateur.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Paramètres

*szInitializationString*<br/>
dans Chaîne d’initialisation.

*fPromptForInfo*<br/>
dans Si cet argument a la valeur **`true`** , `OpenFromInitializationString` affecte à la propriété DBPROP_INIT_PROMPT la valeur DBPROMPT_COMPLETEREQUIRED, qui spécifie que l’utilisateur est invité uniquement si des informations supplémentaires sont nécessaires. Cela est utile dans les situations où la chaîne d’initialisation spécifie une base de données qui requiert un mot de passe, mais la chaîne ne contient pas le mot de passe. L’utilisateur sera invité à entrer un mot de passe (ou toute autre information manquante) lors de la tentative de connexion à la base de données.

La valeur par défaut est **`false`** , qui spécifie que l’utilisateur n’est jamais invité (définit DBPROP_INIT_PROMPT pour DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l'aide des composants de service d'oledb32.dll ; cette DLL contient l'implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l'inscription de transaction automatique, etc.

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a> CDataSource :: OpenWithPromptFileName

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

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l'aide des composants de service d'oledb32.dll ; cette DLL contient l'implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l'inscription de transaction automatique, etc. Pour plus d’informations, consultez la référence OLE DB dans le [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a> CDataSource :: OpenWithServiceComponents

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
dans `CLSID` D’un fournisseur de données.

*szProgID*<br/>
[in] ID de programme d'un fournisseur de données.

*pPropset*<br/>
dans Pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Consultez [jeux de propriétés et groupes de propriétés](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows. Si l'objet source de données est initialisé, les propriétés doivent appartenir au groupe de propriétés Source de données. Si la même propriété est spécifiée plusieurs fois dans *pPropset*, la valeur utilisée est spécifique au fournisseur. Si *ulPropSets* est égal à zéro, ce paramètre est ignoré.

*ulPropSets*<br/>
dans Nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passées dans l’argument *pPropSet* . Si la valeur est égale à zéro, le fournisseur ignore *pPropset*.

### <a name="return-value"></a>Valeur renvoyée

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode ouvre un objet source de données à l'aide des composants de service d'oledb32.dll ; cette DLL contient l'implémentation des fonctionnalités Composants de service, telles que la mise en pool de ressources, l'inscription de transaction automatique, etc. Pour plus d’informations, consultez la référence OLE DB dans le [Guide du programmeur OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
