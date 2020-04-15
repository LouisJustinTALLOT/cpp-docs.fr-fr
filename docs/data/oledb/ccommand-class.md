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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368628"
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

*TAccessor (en anglais)*<br/>
Le type de classe d’accesseur (comme, `CDynamicParameterAccessor` `CDynamicStringAccessor`, ou `CEnumeratorAccessor`) que vous voulez que la commande à utiliser. La valeur `CNoAccessor`par défaut est , qui spécifie que la classe ne supporte pas les paramètres ou les colonnes de sortie.

*TRowset (TRowset)*<br/>
Le type de classe encastrés (comme `CArrayRowset` ou `CNoRowset`) que vous voulez que la commande utilise. Par défaut, il s’agit de `CRowset`.

*TMultiple*<br/>
Pour utiliser une commande OLE DB qui peut retourner plusieurs résultats, spécifiez [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Sinon, utilisez [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Pour plus de détails, voir [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Fermer](#close)|Ferme la commande actuelle.|
|[GetNextResult (en)](#getnextresult)|Récupère le résultat suivant lors de l’utilisation de plusieurs ensembles de résultats.|
|[Ouvrir](#open)|Exécute et lie optionnellement la commande.|

### <a name="inherited-methods"></a>Méthodes héritées

|||
|-|-|
|[Créer](#create)|Crée une nouvelle commande pour la session spécifiée, puis définit le texte de commande.|
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|
|[GetParameterInfo](#getparameterinfo)|Obtient une liste des paramètres de la commande, de leurs noms et de leurs types.|
|[Préparation](#prepare)|Valide et optimise la commande actuelle.|
|[CommuniquéCommand](#releasecommand)|Libère l’accesseur de paramètres si nécessaire, puis libère la commande.|
|[SetParameterInfo](#setparameterinfo)|Spécifie le type natif de chaque paramètre de commande.|
|[Non préparé](#unprepare)|Écarte le plan d’exécution de commandement actuel.|

## <a name="remarks"></a>Notes

Utilisez cette classe lorsque vous avez besoin d’effectuer une opération basée sur des paramètres ou d’exécuter une commande. Si vous avez simplement besoin d’ouvrir un simple jeu de ligne, utilisez [CTable](../../data/oledb/ctable-class.md) à la place.

La classe d’accesseur que vous utilisez détermine la méthode de liaison des paramètres et des données.

Notez que vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet parce que ce fournisseur ne prend pas en charge les procédures stockées (seules les constantes sont autorisées dans les chaînes de requête).

## <a name="ccommandclose"></a><a name="close"></a>CCommand::Fermer

Libère le jeu de ligne de l’accesseur associé à la commande.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Notes

Une commande utilise un jeu de ligne, un accesseur de jeu de résultat et (optionnellement) un accesseur de paramètres (contrairement aux tableaux, qui ne prennent pas en charge les paramètres et n’ont pas besoin d’un accesseur de paramètres).

Lorsque vous exécutez une commande, vous devez appeler les deux `Close` et [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) après la commande.

Lorsque vous souhaitez exécuter la même commande à plusieurs reprises, `Close` vous `Execute`devez libérer chaque accesseur de configuration de résultat en appelant avant d’appeler . À la fin de la série, vous devez `ReleaseCommand`libérer l’accesseur de paramètres en appelant . Un autre scénario courant est d’appeler une procédure stockée qui a des paramètres de sortie. Sur de nombreux fournisseurs (tels que le fournisseur OLE DB pour SQL Server), les valeurs de paramètres de sortie ne seront pas accessibles tant que vous n’aurez pas fermé l’accesseur de configuration de résultat. Appelez `Close` pour fermer l’accesseur de jeu et de jeu de résultat retourné, mais pas l’accesseur de paramètres, vous permettant ainsi de récupérer les valeurs de paramètres de sortie.

### <a name="example"></a>Exemple

L’exemple suivant montre comment vous pouvez appeler `Close` et `ReleaseCommand` lorsque vous exécutez la même commande plusieurs fois.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand::GetNextResult

Récupère le prochain ensemble de résultats si l’un d’eux est disponible.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Paramètres

*pulrowsAffected*<br/>
[dans/out] Un pointeur à la mémoire où le nombre de lignes affectées par une commande est retourné.

*bBind (en)*<br/>
[dans] Précise s’il faut lier automatiquement la commande après avoir été exécuté. La valeur par défaut est **vraie,** ce qui provoque la commande d’être liée automatiquement. Réglage *bBind* à **faux** empêche la liaison automatique de la commande afin que vous puissiez lier manuellement. (La liaison manuelle intéresse particulièrement les utilisateurs de l’OLAP.)

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Si un ensemble de résultats a déjà été récupéré, cette fonction libère l’ensemble de résultats précédent et débine les colonnes. Si *bBind* est **vrai,** il lie les nouvelles colonnes.

Vous ne devez appeler cette fonction que si `CCommand` vous avez spécifié plusieurs résultats en définissant le paramètre du modèle *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand::Ouvert

Exécute et lie optionnellement la commande.

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

*Session*<br/>
[dans] La session dans laquelle exécuter la commande.

*wszCommand wszCommand*<br/>
[dans] La commande d’exécuter, passé comme une chaîne Unicode. Peut être NULL `CAccessor`lors de l’utilisation , auquel cas la commande sera récupérée à partir de la valeur passée à la [macro DEFINE_COMMAND.](../../data/oledb/define-command.md) Voir [ICommand::Exécutez](/previous-versions/windows/desktop/ms718095(v=vs.85)) dans la *référence du programmeur OLE DB* pour plus de détails.

*szCommand (en)*<br/>
[dans] Même que *wszCommand* sauf que ce paramètre prend une chaîne de commande ANSI. La quatrième forme de cette méthode peut prendre une valeur NULL. Voir "Remarques" plus tard dans ce sujet pour plus de détails.

*pPropSet*<br/>
[dans] Un pointeur vers un tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) contenant des propriétés et des valeurs à définir. Voir [les ensembles de propriétés et les groupes de propriété](/previous-versions/windows/desktop/ms713696(v=vs.85)) dans la référence du *programmeur OLE DB* dans le SDK Windows.

*pRowsAffected*<br/>
[dans/out] Un pointeur à la mémoire où le nombre de lignes affectées par une commande est retourné. Si * \*pRowsAffected* est NULL, aucun nombre de lignes n’est retourné. Sinon, `Open` les * \*ensembles pRowsAffected* selon les conditions suivantes:

|Si|Alors|
|--------|----------|
|`cParamSets` L’élément `pParams` de est supérieur à 1|pRowsAffected représente le nombre total de lignes affectées par tous les ensembles de paramètres spécifiés dans l’exécution. * \**|
|Le nombre de lignes touchées n’est pas disponible|pRowsAffected est réglé à -1. * \**|
|La commande ne met pas à jour, ne supprime pas ou n’insère pas de lignes|pRowsAffected n’est pas défini. * \**|

*guidCommand*<br/>
[dans] Un GUID qui spécifie la syntaxe et les règles générales que le fournisseur doit utiliser pour analyser le texte de commande. Voir [ICommandText:GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) et [ICommandText:SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) in the *OLE DB Programmer’s Reference* for details.

*bBind (en)*<br/>
[dans] Précise s’il faut lier automatiquement la commande après avoir été exécuté. La valeur par défaut est **vraie,** ce qui provoque la commande d’être liée automatiquement. Réglage *bBind* à **faux** empêche la liaison automatique de la commande afin que vous puissiez lier manuellement. (La liaison manuelle intéresse particulièrement les utilisateurs de l’OLAP.)

*ulPropSets*<br/>
[dans] Le nombre de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) passé dans l’argument *pPropSet.*

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Les trois premières `Open` formes de prendre une session, créer une commande, et exécuter la commande, liant tous les paramètres si nécessaire.

La première `Open` forme de prend une chaîne de commande Unicode et n’a aucune valeur par défaut.

La deuxième `Open` forme de prend une chaîne de commande ANSI et aucune valeur par défaut (prévue pour la compatibilité vers l’arrière avec les applications ANSI existantes).

La troisième `Open` forme de permet à la chaîne de commande d’être NULL, en raison de type **int** avec une valeur par défaut de NULL. Il est prévu `Open(session, NULL);` `Open(session);` pour l’appel ou parce que NULL est de type **int**. Cette version exige et affirme que le **paramètre int** être NULL.

Utilisez la quatrième `Open` forme de lorsque vous avez déjà créé une commande et que vous souhaitez effectuer une seule [préparation](../../data/oledb/ccommand-prepare.md) et plusieurs exécutions.

> [!NOTE]
> `Open`appels `Execute`, qui `GetNextResult`à son tour appelle .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand::Créer

Appelle [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) pour créer une commande pour la session spécifiée, puis appelle [ICommandText:SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) pour spécifier le texte de commande.

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

*Session*<br/>
[dans] Une session sur laquelle créer la commande.

*wszCommand wszCommand*<br/>
[dans] Un pointeur sur le texte Unicode de la chaîne de commande.

*szCommand (en)*<br/>
[dans] Un pointeur sur le texte DE l’ANSI de la chaîne de commande.

*guidCommand*<br/>
[dans] Un GUID qui spécifie la syntaxe et les règles générales que le fournisseur doit utiliser pour analyser le texte de commande. Pour une description des dialectes, voir [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) dans la *référence du programmeur OLE DB*.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

La première `Create` forme de prend une chaîne de commande Unicode. La deuxième `Create` forme de prend une chaîne de commande ANSI (prévue pour la compatibilité vers l’arrière avec les applications ANSI existantes).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand::CreateCommand

Crée une nouvelle commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Paramètres

*Session*<br/>
[dans] Un `CSession` objet à associer à la nouvelle commande.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode crée une commande à l’aide de l’objet de session spécifié.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand::GetParameterInfo

Obtient une liste des paramètres de la commande, de leurs noms et de leurs types.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Paramètres

Voir [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) in the *OLE DB Programmer’s Reference*.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::Prepare

Valide et optimise la commande actuelle.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Paramètres

*cExpectedRuns*<br/>
[dans] Le nombre de fois que vous prévoyez exécuter la commande.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode enveloppe la méthode OLE DB [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand::ReleaseCommand

Libère l’accesseur de paramètres, puis libère la commande elle-même.

### <a name="syntax"></a>Syntaxe

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Notes

`ReleaseCommand`est utilisé en `Close`conjonction avec . Voir [Fermer](../../data/oledb/ccommand-close.md) pour plus de détails sur l’utilisation.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand::SetParameterInfo

Spécifie le type natif de chaque paramètre de commande.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Paramètres

Voir [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) in the *OLE DB Programmer’s Reference*.

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand::Unprepare

Écarte le plan d’exécution de commandement actuel.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Valeur de retour

Un HRESULT standard.

### <a name="remarks"></a>Notes

Cette méthode enveloppe la méthode OLE DB [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB Consumer Templates Référence](../../data/oledb/ole-db-consumer-templates-reference.md)
