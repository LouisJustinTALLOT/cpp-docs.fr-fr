---
title: CSid, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 02b7cbb9e66e1e8297699503fc510247efed1629
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301894"
---
# <a name="csid-class"></a>CSid, classe

Cette classe est un wrapper pour un `SID` structure de (l’identificateur de sécurité).

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CSid::~CSid](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Retourne le nom du compte associé à la `CSid` objet.|
|[CSid::Domain](#domain)|Retourne le nom de domaine associé à la `CSid` objet.|
|[CSid::EqualPrefix](#equalprefix)|Tests `SID` préfixes (identificateur de sécurité) pour l’égalité.|
|[CSid::GetLength](#getlength)|Retourne la longueur de la `CSid` objet.|
|[CSid::GetPSID](#getpsid)|Retourne un pointeur vers un `SID` structure.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Retourne un pointeur vers le `SID_IDENTIFIER_AUTHORITY` structure.|
|[CSid::GetSubAuthority](#getsubauthority)|Retourne une sous-autorité spécifiée dans un `SID` structure.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Retourne le nombre de sous-autorité.|
|[CSid::IsValid](#isvalid)|Tests du `CSid` objet validité.|
|[CSid::LoadAccount](#loadaccount)|Mises à jour le `CSid` objet selon le nom du compte et de domaine ou un existant `SID` structure.|
|[CSid::Sid](#sid)|Retourne la chaîne d’identification.|
|[CSid::SidNameUse](#sidnameuse)|Retourne une description de l’état de la `CSid` objet.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator =](#operator_eq)|Opérateur d'assignation.|
|[SID const opérateur *](#operator_const_sid__star)|Les casts un `CSid` objet vers un autre pointeur vers un `SID` structure.|

### <a name="global-operators"></a>Opérateurs globaux

|||
|-|-|
|[operator ==](#operator_eq_eq)|Teste si deux objets de descripteur de sécurité pour l’égalité|
|[operator !=](#operator_neq)|Teste si deux objets de descripteur de sécurité pour vérifier leur inégalité|
|[Opérateur \<](#operator_lt_)|Compare la valeur relative de deux objets de descripteurs de sécurité.|
|[opérateur >](#operator_gt_)|Compare la valeur relative de deux objets de descripteurs de sécurité.|
|[Opérateur \<=](#operator_lt__eq)|Compare la valeur relative de deux objets de descripteurs de sécurité.|
|[operator >=](#operator_gt__eq)|Compare la valeur relative de deux objets de descripteurs de sécurité.|

## <a name="remarks"></a>Notes

Le `SID` structure est une structure de longueur variable utilisée pour identifier les utilisateurs ou groupes.

Les applications ne doivent pas modifier le `SID` structure directement, mais plutôt utiliser les méthodes fournies dans cette classe wrapper. Voir aussi [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), et [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsecurity.h

##  <a name="accountname"></a>  CSid::AccountName

Retourne le nom du compte associé à la `CSid` objet.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne le LPCTSTR pointant vers le nom du compte.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver un nom pour le texte spécifié `SID` (identificateur de sécurité). Pour plus d’informations, consultez [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si aucun nom de compte pour le `SID` peut être trouvé, `AccountName` retourne une chaîne vide. Cela peut se produire si un délai d’expiration réseau empêche cette méthode de recherche du nom. Elle se produit également pour les identificateurs de sécurité sans nom de compte correspondant, par exemple une ouverture de session `SID` qui identifie une ouverture de session.

##  <a name="csid"></a>  CSid::CSid

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
Un existant `CSid` objet ou `SID` structure de (l’identificateur de sécurité).

*IdentifierAuthority*<br/>
L’autorité.

*nSubAuthorityCount*<br/>
Le nombre de sous-autorité.

*pszAccountName*<br/>
Le nom du compte.

*pszSystem*<br/>
Le nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Un pointeur vers un `SID` structure.

### <a name="remarks"></a>Notes

Le constructeur initialise la `CSid` objet en affectant un membre de données interne *SidTypeInvalid*, ou en copiant les paramètres d’un existant `CSid`, `SID`, ou le compte existant.

Si l’initialisation échoue, le constructeur lève un [catlexception, classe](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  CSid::~CSid

Destructeur.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère les ressources acquises par l’objet.

##  <a name="csidarray"></a>  CSid::CSidArray

Un tableau de [CSid](../../atl/reference/csid-class.md) objets.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Notes

Ce typedef Spécifie le type de tableau qui peut être utilisé pour récupérer les identificateurs de sécurité à partir d’une liste ACL (liste de contrôle d’accès). Consultez [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Retourne le nom de domaine associé à la `CSid` objet.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne le `LPCTSTR` pointant vers le domaine.

### <a name="remarks"></a>Notes

Cette méthode tente de trouver un nom pour le texte spécifié `SID` (identificateur de sécurité). Pour plus d’informations, consultez [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Si aucun nom de compte pour le `SID` peut être trouvé, `Domain` retourne le domaine comme une chaîne vide. Cela peut se produire si un délai d’expiration réseau empêche cette méthode de recherche du nom. Elle se produit également pour les identificateurs de sécurité sans nom de compte correspondant, par exemple une ouverture de session `SID` qui identifie une ouverture de session.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Tests `SID` préfixes (identificateur de sécurité) pour l’égalité.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Le `SID` structure de (l’identificateur de sécurité) ou `CSid` objet à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Consultez [EqualPrefixSid](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) dans le SDK Windows pour plus d’informations.

##  <a name="getlength"></a>  CSid::GetLength

Retourne la longueur de la `CSid` objet.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la longueur en octets de la `CSid` objet.

### <a name="remarks"></a>Notes

Si le `CSid` structure n’est pas valide, la valeur de retour n’est pas définie. Avant d’appeler `GetLength`, utilisez le [CSid::IsValid](#isvalid) fonction membre pour vérifier que `CSid` est valide.

> [!NOTE]
>  Sous les versions debug la fonction provoque une assertion si le `CSid` objet n’est pas valide.

##  <a name="getpsid"></a>  CSid::GetPSID

Retourne un pointeur vers un `SID` structure de (l’identificateur de sécurité).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne l’adresse de la `CSid` sous-jacente de l’objet `SID` structure.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Retourne un pointeur vers le `SID_IDENTIFIER_AUTHORITY` structure.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, elle retourne l’adresse de la `SID_IDENTIFIER_AUTHORITY` structure. En cas d’échec, la valeur de retour est non définie. Échec peut se produire si le `CSid` objet n’est pas valide, auquel cas la [CSid::IsValid](#isvalid) méthode retourne FALSE. La fonction `GetLastError` peut être appelée pour les informations d’erreur étendues.

> [!NOTE]
>  Sous les versions debug la fonction provoque une assertion si le `CSid` objet n’est pas valide.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Retourne une sous-autorité spécifiée dans un `SID` structure de (l’identificateur de sécurité).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Paramètres

*nSubAuthority*<br/>
La sous-autorité.

### <a name="return-value"></a>Valeur de retour

Retourne la sous-autorité référencée par *nSubAuthority.* La valeur de sous-autorité est un identificateur relatif (RID).

### <a name="remarks"></a>Notes

Le *nSubAuthority* paramètre spécifie une valeur d’index identifiant l’élément de tableau sous-autorité la méthode est retournée. La méthode n’effectue aucun test de validation sur cette valeur. Une application peut appeler [CSid::GetSubAuthorityCount](#getsubauthoritycount) pour découvrir la plage de valeurs acceptables.

> [!NOTE]
>  Sous les versions debug la fonction provoque une assertion si le `CSid` objet n’est pas valide.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Retourne le nombre de sous-autorité.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est le nombre de sous-autorité.

Si la méthode échoue, la valeur de retour est non définie. La méthode échoue si le `CSid` objet n’est pas valide. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

> [!NOTE]
>  Sous les versions debug la fonction provoque une assertion si le `CSid` objet n’est pas valide.

##  <a name="isvalid"></a>  CSid::IsValid

Tests du `CSid` objet validité.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le `CSid` objet est valide, FALSE dans le cas contraire. Il n’existe aucune information d’erreur étendue pour cette méthode ; n’appelez pas `GetLastError`.

### <a name="remarks"></a>Notes

Le `IsValid` méthode valide le `CSid` objet en vérifiant que le numéro de révision est dans une plage connue et que le nombre de sous-autorités est inférieur au nombre maximal.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Mises à jour le `CSid` objet en fonction du nom de compte et de domaine ou d’une structure SID (identificateur de sécurité) existante.

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
Le nom du compte.

*pszSystem*<br/>
Le nom du système. Cette chaîne peut être le nom d’un ordinateur distant. Si cette chaîne est NULL, le système local est utilisé à la place.

*pSid*<br/>
Un pointeur vers un [SID](/windows/desktop/api/winnt/ns-winnt-_sid) structure.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

`LoadAccount` tente de trouver un identificateur de sécurité pour le nom spécifié. Consultez [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) pour plus d’informations.

##  <a name="operator_eq"></a>  CSid::operator =

Opérateur d'assignation.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` à affecter à la `CSid` objet.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la mise à jour `CSid` objet.

##  <a name="operator_eq_eq"></a>  CSid::operator ==

Teste les deux objets de descripteurs de sécurité pour l’égalité.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de l’opérateur ==.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de l’opérateur ==.

### <a name="return-value"></a>Valeur de retour

TRUE si les descripteurs de sécurité sont identiques, sinon, FALSE.

##  <a name="operator_neq"></a>  CSid::operator ! =

Teste si deux objets de descripteur de sécurité pour vérifier leur inégalité.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de la ! =, opérateur.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de la ! =, opérateur.

### <a name="return-value"></a>Valeur de retour

TRUE si les descripteurs de sécurité ne sont pas égaux ; sinon, FALSE.

##  <a name="operator_lt"></a>  CSid::operator &lt;

Compare la valeur relative de deux objets de descripteurs de sécurité.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de la ! =, opérateur.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de la ! =, opérateur.

### <a name="return-value"></a>Valeur de retour

TRUE si *lhs* est inférieure à *rhs*; sinon, FALSE.

##  <a name="operator_lt__eq"></a>  CSid::operator &lt;=

Compare la valeur relative de deux objets de descripteurs de sécurité.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de la ! =, opérateur.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de la ! =, opérateur.

### <a name="return-value"></a>Valeur de retour

TRUE si *lhs* est inférieure ou égale à *rhs*; sinon, FALSE.

##  <a name="operator_gt"></a>  CSid::operator &gt;

Compare la valeur relative de deux objets de descripteurs de sécurité.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de la ! =, opérateur.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de la ! =, opérateur.

### <a name="return-value"></a>Valeur de retour

TRUE si *lhs* est supérieur à *rhs*; sinon, FALSE.

##  <a name="operator_gt__eq"></a>  CSid::operator &gt;=

Compare la valeur relative de deux objets de descripteurs de sécurité.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté gauche de la ! =, opérateur.

*rhs*<br/>
Le `SID` (identificateur de sécurité) ou `CSid` qui apparaît sur le côté droit de la ! =, opérateur.

### <a name="return-value"></a>Valeur de retour

TRUE si *lhs* est supérieur ou égal à *rhs*; sinon, FALSE.

##  <a name="operator_const_sid__star"></a>  CSid::operator const SID \*

Les casts un `CSid` objet vers un autre pointeur vers un `SID` structure de (l’identificateur de sécurité).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Notes

Retourne l’adresse de la `SID` structure.

##  <a name="sid"></a>  CSid::Sid

Retourne le `SID` structure (identificateur de sécurité) sous forme de chaîne.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valeur de retour

Retourne le `SID` structure sous forme de chaîne dans un format approprié pour l’affichage, de stockage ou de transmission. Équivalent à [ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Retourne une description de l’état de la `CSid` objet.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du membre de données qui stocke une valeur qui décrit l’état de la `CSid` objet.

|Value|Description|
|-----------|-----------------|
|SidTypeUser|Indique qu’un utilisateur `SID` (identificateur de sécurité).|
|SidTypeGroup|Indique un groupe `SID`.|
|SidTypeDomain|Indique un domaine `SID`.|
|SidTypeAlias|Indique un alias `SID`.|
|SidTypeWellKnownGroup|Indique un `SID` pour un groupe bien connu.|
|SidTypeDeletedAccount|Indique un `SID` pour un compte supprimé.|
|SidTypeInvalid|Indique un non valide `SID`.|
|SidTypeUnknown|Indique une inconnue `SID` type.|
|SidTypeComputer|Indique un `SID` pour un ordinateur.|

### <a name="remarks"></a>Notes

Appelez [CSid::LoadAccount](#loadaccount) pour mettre à jour le `CSid` objet avant d’appeler `SidNameUse` pour retourner son état. `SidNameUse` ne modifie pas l’état de l’objet (par l’appel de `LookupAccountName` ou `LookupAccountSid`), mais retourne uniquement l’état actuel.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)<br/>
[Opérateurs](../../atl/reference/atl-operators.md)
