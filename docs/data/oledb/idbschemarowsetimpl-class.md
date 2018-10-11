---
title: IDBSchemaRowsetImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e4701b3731233144550ddbc1dd38ae43d14c786f
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083071"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl (classe)

Fournit l’implémentation pour les ensembles de lignes de schéma.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
### <a name="parameters"></a>Paramètres  

*SessionClass*<br/>
Classe par laquelle `IDBSchemaRowsetImpl` est hérité. En général, cette classe est la classe session de l’utilisateur. 

## <a name="requirements"></a>Configuration requise  

**En-tête :** atldb.h  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CheckRestrictions](#checkrestrictions)|Vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.|  
|[CreateSchemaRowset](#createschemarowset)|Implémente une fonction du créateur d’objet COM pour l’objet spécifié par le paramètre de modèle.|  
|[SetRestrictions](#setrestrictions)|Spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.|  
  
### <a name="interface-methods"></a>Méthodes d’interface  
  
|||  
|-|-|  
|[GetRowset](#getrowset)|Retourne un ensemble de lignes de schéma.|  
|[GetSchemas](#getschemas)|Retourne une liste d’ensembles de lignes de schéma accessibles par [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|  
  
## <a name="remarks"></a>Notes  

Cette classe implémente l’interface [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) et la fonction de créateur mise en modèle [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).  
  
OLE DB utilise les ensembles de lignes de schéma pour retourner des données à propos des données d’un fournisseur. Ces données sont souvent appelées « métadonnées ». Par défaut, un fournisseur doit toujours prendre en charge `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, et `DBSCHEMA_PROVIDER_TYPES`, comme décrit dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) dans le *de référence du programmeur OLE DB*. Les ensembles de lignes de schéma sont désignés dans un mappage de schéma. Pour plus d’informations sur les entrées de mappage de schéma, consultez [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).  
  
L’Assistant Fournisseur OLE DB, dans l’Assistant Objet ATL, génère automatiquement le code pour les ensembles de lignes de schéma dans votre projet. (Par défaut, l’Assistant prend en charge les ensembles de lignes de schéma obligatoires précédemment mentionnés.) Quand vous créez un consommateur à l’aide de l’Assistant Objet ATL, l’Assistant utilise les ensembles de lignes de schéma pour lier les données appropriées à un fournisseur. Si vous n’implémentez pas vos ensembles de lignes de schéma pour fournir les métadonnées correctes, l’Assistant ne lie pas les bonnes données.  
  
Pour plus d’informations sur la prise en charge des ensembles de lignes de schéma dans votre fournisseur, consultez [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).  
  
Pour plus d’informations sur les ensembles de lignes de schéma, consultez [Ensembles de lignes de schéma](/previous-versions/windows/desktop/ms712921) dans les *Informations de référence du programmeur OLE DB*.  

## <a name="checkrestrictions"></a> IDBSchemaRowsetImpl::CheckRestrictions

Vérifie la validité des restrictions par rapport à un ensemble de lignes de schéma.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>Paramètres  

*rguidSchema*<br/>
[in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).  
  
*cRestrictions*<br/>
[in] Nombre de restrictions passées par le consommateur pour l’ensemble de lignes de schéma.  
  
*rgRestrictions*<br/>
[in] Tableau de longueur *cRestrictions* des valeurs de restriction à définir. Pour plus d’informations, consultez la description de la *rgRestrictions* paramètre dans [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
### <a name="remarks"></a>Notes  

Utilisez la méthode `CheckRestrictions` pour vérifier la validité des restrictions par rapport à un ensemble de lignes de schéma. Il vérifie les restrictions pour `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, et `DBSCHEMA_PROVIDER_TYPES` ensembles de lignes de schéma. Appelez-la pour déterminer si un consommateur l’appel à `IDBSchemaRowset::GetRowset` est correct. Si vous voulez prendre en charge d’autres ensembles de lignes de schéma que ceux répertoriés ci-dessus, vous devez créer votre propre fonction pour mener à bien cette tâche.  
  
`CheckRestrictions` Détermine si le consommateur appelle [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) avec la restriction et le type de restriction appropriés (par exemple, VT_BSTR pour une chaîne) qui prend en charge par le fournisseur. De même, elle détermine si le nombre correct de restrictions est pris en charge. Par défaut, `CheckRestrictions` demande au fournisseur, via l’appel [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) , quelles restrictions il prend en charge dans un ensemble de lignes donné. La méthode compare ensuite les restrictions du consommateur à celles que prend en charge le fournisseur avant d’aboutir ou d’échouer.  
  
Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) dans le *de référence du programmeur OLE DB* dans le SDK Windows.  

## <a name="createschemarowset"></a> IDBSchemaRowsetImpl::CreateSchemaRowset

Implémente une fonction du créateur d’objet COM pour l’objet spécifié par le paramètre de modèle.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  

*pUnkOuter*<br/>
[in] Externe [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) lors de l’agrégation, sinon NULL.  
  
*cRestrictions*<br/>
[in] Nombre de restrictions appliquées à l’ensemble de lignes du schéma.  
  
*rgRestrictions*<br/>
[in] Tableau de `cRestrictions`**s de**à appliquer à l’ensemble de lignes.  
  
*riid*<br/>
[in] L’interface à [QueryInterface](../../atl/queryinterface.md) pour sur la sortie `IUnknown`.  
  
*cPropertySets*<br/>
[in] Nombre de sets de propriétés à définir.  
  
*rgPropertySets*<br/>
[in] Tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367) qui spécifient les propriétés définies.  
  
*ppRowset*<br/>
[out] Sortant `IUnknown` demandé par *riid*. Cela `IUnknown` est une interface sur l’objet d’ensemble de lignes de schéma.  
  
*pSchemaRowset*<br/>
[out] Pointeur vers une instance de la classe d’ensemble de lignes du schéma. Ce paramètre n’est généralement pas utilisé, mais il peut l’être si vous devez effectuer des tâches supplémentaires sur l’ensemble de lignes du schéma avant de le passer à un objet COM. La durée de vie de *pSchemaRowset* est liée par *ppRowset*.  
  
### <a name="return-value"></a>Valeur de retour  

Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  

Cette fonction implémente un créateur générique pour tous les types d’ensembles de lignes du schéma. En règle générale, l’utilisateur n’appelle pas cette fonction. Elle est appelée par l’implémentation du mappage de schéma. 

## <a name="setrestrictions"></a> IDBSchemaRowsetImpl::SetRestrictions

Spécifie les restrictions que vous prenez en charge sur un ensemble de lignes de schéma particulier.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void SetRestrictions(ULONG cRestrictions,  
   GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>Paramètres  

*cRestrictions*<br/>
[in] Le nombre de restrictions dans le *rgRestrictions* tableau et le nombre de GUID dans le *rguidSchema* tableau.  
  
*rguidSchema*<br/>
[in] Tableau des GUID des ensembles de lignes de schéma pour lesquels les restrictions doivent être récupérées. Chaque élément de tableau contient le GUID d’un ensemble de lignes de schéma (par exemple, `DBSCHEMA_TABLES`).  
  
*rgRestrictions*<br/>
[in] Tableau de longueur *cRestrictions* des valeurs de restriction à définir. Chaque élément correspond aux restrictions de l’ensemble de lignes de schéma identifié par le GUID. Si un ensemble de lignes de schéma n’est pas pris en charge par le fournisseur, la valeur définie de l’élément est zéro. Dans le cas contraire, la valeur **ULONG** contient un masque de bits qui représente les restrictions prises en charge sur cet ensemble de lignes de schéma. Pour plus d’informations sur les restrictions correspondant à un ensemble de lignes de schéma particulier, consultez le tableau de GUID du jeu de lignes de schéma dans [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) dans le *de référence du programmeur OLE DB* dans le Windows KIT DE DÉVELOPPEMENT LOGICIEL.  
  
### <a name="remarks"></a>Notes  

Le `IDBSchemaRowset` object appelle `SetRestrictions` pour déterminer les restrictions que vous prenez en charge sur un ensemble de lignes de schéma déterminé (elle est appelée par [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) via un pointeur converti en supertype). Les restrictions permettent aux consommateurs de récupérer uniquement les lignes correspondantes (par exemple, toutes les colonnes de la table « MaTable »). Les restrictions sont facultatives, et dans le cas où aucune n’est prise en charge (par défaut), toutes les données sont systématiquement retournées.  
  
L’implémentation par défaut de cette méthode définit le *rgRestrictions* 0 éléments de tableau. Remplacez la valeur par défaut dans votre classe session pour définir d’autres restrictions que celle par défaut.  
  
Pour plus d’informations sur l’implémentation de la prise en charge des ensembles de lignes de schéma, consultez [Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md).  
  
Pour obtenir un exemple de fournisseur qui prend en charge les ensembles de lignes de schéma, consultez l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .  
  
Pour plus d’informations sur les ensembles de lignes de schéma, consultez [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) dans le *de référence du programmeur OLE DB* dans le SDK Windows. 
  
## <a name="getrowset"></a> IDBSchemaRowsetImpl::GetRowset

Retourne un ensemble de lignes de schéma.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>Paramètres  

*pUnkOuter*<br/>
[in] Externe `IUnknown` pendant l’agrégation ; sinon, NULL.  
  
*rguidSchema*<br/>
[in] Référence au GUID d’ensemble de lignes de schéma demandé (par exemple, `DBSCHEMA_TABLES`).  
  
*cRestrictions*<br/>
[in] Nombre de restrictions à appliquer à l’ensemble de lignes.  
  
*rgRestrictions*<br/>
[in] Tableau d’objets `cRestrictions`**VARIANT**qui représentent les restrictions.  
  
*riid*<br/>
[in] IID associé à la demande portant sur l’ensemble de lignes de schéma nouvellement créé.  
  
*cPropertySets*<br/>
[in] Nombre de sets de propriétés à définir.  
  
*rgPropertySets*<br/>
[in/out] Tableau de structures [DBPROPSET](/previous-versions/windows/desktop/ms714367) à définir sur l’ensemble de lignes de schéma nouvellement créé.  
  
*ppRowset*<br/>
[out] Pointeur désignant l’interface demandée sur l’ensemble de lignes de schéma nouvellement créé.  
  
### <a name="remarks"></a>Notes  

Cette méthode impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. En utilisant les informations de mappage de schéma, `GetRowset` crée un objet rowset donné si le *rguidSchema* paramètre est égal à une des entrées de mappage GUID. Consultez [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) pour obtenir une description de l’entrée de mappage.  
  
Consultez [IDBSchemaRowset::GetRowset](/previous-versions/windows/desktop/ms722634) dans le Kit de développement logiciel Windows.  

## <a name="getschemas"></a> IDBSchemaRowsetImpl::GetSchemas

Retourne une liste d’ensembles de lignes de schéma accessibles par [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest);  
```  
  
#### <a name="parameters"></a>Paramètres  

*pcSchemas*<br/>
[out] Pointeur désignant un **ULONG** complété du nombre de schémas.  
  
*prgSchemas*<br/>
[out] Pointeur désignant un tableau de GUID complété d’un pointeur désignant un tableau de GUID d’ensembles de lignes de schéma.  
  
*prgRest*<br/>
[out] Pointeur désignant un tableau de **ULONG**qui doit être complété du tableau de restrictions.  
  
### <a name="remarks"></a>Notes  

Cette méthode retourne un tableau de tous les ensembles de lignes de schéma pris en charge par le fournisseur. Consultez [IDBSchemaRowset::GetSchemas](/previous-versions/windows/desktop/ms719605) dans le Kit de développement logiciel Windows.  
  
L’implémentation de cette fonction impose à l’utilisateur de disposer d’un mappage de schéma dans la classe session. À partir des informations de mappage de schéma, elle répond ensuite avec le tableau de GUID des schémas contenus dans le mappage. Il s’agit des schémas pris en charge par le fournisseur.  

## <a name="see-also"></a>Voir aussi  

[Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Prise en charge des ensembles de lignes de schéma](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)