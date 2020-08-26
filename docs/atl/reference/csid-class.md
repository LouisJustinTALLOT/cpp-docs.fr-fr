---
title: CSid (classe)
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
ms.openlocfilehash: b6787c0e3f075935f19d51aa73bbd66da9cc0fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835595"
---
# <a name="csid-class"></a>CSid (classe)

Cette classe est un wrapper pour une `SID` structure (identificateur de sécurité).

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
|[CSid :: CSidArray](#csidarray)|Tableau d'objets `CSid`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSid :: CSid](#csid)|Constructeur.|
|[CSid :: ~ CSid](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSid :: AccountName](#accountname)|Retourne le nom du compte associé à l' `CSid` objet.|
|[CSid ::D omaine](#domain)|Retourne le nom du domaine associé à l' `CSid` objet.|
|[CSid :: EqualPrefix](#equalprefix)|Tests `SID` (identificateur de sécurité) préfixes d’égalité.|
|[CSid :: GetLength](#getlength)|Retourne la longueur de l' `CSid` objet.|
|[CSid :: GetPSID](#getpsid)|Retourne un pointeur vers une `SID` structure.|
|[CSid :: GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Retourne un pointeur vers la `SID_IDENTIFIER_AUTHORITY` structure.|
|[CSid :: GetSubAuthority](#getsubauthority)|Retourne une sous-autorité spécifiée dans une `SID` structure.|
|[CSid :: GetSubAuthorityCount](#getsubauthoritycount)|Retourne le nombre de sous-autorités.|
|[CSid :: IsValid](#isvalid)|Teste la `CSid` validité de l’objet.|
|[CSid :: LoadAccount](#loadaccount)|Met à jour l' `CSid` objet en fonction du nom de compte et du domaine, ou d’une `SID` structure existante.|
|[CSid :: sid](#sid)|Retourne la chaîne d’ID.|
|[CSid :: SidNameUse](#sidnameuse)|Retourne une description de l’état de l' `CSid` objet.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur =](#operator_eq)|Opérateur d'assignation.|
|[SID const, opérateur *](#operator_const_sid__star)|Effectue un cast d’un `CSid` objet en pointeur vers une `SID` structure.|

### <a name="global-operators"></a>Opérateurs globaux

|Nom|Description|
|-|-|
|[opérateur = =](#operator_eq_eq)|Teste l’égalité de deux objets descripteurs de sécurité|
|[opérateur ! =](#operator_neq)|Teste l’inégalité de deux objets descripteurs de sécurité|
|[and \<](#operator_lt)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[>d’opérateur ](#operator_gt)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[and \<=](#operator_lt__eq)|Compare la valeur relative de deux objets descripteurs de sécurité.|
|[>opérateur =](#operator_gt__eq)|Compare la valeur relative de deux objets descripteurs de sécurité.|

## <a name="remarks"></a>Notes

La `SID` structure est une structure de longueur variable utilisée pour identifier de façon unique des utilisateurs ou des groupes.

Les applications ne doivent pas modifier la `SID` structure directement, mais utilisent à la place les méthodes fournies dans cette classe wrapper. Voir aussi [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)et [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Configuration requise

**En-tête :** ATLSecurity. h

## <a name="csidaccountname"></a><a name="accountname"></a> CSid :: AccountName

Retourne le nom du compte associé à l' `CSid` objet.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le LPCTSTR pointant vers le nom du compte.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver un nom pour le spécifié `SID` (identificateur de sécurité). Pour plus d’informations, consultez [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si aucun nom de compte n' `SID` est trouvé pour le, `AccountName` retourne une chaîne vide. Cela peut se produire si un délai d’attente réseau empêche cette méthode de trouver le nom. Il se produit également pour les identificateurs de sécurité sans nom de compte correspondant, tel qu’un `SID` qui identifie une session de connexion.

## <a name="csidcsid"></a><a name="csid"></a> CSid :: CSid

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
Un `CSid` objet existant ou une `SID` structure (identificateur de sécurité).

*IdentifierAuthority*<br/>
Autorité.

*nSubAuthorityCount*<br/>
Nombre de sous-autorités.

*pszAccountName*<br/>
Nom du compte.

*pszSystem*<br/>
Nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Pointeur vers une `SID` structure.

### <a name="remarks"></a>Notes

Le constructeur initialise l' `CSid` objet, en affectant la valeur *SidTypeInvalid*à un membre de données interne, ou en copiant les paramètres à partir d’un `CSid` compte existant, `SID` ou existant.

Si l’initialisation échoue, le constructeur lèvera une [classe CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a> CSid :: ~ CSid

Destructeur.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet.

## <a name="csidcsidarray"></a><a name="csidarray"></a> CSid :: CSidArray

Tableau d’objets [CSID](../../atl/reference/csid-class.md) .

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Notes

Ce typedef spécifie le type de tableau qui peut être utilisé pour récupérer des identificateurs de sécurité à partir d’une liste de contrôle d’accès (ACL). Consultez [CaCl :: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a> CSid ::D omaine

Retourne le nom du domaine associé à l' `CSid` objet.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le `LPCTSTR` pointant vers le domaine.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver un nom pour le spécifié `SID` (identificateur de sécurité). Pour plus d’informations, consultez [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Si aucun nom de compte n' `SID` est trouvé pour le, `Domain` retourne le domaine sous la forme d’une chaîne vide. Cela peut se produire si un délai d’attente réseau empêche cette méthode de trouver le nom. Il se produit également pour les identificateurs de sécurité sans nom de compte correspondant, tel qu’un `SID` qui identifie une session de connexion.

## <a name="csidequalprefix"></a><a name="equalprefix"></a> CSid :: EqualPrefix

Tests `SID` (identificateur de sécurité) préfixes d’égalité.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`SID`Structure ou objet (identificateur de sécurité) `CSid` à comparer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) dans le SDK Windows.

## <a name="csidgetlength"></a><a name="getlength"></a> CSid :: GetLength

Retourne la longueur de l' `CSid` objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la longueur en octets de l' `CSid` objet.

### <a name="remarks"></a>Notes

Si la `CSid` structure n’est pas valide, la valeur de retour n’est pas définie. Avant `GetLength` d’appeler, utilisez la fonction membre [CSID :: IsValid](#isvalid) pour vérifier que `CSid` est valide.

> [!NOTE]
> Sous les builds de débogage, la fonction provoque une assertion si l' `CSid` objet n’est pas valide.

## <a name="csidgetpsid"></a><a name="getpsid"></a> CSid :: GetPSID

Retourne un pointeur vers une `SID` structure (identificateur de sécurité).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’adresse de la `CSid` structure sous-jacente de l’objet `SID` .

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a> CSid :: GetPSID_IDENTIFIER_AUTHORITY

Retourne un pointeur vers la `SID_IDENTIFIER_AUTHORITY` structure.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, elle retourne l’adresse de la `SID_IDENTIFIER_AUTHORITY` structure. En cas d’échec, la valeur de retour n’est pas définie. Une défaillance peut se produire si l' `CSid` objet n’est pas valide, auquel cas la méthode [CSID :: IsValid](#isvalid) retourne la valeur false. La fonction `GetLastError` peut être appelée pour les informations d’erreur étendues.

> [!NOTE]
> Sous les builds de débogage, la fonction provoque une assertion si l' `CSid` objet n’est pas valide.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a> CSid :: GetSubAuthority

Retourne une sous-autorité spécifiée dans une `SID` structure (identificateur de sécurité).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Paramètres

*nSubAuthority*<br/>
Sous-autorité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la sous-autorité référencée par *nSubAuthority.* La valeur de la sous-autorité est un identificateur relatif (RID).

### <a name="remarks"></a>Notes

Le paramètre *nSubAuthority* spécifie une valeur d’index identifiant l’élément de tableau de sous-autorité que la méthode retournera. La méthode n’effectue aucun test de validation sur cette valeur. Une application peut appeler [CSID :: GetSubAuthorityCount](#getsubauthoritycount) pour découvrir la plage de valeurs acceptables.

> [!NOTE]
> Sous les builds de débogage, la fonction provoque une assertion si l' `CSid` objet n’est pas valide.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a> CSid :: GetSubAuthorityCount

Retourne le nombre de sous-autorités.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Si la méthode est réussie, la valeur de retour est le nombre de sous-autorités.

Si la méthode échoue, la valeur de retour n’est pas définie. La méthode échoue si l' `CSid` objet n’est pas valide. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

> [!NOTE]
> Sous les builds de débogage, la fonction provoque une assertion si l' `CSid` objet n’est pas valide.

## <a name="csidisvalid"></a><a name="isvalid"></a> CSid :: IsValid

Teste la `CSid` validité de l’objet.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l' `CSid` objet est valide, false dans le cas contraire. Il n’y a pas d’informations d’erreur étendues pour cette méthode. n’appelez pas `GetLastError` .

### <a name="remarks"></a>Notes

La `IsValid` méthode valide l' `CSid` objet en vérifiant que le numéro de révision se trouve dans une plage connue et que le nombre de sous-autorités est inférieur au maximum.

## <a name="csidloadaccount"></a><a name="loadaccount"></a> CSid :: LoadAccount

Met à jour l' `CSid` objet en fonction du nom de compte et du domaine, ou d’une structure d’identificateur de sécurité (SID) existante.

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

*pszSystem*<br/>
Nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Pointeur vers une structure [sid](/windows/win32/api/winnt/ns-winnt-sid) .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

`LoadAccount` tente de trouver un identificateur de sécurité pour le nom spécifié. Pour plus d’informations, consultez [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) .

## <a name="csidoperator-"></a><a name="operator_eq"></a> CSid :: Operator =

Opérateur d'assignation.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` à assigner à l' `CSid` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’objet mis à jour `CSid` .

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a> CSid :: Operator = =

Teste l’égalité de deux objets descripteurs de sécurité.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur = =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de l’opérateur = =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les descripteurs de sécurité sont égaux, sinon FALSe.

## <a name="csidoperator-"></a><a name="operator_neq"></a> CSid :: Operator ! =

Teste l’inégalité de deux objets descripteurs de sécurité.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ! =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît à droite de l’opérateur ! =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si les descripteurs de sécurité ne sont pas égaux, sinon FALSe.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a> CSid :: Operator &lt;

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ! =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît à droite de l’opérateur ! =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si *LHS* est inférieur à *RHS*, sinon false.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a> CSid :: Operator &lt;=

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ! =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît à droite de l’opérateur ! =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si *LHS* est inférieur ou égal à *RHS*, sinon false.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a> CSid :: Operator &gt;

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ! =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît à droite de l’opérateur ! =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si *LHS* est supérieur à *RHS*, sinon false.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a> CSid :: Operator &gt;=

Compare la valeur relative de deux objets descripteurs de sécurité.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ! =.

*rhs*<br/>
`SID`(Identificateur de sécurité) ou `CSid` qui apparaît à droite de l’opérateur ! =.

### <a name="return-value"></a>Valeur renvoyée

TRUE si *LHS* est supérieur ou égal à *RHS*, sinon false.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a> CSid :: Operator, SID const \*

Effectue un cast d’un `CSid` objet en pointeur vers une `SID` structure (identificateur de sécurité).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse de la `SID` structure.

## <a name="csidsid"></a><a name="sid"></a> CSid :: sid

Retourne la `SID` structure (identificateur de sécurité) sous la forme d’une chaîne.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la `SID` structure sous la forme d’une chaîne dans un format approprié pour l’affichage, le stockage ou la transmission. Équivalent à [ConvertSidToStringSid a](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a> CSid :: SidNameUse

Retourne une description de l’état de l' `CSid` objet.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur du membre de données qui stocke une valeur décrivant l’état de l' `CSid` objet.

|Valeur|Description|
|-----------|-----------------|
|SidTypeUser|Indique un utilisateur `SID` (identificateur de sécurité).|
|SidTypeGroup|Indique un groupe `SID` .|
|SidTypeDomain|Indique un domaine `SID` .|
|SidTypeAlias|Indique un alias `SID` .|
|SidTypeWellKnownGroup|Indique un `SID` pour un groupe bien connu.|
|SidTypeDeletedAccount|Indique un `SID` pour un compte supprimé.|
|SidTypeInvalid|Indique un non valide `SID` .|
|SidTypeUnknown|Indique un `SID` type inconnu.|
|SidTypeComputer|Indique un `SID` pour un ordinateur.|

### <a name="remarks"></a>Notes

Appelez [CSID :: LoadAccount](#loadaccount) pour mettre à jour l' `CSid` objet avant `SidNameUse` d’appeler pour retourner son état. `SidNameUse` ne modifie pas l’état de l’objet (en appelant à `LookupAccountName` ou `LookupAccountSid` ), mais retourne uniquement l’état actuel.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)<br/>
[Opérateurs](../../atl/reference/atl-operators.md)
