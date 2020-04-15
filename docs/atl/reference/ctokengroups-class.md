---
title: Classe CTokenGroups
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
ms.openlocfilehash: 1e9d21c59eb5efabf036fbc938a40de2c4b7a0b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330552"
---
# <a name="ctokengroups-class"></a>Classe CTokenGroups

Cette classe est un `TOKEN_GROUPS` emballage pour la structure.

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
|[CTokenGroups: :CTokenGroups](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTokenGroups::Ajouter](#add)|Ajoute `CSid` une `TOKEN_GROUPS` structure ou `CTokenGroups` une structure existante à l’objet.|
|[CTokenGroups::Delete](#delete)|Supprime un `CSid` et ses attributs `CTokenGroups` associés de l’objet.|
|[CTokenGroups::DeleteAll](#deleteall)|Supprime tous `CSid` les objets et leurs `CTokenGroups` attributs associés de l’objet.|
|[CTokenGroups::GetCount](#getcount)|Retourne le `CSid` nombre d’objets et `CTokenGroups` d’attributs associés contenus dans l’objet.|
|[CTokenGroups::GetLength](#getlength)|Retourne la taille `CTokenGroups` de l’objet.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Récupère un pointeur `TOKEN_GROUPS` de la structure.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Récupère les `CSid` objets et les `CTokenGroups` attributs appartenant à l’objet.|
|[CTokenGroups::LookupSid](#lookupsid)|Récupère les attributs associés `CSid` à un objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CTokenGroups::l’opérateur const TOKEN_GROUPS](#operator_const_token_groups__star)|Jette l’objet `CTokenGroups` à un `TOKEN_GROUPS` pointeur de la structure.|
|[CTokenGroups::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Un [jeton d’accès](/windows/win32/SecAuthZ/access-tokens) est un objet qui décrit le contexte de sécurité d’un processus ou d’un thread et qui est attribué à chaque utilisateur connecté à un système Windows.

La `CTokenGroups` classe est un emballage pour la structure [TOKEN_GROUPS,](/windows/win32/api/winnt/ns-winnt-token_groups) contenant des informations sur les identifiants de sécurité du groupe (SID) dans un jeton d’accès.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Ajouter

Ajoute `CSid` une `TOKEN_GROUPS` structure ou `CTokenGroups` une structure existante à l’objet.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Un objet [CSid.](../../atl/reference/csid-class.md)

*dwAttributes*<br/>
Les attributs à `CSid` associer à l’objet.

*rTokenGroups (en anglais)*<br/>
Une structure [TOKEN_GROUPS.](/windows/win32/api/winnt/ns-winnt-token_groups)

### <a name="remarks"></a>Notes

Ces méthodes ajoutent `CSid` un ou plusieurs objets `CTokenGroups` et leurs attributs associés à l’objet.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Constructeur.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’objet `CTokenGroups` ou [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) structure avec laquelle `CTokenGroups` construire l’objet.

### <a name="remarks"></a>Notes

L’objet `CTokenGroups` peut être créé `TOKEN_GROUPS` en option `CTokenGroups` à l’aide d’une structure ou d’un objet précédemment défini.

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups: :CTokenGroups

Destructeur.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete

Supprime un `CSid` et ses attributs `CTokenGroups` associés de l’objet.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
[L’objet CSid](../../atl/reference/csid-class.md) pour lequel l’identifiant de sécurité (SID) et les attributs doivent être supprimés.

### <a name="return-value"></a>Valeur de retour

Retourne vrai `CSid` si le est enlevé, faux autrement.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll

Supprime tous `CSid` les objets et leurs `CTokenGroups` attributs associés de l’objet.

```
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount

Retourne le `CSid` nombre d’objets contenus dans `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’objets [CSid](../../atl/reference/csid-class.md) et `CTokenGroups` leurs attributs associés contenus dans l’objet.

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength

Retourne la taille `CTokenGroup` de l’objet.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Notes

Retourne la taille `CTokenGroup` totale de l’objet, dans les octets.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Récupère un pointeur `TOKEN_GROUPS` de la structure.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) sur la structure TOKEN_GROUPS `CTokenGroups` appartenant à l’objet symbolique d’accès.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Récupère les `CSid` objets et (optionnellement) les `CTokenGroups` attributs appartenant à l’objet.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSids*<br/>
Pointeur vers une gamme d’objets [CSid.](../../atl/reference/csid-class.md)

*pAttributes*<br/>
Pointeur vers un tableau de DWORDs. Si ce paramètre est omis ou NULL, les attributs ne sont pas récupérés.

### <a name="remarks"></a>Notes

Cette méthode énumérera tous `CSid` les objets `CTokenGroups` contenus dans l’objet et les placera et (optionnellement) les drapeaux d’attribut dans des objets de tableau.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::LookupSid

Récupère les attributs associés `CSid` à un objet.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
[L’objet CSid.](../../atl/reference/csid-class.md)

*pdwAttributes*<br/>
Pointeur vers un DWORD `CSid` qui acceptera l’attribut de l’objet. S’il est omis ou NULL, l’attribut ne sera pas récupéré.

### <a name="return-value"></a>Valeur de retour

Retourne vrai `CSid` si le est trouvé, faux autrement.

### <a name="remarks"></a>Notes

Réglage *pdwAttributes* à NULL fournit un moyen `CSid` de confirmer l’existence de l’attribut sans accéder à l’attribut. Notez que cette méthode ne doit pas être utilisée pour vérifier les droits d’accès. Les applications doivent plutôt utiliser la [méthode CAccessToken::CheckTokenMembership.](../../atl/reference/caccesstoken-class.md#checktokenmembership)

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::opérateur

Opérateur d'assignation.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’objet `CTokenGroups` ou [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) structure à `CTokenGroups` attribuer à l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CTokenGroups`

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::l’opérateur const TOKEN_GROUPS

Jette une valeur à un `TOKEN_GROUPS` pointeur de la structure.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Notes

Lance une valeur à un pointeur de la structure [TOKEN_GROUPS.](/windows/win32/api/winnt/ns-winnt-token_groups)

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[Classe CSid](../../atl/reference/csid-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
