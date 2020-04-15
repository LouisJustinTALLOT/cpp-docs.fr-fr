---
title: Classe CSid
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330916"
---
# <a name="csid-class"></a>Classe CSid

Cette classe est un `SID` emballage pour une structure (identifiant de sécurité).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSid
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Tableau d'objets `CSid`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSid::CSid](#csid)|Constructeur.|
|[CSid: :CSid](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Retourne le nom du compte `CSid` associé à l’objet.|
|[CSid::Domain](#domain)|Retourne le nom du domaine `CSid` associé à l’objet.|
|[CSid::EqualPrefix](#equalprefix)|Tests `SID` (identifiant de sécurité) préfixes pour l’égalité.|
|[CSid::GetLength](#getlength)|Retourne la longueur `CSid` de l’objet.|
|[CSid::GetPSID](#getpsid)|Retourne un pointeur à une `SID` structure.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Retourne un pointeur à la `SID_IDENTIFIER_AUTHORITY` structure.|
|[CSid::GetSubAuthority](#getsubauthority)|Retourne une sous-autorité spécifiée dans une `SID` structure.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Retourne le nombre de sous-auteurs.|
|[CSid::IsValid](#isvalid)|Teste `CSid` l’objet pour obtenir de la validité.|
|[CSid::LoadAccount](#loadaccount)|Mise `CSid` à jour de l’objet compte `SID` tenu du nom et du domaine du compte, ou d’une structure existante.|
|[CSid::Sid](#sid)|Retourne la chaîne d’identification.|
|[CSid::SidNameUse](#sidnameuse)|Renvoie une description de `CSid` l’état de l’objet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur](#operator_eq)|Opérateur d'assignation.|
|[l’opérateur const SID](#operator_const_sid__star)|Jette un `CSid` objet à un `SID` pointeur à une structure.|

### <a name="global-operators"></a>Opérateurs mondiaux

|||
|-|-|
|[opérateur](#operator_eq_eq)|Teste deux objets descripteur de sécurité pour l’égalité|
|[opérateur !](#operator_neq)|Teste deux objets descripteur de sécurité pour l’inégalité|
|[Opérateur\<](#operator_lt)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[>de l’opérateur](#operator_gt)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[Opérateur\<=](#operator_lt__eq)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[>de l’opérateur](#operator_gt__eq)|Compare la valeur relative de deux objets descripteurs de sécurité.|

## <a name="remarks"></a>Notes

La `SID` structure est une structure à longueur variable utilisée pour identifier uniquement les utilisateurs ou les groupes.

Les applications ne `SID` doivent pas modifier la structure directement, mais plutôt utiliser les méthodes fournies dans cette classe d’emballage. Voir aussi [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupsid](security-global-functions.md#atlgetgroupsid), et [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::AccountName

Retourne le nom du compte `CSid` associé à l’objet.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne le LPCTSTR indiquant le nom du compte.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver `SID` un nom pour l’identifiant de sécurité spécifié). Pour plus de détails, voir [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si aucun nom `SID` de compte `AccountName` pour le peut être trouvé, retourne une chaîne vide. Cela peut se produire si un délai d’attente réseau empêche cette méthode de trouver le nom. Il se produit également pour les identifiants de `SID` sécurité sans nom de compte correspondant, comme un qui identifie une session de connexion.

## <a name="csidcsid"></a><a name="csid"></a>CSid::CSid

Constructeur.

```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Une `CSid` structure `SID` existante d’objet ou (identifiant de sécurité).

*IdentifierAuthority*<br/>
L’autorité.

*nSubAuthorityCount (en)*<br/>
Le compte de sous-autorité.

*pszAccountName*<br/>
Nom du compte.

*pszSystem (en)*<br/>
Le nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Un pointeur `SID` vers une structure.

### <a name="remarks"></a>Notes

Le constructeur initialise `CSid` l’objet, définissant un membre interne des données à *SidTypeInvalid*, ou en copiant les paramètres d’un compte existant, `CSid` `SID`, ou existant.

En cas d’échec de l’initialisation, le constructeur lancera une [classe CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a>CSid: :CSid

Destructeur.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet.

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray

Une gamme d’objets [CSid.](../../atl/reference/csid-class.md)

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Notes

Ce tapdef spécifie le type de tableau qui peut être utilisé pour récupérer les identifiants de sécurité d’un ACL (liste de contrôle d’accès). Voir [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a>CSid::Domain

Retourne le nom du domaine `CSid` associé à l’objet.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne `LPCTSTR` le pointage vers le domaine.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver `SID` un nom pour l’identifiant de sécurité spécifié). Pour plus de détails, voir [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si aucun nom `SID` de compte `Domain` pour le peut être trouvé, retourne le domaine comme une chaîne vide. Cela peut se produire si un délai d’attente réseau empêche cette méthode de trouver le nom. Il se produit également pour les identifiants de `SID` sécurité sans nom de compte correspondant, comme un qui identifie une session de connexion.

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix

Tests `SID` (identifiant de sécurité) préfixes pour l’égalité.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
La `SID` structure (identifiant `CSid` de sécurité) ou l’objet à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Voir [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) dans le Windows SDK pour plus de détails.

## <a name="csidgetlength"></a><a name="getlength"></a>CSid::GetLength

Retourne la longueur `CSid` de l’objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur dans `CSid` les octets de l’objet.

### <a name="remarks"></a>Notes

Si `CSid` la structure n’est pas valide, la valeur de rendement n’est pas définie. Avant `GetLength`d’appeler, utilisez le [CSid::IsValid](#isvalid) fonction membre pour vérifier qui `CSid` est valide.

> [!NOTE]
> Sous débog construit la fonction provoquera `CSid` un ASSERT si l’objet n’est pas valide.

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID

Renvoie un `SID` pointeur à une structure (identifiant de sécurité).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne l’adresse `CSid` de la `SID` structure sous-jacente de l’objet.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

Retourne un pointeur à la `SID_IDENTIFIER_AUTHORITY` structure.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle `SID_IDENTIFIER_AUTHORITY` renvoie l’adresse de la structure. En cas d’échec, la valeur de rendement n’est pas définie. L’échec peut `CSid` se produire si l’objet n’est pas valide, auquel cas la méthode [CSid::IsValid](#isvalid) retourne FALSE. La `GetLastError` fonction peut être appelée pour des informations d’erreur étendues.

> [!NOTE]
> Sous débog construit la fonction provoquera `CSid` un ASSERT si l’objet n’est pas valide.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority

Renvoie une sous-autorité `SID` spécifiée dans une structure (identifiant de sécurité).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Paramètres

*nSubAuthority (en)*<br/>
La sous-autorité.

### <a name="return-value"></a>Valeur de retour

Retourne la sous-autorité référencée par *nSubAuthority.* La valeur de sous-autorité est un identifiant relatif (RID).

### <a name="remarks"></a>Notes

Le paramètre *nSubAuthority* spécifie une valeur indicative identifiant l’élément de tableau de sous-auteur que la méthode retournera. La méthode n’effectue aucun test de validation sur cette valeur. Une application peut appeler [CSid::GetSubAuthorityCompe](#getsubauthoritycount) pour découvrir la gamme de valeurs acceptables.

> [!NOTE]
> Sous débog construit la fonction provoquera `CSid` un ASSERT si l’objet n’est pas valide.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount

Retourne le nombre de sous-auteurs.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est le nombre de sous-auteurs.

Si la méthode échoue, la valeur de retour n’est pas définie. La méthode échoue `CSid` si l’objet est invalide. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

> [!NOTE]
> Sous débog construit la fonction provoquera `CSid` un ASSERT si l’objet n’est pas valide.

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid::IsValid

Teste `CSid` l’objet pour obtenir de la validité.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI `CSid` si l’objet est valide, FALSE si ce n’est pas le cas. Il n’y a pas d’informations d’erreur prolongées pour cette méthode; n’appelez `GetLastError`pas .

### <a name="remarks"></a>Notes

La `IsValid` méthode valide `CSid` l’objet en vérifiant que le numéro de révision se trouve dans une plage connue et que le nombre de sous-auteurs est inférieur au maximum.

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::LoadAccount

Mise `CSid` à jour de l’objet compte tenu du nom et du domaine du compte, ou d’une structure SID (identifiant de sécurité) existante.

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszAccountName*<br/>
Nom du compte.

*pszSystem (en)*<br/>
Le nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Un pointeur vers une structure [de SMSN.](/windows/win32/api/winnt/ns-winnt-sid)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

`LoadAccount`tente de trouver un identifiant de sécurité pour le nom spécifié. Voir [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) pour plus de détails.

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::opérateur

Opérateur d'assignation.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou `CSid` d’attribuer à l’objet.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CSid` à l’objet mis à jour.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::opérateur

Teste deux objets descripteur de sécurité pour l’égalité.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identifiant `SID` de `CSid` sécurité (identifiant de sécurité) ou qui apparaît sur le côté gauche de l’opérateur.

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité (identifiant de sécurité) ou qui apparaît sur le côté droit de l’opérateur.

### <a name="return-value"></a>Valeur de retour

VRAI si les descripteurs de sécurité sont égaux, sinon FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::opérateur !

Teste deux objets descripteur de sécurité pour l’inégalité.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identificateur `SID` `CSid` de sécurité ou qui apparaît sur le côté gauche de l’opérateur ! .

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou qui apparaît sur le côté droit de l’opérateur ! .

### <a name="return-value"></a>Valeur de retour

VRAI si les descripteurs de sécurité ne sont pas égaux, sinon FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::opérateur&lt;

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identificateur `SID` `CSid` de sécurité ou qui apparaît sur le côté gauche de l’opérateur ! .

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou qui apparaît sur le côté droit de l’opérateur ! .

### <a name="return-value"></a>Valeur de retour

VRAI si *lhs* est moins de *rhs*, sinon FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::opérateur&lt;=

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identificateur `SID` `CSid` de sécurité ou qui apparaît sur le côté gauche de l’opérateur ! .

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou qui apparaît sur le côté droit de l’opérateur ! .

### <a name="return-value"></a>Valeur de retour

VRAI si *lhs* est moins ou égal à *rhs*, sinon FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::opérateur&gt;

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identificateur `SID` `CSid` de sécurité ou qui apparaît sur le côté gauche de l’opérateur ! .

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou qui apparaît sur le côté droit de l’opérateur ! .

### <a name="return-value"></a>Valeur de retour

VRAI si *lhs* est plus grand que *rhs*, sinon FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::opérateur&gt;=

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Paramètres

*Lhs*<br/>
L’identificateur `SID` `CSid` de sécurité ou qui apparaît sur le côté gauche de l’opérateur ! .

*rhs*<br/>
L’identifiant `SID` de `CSid` sécurité ou qui apparaît sur le côté droit de l’opérateur ! .

### <a name="return-value"></a>Valeur de retour

VRAI si *lhs* est plus grand ou égal à *rhs*, sinon FALSE.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::opérateur const SID\*

Lance un `CSid` objet à un `SID` pointeur vers une structure (identifiant de sécurité).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse `SID` de la structure.

## <a name="csidsid"></a><a name="sid"></a>CSid::Sid

Renvoie `SID` la structure (identifiant de sécurité) comme une chaîne.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne `SID` la structure comme une chaîne dans un format adapté à l’affichage, le stockage ou la transmission. Équivalent à [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse

Renvoie une description de `CSid` l’état de l’objet.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du membre de données qui `CSid` stocke une valeur décrivant l’état de l’objet.

|Valeur|Description|
|-----------|-----------------|
|SidTypeUser (en anglais seulement)|Indique un `SID` utilisateur (identifiant de sécurité).|
|SidTypeGroup (en anglais seulement)|Indique un `SID`groupe .|
|SidTypeDomain|Indique un `SID`domaine .|
|SidTypeAlias|Indique un `SID`alias .|
|SidTypeWellKnownGroup (en anglais seulement)|Indique `SID` un pour un groupe bien connu.|
|SidTypeDeletedAccount (en anglais seulement)|Indique `SID` un pour un compte supprimé.|
|SidTypeInvalid|Indique un `SID`invalide .|
|SidTypeUnknown|Indique un `SID` type inconnu.|
|SidTypeComputer (en anglais seulement)|Indique `SID` un pour un ordinateur.|

### <a name="remarks"></a>Notes

Appelez [CSid::LoadAccount](#loadaccount) pour `CSid` mettre `SidNameUse` à jour l’objet avant d’appeler pour retourner son état. `SidNameUse`ne modifie pas l’état de `LookupAccountName` l’objet (en appelant ou), `LookupAccountSid`mais ne renvoie que l’état actuel.

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)<br/>
[Opérateurs](../../atl/reference/atl-operators.md)
