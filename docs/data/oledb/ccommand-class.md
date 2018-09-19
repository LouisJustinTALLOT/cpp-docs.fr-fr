---
title: CCommand, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9cc04c6d9e270e0c3b5c3bd02e05b426ccf4c53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060926"
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
Le type de classe d’accesseur (tel que `CDynamicParameterAccessor`, `CDynamicStringAccessor`, ou `CEnumeratorAccessor`) que vous voulez que la commande à utiliser. La valeur par défaut est `CNoAccessor`, qui spécifie que la classe pas prendre en charge des paramètres ou colonnes de sortie.  
  
*TRowset*<br/>
Le type de classe de l’ensemble de lignes (tel que `CArrayRowset` ou `CNoRowset`) que vous voulez que la commande à utiliser. La valeur par défaut est `CRowset`.  
  
*TMultiple*<br/>
Pour utiliser une commande OLE DB qui peut retourner plusieurs résultats, spécifiez [CMultipleResults](../../data/oledb/cmultipleresults-class.md). Sinon, utilisez [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Pour plus d’informations, consultez [IMultipleResults](/previous-versions/windows/desktop/ms721289\(v=vs.85\)).  

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldbcli.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Fermer](#close)|Ferme la commande actuelle.|  
|[GetNextResult](#getnextresult)|Récupère le résultat suivant lors de l’utilisation de plusieurs résultats définit.|  
|[Ouvrir](#open)|Exécute et éventuellement lie la commande.|  
  
### <a name="inherited-methods"></a>Méthodes héritées  
  
|||  
|-|-|  
|[Créer](#create)|Crée une nouvelle commande pour la session spécifiée, puis définit le texte de commande.|  
|[CreateCommand](#createcommand)|Crée une nouvelle commande.|  
|[GetParameterInfo](#getparameterinfo)|Obtient une liste de paramètres de la commande, leurs noms et leurs types.|  
|[Préparer](#prepare)|Valide et optimise la commande actuelle.|  
|[ReleaseCommand](#releasecommand)|Libère l’accesseur de paramètre, si nécessaire, puis libère de la commande.|  
|[SetParameterInfo](#setparameterinfo)|Spécifie le type natif de chaque paramètre de commande.|  
|[Supprimer la préparation](#unprepare)|Ignore le plan d’exécution de commande actuelle.|  
  
## <a name="remarks"></a>Notes  

Utilisez cette classe lorsque vous avez besoin effectuer une opération basée sur un paramètre ou exécuter une commande. Si vous devez simplement ouvrir un simple ensemble de lignes, utilisez [CTable](../../data/oledb/ctable-class.md) à la place.  
  
La classe d’accesseur que vous utilisez détermine la méthode de liaison des paramètres et des données.  
  
Notez que vous ne pouvez pas utiliser les procédures stockées avec le fournisseur OLE DB pour Jet, car ce fournisseur ne prend pas en charge les procédures (seules les constantes sont autorisées dans les chaînes de requête).  

## <a name="close"></a> CCommand::Close

Libère l’ensemble de lignes accesseur associé à la commande.  
  
### <a name="syntax"></a>Syntaxe

```cpp
void Close();  
```  
  
### <a name="remarks"></a>Notes  

Une commande utilise un ensemble de lignes, accesseur set de résultat et (éventuellement) un accesseur de paramètre (contrairement aux tables, qui ne prennent pas en charge les paramètres et n’avez pas besoin d’un accesseur de paramètre).  
  
Lorsque vous exécutez une commande, vous devez appeler les deux `Close` et [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) après la commande.  
  
Lorsque vous souhaitez exécuter la même commande plusieurs fois, vous devez en libérer chaque accesseur de jeu de résultats en appelant `Close` avant d’appeler `Execute`. À la fin de la série, vous devez en libérer l’accesseur de paramètre en appelant `ReleaseCommand`. Un autre scénario courant appelle une procédure stockée qui a des paramètres de sortie. De nombreux fournisseurs (par exemple, le fournisseur OLE DB pour SQL Server) les valeurs de paramètre de sortie sera pas accessibles jusqu'à la fermeture de l’accesseur set de résultat. Appelez `Close` pour fermer l’ensemble de lignes retournée et accesseur set de résultat, mais pas l’accesseur de paramètre, vous permettant ainsi de récupérer les valeurs de paramètre de sortie.  
  
### <a name="example"></a>Exemple  

L’exemple suivant montre comment vous pouvez appeler `Close` et `ReleaseCommand` lorsque vous exécutez la même commande plusieurs fois.  
  
[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="getnextresult"></a> CCommand::GetNextResult

Extrait le prochain jeu de résultats si celle-ci est disponible.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected, 
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  

*pulRowsAffected*<br/>
[entrée/sortie] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné.  
  
*bBind*<br/>
[in] Spécifie s’il faut lier la commande automatiquement après en cours d’exécution. La valeur par défaut est **true**, ce qui entraîne la commande à lier automatiquement. Paramètre *bBind* à **false** empêche la liaison automatique de la commande de sorte que vous pouvez lier manuellement. (Liaison manuelle est un intérêt particulier pour les utilisateurs OLAP).  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Si un jeu de résultats ont été extraites précédemment, cette fonction libère le jeu de résultats précédent et dissocie les colonnes. Si *bBind* est **true**, il lie les nouvelles colonnes.  
  
Vous devez appeler cette fonction uniquement si vous avez spécifié plusieurs résultats en définissant le `CCommand` paramètre de modèle *TMultiple*=`CMultipleResults`. 

## <a name="open"></a> CCommand::Open

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
[in] La session dans laquelle exécuter la commande.  
  
*wszCommand*<br/>
[in] La commande à exécuter, transmis sous forme de chaîne Unicode. Peut être NULL lors de l’utilisation `CAccessor`, auquel cas la commande sera extraite de la valeur passée à la [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Consultez [ICommand::Execute](/previous-versions/windows/desktop/ms718095\(v=vs.85\)) dans le *de référence du programmeur OLE DB* pour plus d’informations.  
  
*szCommand*<br/>
[in] Identique à *wszCommand* , à ceci près que ce paramètre accepte une chaîne de commande ANSI. Le quatrième écran de cette méthode peut prendre une valeur NULL. Consultez « Remarques » plus loin dans cette rubrique pour plus d’informations.  
  
*pPropSet*<br/>
[in] Un pointeur vers un tableau de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) dans le *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
*pRowsAffected*<br/>
[entrée/sortie] Pointeur vers la mémoire où le nombre de lignes affectées par une commande est retourné. Si  *\*pRowsAffected* est NULL, aucun décompte de lignes est retourné. Sinon, `Open` définit  *\*pRowsAffected* selon les conditions suivantes :  
  
|If|Then|  
|--------|----------|  
|Le `cParamSets` élément de `pParams` est supérieur à 1|*\*pRowsAffected* représente le nombre total de lignes affectées par tous les jeux de paramètres spécifiés dans l’exécution.|  
|Le nombre de lignes affectées n’est pas disponible|*\*pRowsAffected* est définie sur -1.|  
|La commande ne met pas à jour, supprimer ou insérer des lignes|*\*pRowsAffected* n’est pas défini.|  
  
*guidCommand*<br/>
[in] Un GUID qui spécifie la syntaxe et les règles générales pour le fournisseur à utiliser dans l’analyse du texte de commande. Consultez [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\)) et [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757\(v=vs.85\)) dans le *de référence du programmeur OLE DB* pour plus d’informations.  
  
*bBind*<br/>
[in] Spécifie s’il faut lier la commande automatiquement après en cours d’exécution. La valeur par défaut est **true**, ce qui entraîne la commande à lier automatiquement. Paramètre *bBind* à **false** empêche la liaison automatique de la commande de sorte que vous pouvez lier manuellement. (Liaison manuelle est un intérêt particulier pour les utilisateurs OLAP).  
  
*ulPropSets*<br/>
[in] Le nombre de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) structures passées dans le *pPropSet* argument.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Les trois premiers formulaires de `Open` prendre une session, créer une commande et exécuter la commande, tous les paramètres de liaison en fonction des besoins.  
  
La première forme de `Open` prend une chaîne de commande Unicode et n’a aucune valeur par défaut.  
  
La deuxième forme de `Open` prend une chaîne de commande ANSI et aucune valeur par défaut (fourni pour la compatibilité descendante avec les applications existantes de ANSI).  
  
La troisième forme de `Open` permet à la chaîne de commande à être NULL, en raison de type **int** avec une valeur par défaut NULL. Il est fourni pour appeler `Open(session, NULL);` ou `Open(session);` , car la valeur NULL est de type **int**. Cette version requiert et déclare que le **int** paramètre être NULL.  
  
Le quatrième écran de `Open` lorsque vous avez déjà créé une commande et que vous souhaitez effectuer une seule [préparation](../../data/oledb/ccommand-prepare.md) et plusieurs exécutions.  
  
> [!NOTE]
>  `Open` appels `Execute`, qui appelle à son tour `GetNextResult`. 

## <a name="create"></a> CCommand::Create

Appels [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) pour créer une commande pour la session spécifiée, puis appelle [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\)) pour spécifier le texte de commande.  
  
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
[in] Une session sur laquelle créer la commande.  
  
*wszCommand*<br/>
[in] Pointeur vers le texte Unicode de la chaîne de commande.  
  
*szCommand*<br/>
[in] Pointeur vers le texte ANSI de la chaîne de commande.  
  
*guidCommand*<br/>
[in] Un GUID qui spécifie la syntaxe et les règles générales pour le fournisseur à utiliser dans l’analyse du texte de commande. Pour obtenir une description des dialectes, consultez [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

La première forme de `Create` prend une chaîne de commande Unicode. La deuxième forme de `Create` accepte une chaîne de commande ANSI (fournie pour la compatibilité descendante avec les applications existantes de ANSI).

## <a name="createcommand"></a> CCommand::CreateCommand

Crée une nouvelle commande.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  

*session*<br/>
[in] Un `CSession` objet à associer à la nouvelle commande.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Cette méthode crée une commande à l’aide de l’objet de session spécifié.  

## <a name="getparameterinfo"></a> CCommand::GetParameterInfo

Obtient une liste de paramètres de la commande, leurs noms et leurs types.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.   

## <a name="prepare"></a> CCommand::Prepare

Valide et optimise la commande actuelle.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  

*cExpectedRuns*<br/>
[in] Le nombre de fois que vous devez exécuter la commande.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Cette méthode encapsule la méthode OLE DB [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370\(v=vs.85\)).  

## <a name="releasecommand"></a> CCommand::ReleaseCommand

Libère l’accesseur de paramètre, puis libère de la commande elle-même.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
```  
  
### <a name="remarks"></a>Notes  

`ReleaseCommand` est utilisé conjointement avec `Close`. Consultez [fermer](../../data/oledb/ccommand-close.md) pour plus d’informations. 

## <a name="setparameterinfo"></a> CCommand::SetParameterInfo

Spécifie le type natif de chaque paramètre de commande.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  

Consultez [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393\(v=vs.85\)) dans le *de référence du programmeur OLE DB*.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  

## <a name="unprepare"></a> CCommand::Unprepare

Ignore le plan d’exécution de commande actuelle.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::Unprepare() throw();  
```  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Cette méthode encapsule la méthode OLE DB [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635\(v=vs.85\)). 
  
## <a name="see-also"></a>Voir aussi  

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)