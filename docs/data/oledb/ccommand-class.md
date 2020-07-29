---
title: CCommand, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 73b02f0ffb9d9b98a17933cc3b17c8627121e3ac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228919"
---
# <a name="ccommand-class"></a>CCommand, classe

Fournit des méthodes pour définir et exécuter une commande.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Type de classe d’accesseur (par exemple `CDynamicParameterAccessor` , `CDynamicStringAccessor` ou `CEnumeratorAccessor` ) que vous souhaitez que la commande utilise. La valeur par défaut est `CNoAccessor` , qui spécifie que la classe ne prend pas en charge les paramètres ou les colonnes de sortie.

*TRowset*<br/>
Type de classe d’ensemble de lignes (tel que `CArrayRowset` ou `CNoRowset` ) que la commande doit utiliser. Par défaut, il s’agit de `CRowset`.

*TMultiple*<br/>
Pour utiliser une commande OLE DB qui peut retourner plusieurs résultats, spécifiez [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Sinon, utilisez [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Pour plus d’informations, consultez [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Close](#close)|Ferme la commande active.|
|[GetNextResult](#getnextresult)|Extrait le résultat suivant lors de l’utilisation de plusieurs jeux de résultats.|
|[Ouvrir](#open)|Exécute et éventuellement lie la commande.|

### <a name="inherited-methods"></a>Méthodes héritées

|||
|-|-|
|[Créer](#create)|Crée une nouvelle commande pour la session spécifiée, puis définit le texte de la commande.|
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|
|[GetParameterInfo](#getparameterinfo)|Obtient une liste des paramètres de la commande, leurs noms et leurs types.|
|[Préparation](#prepare)|Valide et optimise la commande actuelle.|
|[ReleaseCommand](#releasecommand)|Libère l’accesseur de paramètre si nécessaire, puis libère la commande.|
|[SetParameterInfo](#setparameterinfo)|Spécifie le type natif de chaque paramètre de commande.|
|[Unprepare](#unprepare)|Ignore le plan d’exécution de la commande en cours.|

## <a name="remarks"></a>Notes

Utilisez cette classe lorsque vous devez effectuer une opération basée sur des paramètres ou exécuter une commande. Si vous avez simplement besoin d’ouvrir un ensemble de lignes simple, utilisez [CTable](../../data/oledb/ctable-class.md) à la place.

La classe d’accesseur que vous utilisez détermine la méthode de liaison des paramètres et des données.

Notez que vous ne pouvez pas utiliser de procédures stockées avec le fournisseur de OLE DB pour jet, car ce fournisseur ne prend pas en charge les procédures stockées (seules les constantes sont autorisées dans les chaînes de requête).

## <a name="ccommandclose"></a><a name="close"></a>CCommand :: Close

Libère l’ensemble de lignes d’accesseur associé à la commande.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Une commande utilise un ensemble de lignes, un accesseur de jeu de résultats et (éventuellement) un accesseur de paramètre (à la différence des tables, qui ne prennent pas en charge les paramètres et n’ont pas besoin d’un accesseur de paramètre).

Quand vous exécutez une commande, vous devez appeler `Close` et [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) après la commande.

Lorsque vous souhaitez exécuter la même commande à plusieurs reprises, vous devez libérer chaque accesseur du jeu de résultats en appelant `Close` avant d’appeler `Execute` . À la fin de la série, vous devez libérer l’accesseur de paramètre en appelant `ReleaseCommand` . Un autre scénario courant consiste à appeler une procédure stockée qui a des paramètres de sortie. Sur de nombreux fournisseurs (tels que le fournisseur OLE DB pour SQL Server), les valeurs des paramètres de sortie ne sont pas accessibles tant que vous n’avez pas fermé l’accesseur du jeu de résultats. Appelez `Close` pour fermer l’ensemble de lignes et l’accesseur de jeu de résultats retournés, mais pas l’accesseur de paramètre, ce qui vous permet de récupérer les valeurs des paramètres de sortie.

### <a name="example"></a>Exemple

L’exemple suivant montre comment vous pouvez appeler `Close` et `ReleaseCommand` lorsque vous exécutez la même commande plusieurs fois.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand :: GetNextResult

Récupère le jeu de résultats suivant, s’il est disponible.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Paramètres

*pulRowsAffected*<br/>
[in/out] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné.

*bBind*<br/>
dans Spécifie si la commande doit être liée automatiquement après son exécution. La valeur par défaut est **`true`** , ce qui entraîne la liaison automatique de la commande. La définition de *bBind* **`false`** empêche la liaison automatique de la commande afin que vous puissiez la lier manuellement. (La liaison manuelle présente un intérêt particulier pour les utilisateurs OLAP.)

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Si un jeu de résultats a été récupéré précédemment, cette fonction libère le jeu de résultats précédent et dissocie les colonnes. Si *bBind* est **`true`** , il lie les nouvelles colonnes.

Vous devez appeler cette fonction uniquement si vous avez spécifié plusieurs résultats en définissant le `CCommand` paramètre de modèle *TMultiple* = `CMultipleResults` .

## <a name="ccommandopen"></a><a name="open"></a>CCommand :: Open

Exécute et éventuellement lie la commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
dans Session dans laquelle exécuter la commande.

*wszCommand*<br/>
dans Commande à exécuter, transmise en tant que chaîne Unicode. Peut avoir la valeur NULL lors de l’utilisation `CAccessor` de, auquel cas la commande est Récupérée de la valeur passée à la macro [DEFINE_COMMAND](../../data/oledb/define-command.md) . Pour plus d’informations, consultez [ICommand :: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* .

*szCommand*<br/>
dans Identique à *wszCommand* , sauf que ce paramètre prend une chaîne de commande ANSI. La quatrième forme de cette méthode peut prendre une valeur NULL. Pour plus d’informations, consultez « Remarques » plus loin dans cette rubrique.

*pPropSet*<br/>
dans Pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Consultez [jeux de propriétés et groupes de propriétés](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* dans le SDK Windows.

*pRowsAffected*<br/>
[in/out] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné. Si * \* pRowsAffected* a la valeur null, aucun nombre de lignes n’est retourné. Sinon, `Open` définit * \* pRowsAffected* selon les conditions suivantes :

|Si|Alors|
|--------|----------|
|L' `cParamSets` élément de `pParams` est supérieur à 1|* \* pRowsAffected* représente le nombre total de lignes affectées par tous les jeux de paramètres spécifiés dans l’exécution.|
|Le nombre de lignes affectées n’est pas disponible|* \* pRowsAffected* a la valeur-1.|
|La commande ne met pas à jour, supprime ou insère des lignes|* \* pRowsAffected* n’est pas défini.|

*guidCommand*<br/>
dans GUID qui spécifie la syntaxe et les règles générales que le fournisseur doit utiliser pour analyser le texte de la commande. Pour plus d’informations, consultez [ICommandText :: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) et [ICommandText :: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) dans le *Guide de référence du programmeur OLE DB* .

*bBind*<br/>
dans Spécifie si la commande doit être liée automatiquement après son exécution. La valeur par défaut est **`true`** , ce qui entraîne la liaison automatique de la commande. La définition de *bBind* **`false`** empêche la liaison automatique de la commande afin que vous puissiez la lier manuellement. (La liaison manuelle présente un intérêt particulier pour les utilisateurs OLAP.)

*ulPropSets*<br/>
dans Nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passées dans l’argument *pPropSet* .

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Les trois premières formes de `Open` prendre une session, de créer une commande et d’exécuter la commande, en liant les paramètres si nécessaire.

La première forme de `Open` prend une chaîne de commande Unicode et n’a pas de valeur par défaut.

La seconde forme de `Open` prend une chaîne de commande ANSI et aucune valeur par défaut (fournie pour la compatibilité descendante avec les applications ANSI existantes).

La troisième forme de `Open` permet à la chaîne de commande d’être null, en raison de type **`int`** avec une valeur par défaut null. Elle est fournie pour appeler `Open(session, NULL);` ou `Open(session);` , car null est de type **`int`** . Cette version requiert et déclare que le **`int`** paramètre est null.

Utilisez la quatrième forme de `Open` lorsque vous avez déjà créé une commande et que vous souhaitez effectuer une seule [préparation](../../data/oledb/ccommand-prepare.md) et plusieurs exécutions.

> [!NOTE]
> `Open`appelle `Execute` , qui à son tour appelle `GetNextResult` .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand :: Create

Appelle [CCommand :: CreateCommand](../../data/oledb/ccommand-createcommand.md) pour créer une commande pour la session spécifiée, puis appelle [ICommandText :: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) pour spécifier le texte de la commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
dans Session sur laquelle créer la commande.

*wszCommand*<br/>
dans Pointeur vers le texte Unicode de la chaîne de commande.

*szCommand*<br/>
dans Pointeur vers le texte ANSI de la chaîne de commande.

*guidCommand*<br/>
dans GUID qui spécifie la syntaxe et les règles générales que le fournisseur doit utiliser pour analyser le texte de la commande. Pour obtenir une description des dialectes, consultez [ICommandText :: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

La première forme de `Create` prend une chaîne de commande Unicode. La seconde forme de `Create` prend une chaîne de commande ANSI (fournie pour la compatibilité descendante avec les applications ANSI existantes).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand :: CreateCommand

Crée une nouvelle commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Paramètres

*session*<br/>
dans `CSession`Objet à associer à la nouvelle commande.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode crée une commande à l’aide de l’objet de session spécifié.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand :: GetParameterInfo

Obtient une liste des paramètres de la commande, leurs noms et leurs types.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandWithParameters :: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand ::P reparenthèse

Valide et optimise la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*cExpectedRuns*<br/>
dans Nombre de fois où vous prévoyez d’exécuter la commande.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode OLE DB [ICommandPrepare ::P](/previous-versions/windows/desktop/ms718370(v=vs.85))restante.

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand :: ReleaseCommand

Libère l’accesseur de paramètre, puis libère la commande elle-même.

### <a name="syntax"></a>Syntaxe

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Notes

`ReleaseCommand`est utilisé conjointement avec `Close` . Pour plus d’informations sur l’utilisation, consultez [Close](../../data/oledb/ccommand-close.md) .

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand :: SetParameterInfo

Spécifie le type natif de chaque paramètre de commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandWithParameters :: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand :: Unprepare

Ignore le plan d’exécution de la commande en cours.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Valeur de retour

HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode encapsule la méthode OLE DB [ICommandPrepare :: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
