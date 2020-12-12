---
description: 'En savoir plus sur : classe CTokenGroups'
title: CTokenGroups, classe
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 3d6633afbd649aa175196f1fae8e62afdf784f99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140346"
---
# <a name="ctokengroups-class"></a>CTokenGroups, classe

Cette classe est un wrapper pour la `TOKEN_GROUPS` structure.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CTokenGroups
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Constructeur.|
|[CTokenGroups :: ~ CTokenGroups](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTokenGroups :: Add](#add)|Ajoute une `CSid` structure ou existante `TOKEN_GROUPS` à l' `CTokenGroups` objet.|
|[CTokenGroups ::D supprim](#delete)|Supprime un `CSid` et ses attributs associés de l' `CTokenGroups` objet.|
|[CTokenGroups ::D eleteAll](#deleteall)|Supprime tous les `CSid` objets et leurs attributs associés de l' `CTokenGroups` objet.|
|[CTokenGroups :: GetCount](#getcount)|Retourne le nombre d' `CSid` objets et les attributs associés contenus dans l' `CTokenGroups` objet.|
|[CTokenGroups :: GetLength](#getlength)|Retourne la taille de l' `CTokenGroups` objet.|
|[CTokenGroups :: GetPTOKEN_GROUPS](#getptoken_groups)|Récupère un pointeur vers la `TOKEN_GROUPS` structure.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Récupère les `CSid` objets et les attributs appartenant à l' `CTokenGroups` objet.|
|[CTokenGroups::LookupSid](#lookupsid)|Récupère les attributs associés à un `CSid` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenGroups :: Operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Convertit l' `CTokenGroups` objet en un pointeur vers la `TOKEN_GROUPS` structure.|
|[CTokenGroups :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est alloué à chaque utilisateur connecté à un système Windows.

La `CTokenGroups` classe est un wrapper pour la structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) , contenant des informations sur les identificateurs de sécurité (SID) de groupe dans un jeton d’accès.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="ctokengroupsadd"></a><a name="add"></a> CTokenGroups :: Add

Ajoute une `CSid` structure ou existante `TOKEN_GROUPS` à l' `CTokenGroups` objet.

```cpp
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) .

*dwAttributes*<br/>
Attributs à associer à l' `CSid` objet.

*rTokenGroups*<br/>
Structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) .

### <a name="remarks"></a>Notes

Ces méthodes ajoutent un ou plusieurs `CSid` objets et leurs attributs associés à l' `CTokenGroups` objet.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a> CTokenGroups::CTokenGroups

Constructeur.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CTokenGroups`Objet ou structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) avec laquelle construire l' `CTokenGroups` objet.

### <a name="remarks"></a>Notes

L' `CTokenGroups` objet peut éventuellement être créé à l’aide d’une `TOKEN_GROUPS` structure ou d’un objet défini précédemment `CTokenGroups` .

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a> CTokenGroups :: ~ CTokenGroups

Destructeur.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="ctokengroupsdelete"></a><a name="delete"></a> CTokenGroups ::D supprim

Supprime un `CSid` et ses attributs associés de l' `CTokenGroups` objet.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) pour lequel l’identificateur de sécurité (SID) et les attributs doivent être supprimés.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le `CSid` est supprimé ; sinon, false.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a> CTokenGroups ::D eleteAll

Supprime tous les `CSid` objets et leurs attributs associés de l' `CTokenGroups` objet.

```cpp
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a> CTokenGroups :: GetCount

Retourne le nombre d' `CSid` objets contenus dans `CTokenGroups` .

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’objets [CSID](../../atl/reference/csid-class.md) et leurs attributs associés contenus dans l' `CTokenGroups` objet.

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a> CTokenGroups :: GetLength

Retourne la taille de l' `CTokenGroup` objet.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Notes

Retourne la taille totale de l' `CTokenGroup` objet, en octets.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a> CTokenGroups :: GetPTOKEN_GROUPS

Récupère un pointeur vers la `TOKEN_GROUPS` structure.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Récupère un pointeur vers la structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) qui appartient à l' `CTokenGroups` objet de jeton d’accès.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a> CTokenGroups::GetSidsAndAttributes

Récupère les `CSid` objets et (éventuellement) les attributs appartenant à l' `CTokenGroups` objet.

```cpp
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSids*<br/>
Pointeur vers un tableau d’objets [CSID](../../atl/reference/csid-class.md) .

*pAttributes*<br/>
Pointeur vers un tableau de DWORDs. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés.

### <a name="remarks"></a>Notes

Cette méthode énumère tous les `CSid` objets contenus dans l' `CTokenGroups` objet et les place et (éventuellement) les indicateurs d’attribut dans des objets de tableau.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a> CTokenGroups::LookupSid

Récupère les attributs associés à un `CSid` objet.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) .

*pdwAttributes*<br/>
Pointeur vers un DWORD qui accepte l' `CSid` attribut de l’objet. En cas d’omission ou de valeur NULL, l’attribut n’est pas récupéré.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si `CSid` est trouvé ; sinon, false.

### <a name="remarks"></a>Notes

La définition de *pdwAttributes* sur la valeur null permet de confirmer l’existence du `CSid` sans accéder à l’attribut. Notez que cette méthode ne doit pas être utilisée pour vérifier les droits d’accès. À la place, les applications doivent utiliser la méthode [caccesstoken, :: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) .

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a> CTokenGroups :: Operator =

Opérateur d'assignation.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CTokenGroups`Objet ou structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) à assigner à l' `CTokenGroups` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CTokenGroups` .

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a> CTokenGroups :: Operator const TOKEN_GROUPS *

Convertit une valeur en pointeur vers la `TOKEN_GROUPS` structure.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Notes

Convertit une valeur en pointeur vers la structure [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) .

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[CSid (classe)](../../atl/reference/csid-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
