---
title: CDacl, classe
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 1beac6106b825c775012b85ccd01226c3dfab795
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770017"
---
# <a name="cdacl-class"></a>CDacl, classe

Cette classe est un wrapper pour une structure DACL (liste de contrôle d’accès discrétionnaire).

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDacl : public CAcl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Constructeur.|
|[CDacl::~CDacl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Ajoute un ACE autorisé (entrée de contrôle d’accès) à la `CDacl` objet.|
|[CDacl::AddDeniedAce](#adddeniedace)|Ajoute un ACE de refus à le `CDacl` objet.|
|[CDacl::GetAceCount](#getacecount)|Retourne le nombre d’entrées ACE (entrées de contrôle d’accès) dans le `CDacl` objet.|
|[CDacl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CDacl` objet.|
|[CDacl::RemoveAllAces](#removeallaces)|Supprime tous les ACE contenues dans le `CDacl` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Descripteur de sécurité d’un objet peut contenir une liste DACL. Une liste DACL contient zéro ou plusieurs entrées ACE (entrées de contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Si une liste DACL est vide (autrement dit, elle contient zéro ACE), aucun accès n’est accordé explicitement, donc l’accès est refusé implicitement. Toutefois, si le descripteur de sécurité d’un objet ne dispose pas d’une liste DACL, l’objet n’est pas protégé, et tout le monde a un accès complet.

Pour récupérer la liste DACL d’un objet, vous devez être propriétaire de l’objet ou avoir accès READ_CONTROL à l’objet. Pour modifier la liste DACL d’un objet, vous devez disposer de l’accès WRITE_DAC à l’objet.

Utilisez les méthodes de classe fournis pour créer, ajouter, supprimer et supprimer des entrées à partir de la `CDacl` objet. Voir aussi [AtlGetDacl](security-global-functions.md#atlgetdacl) et [AtlSetDacl](security-global-functions.md#atlsetdacl).

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Ajoute un ACE autorisé (entrée de contrôle d’accès) à la `CDacl` objet.

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Un [CSid](../../atl/reference/csid-class.md) objet.

*AccessMask*<br/>
Spécifie le masque de droits d’accès à autoriser pour le texte spécifié `CSid` objet.

*AceFlags*<br/>
Un ensemble de bits indicateurs qui contrôlent l’héritage des ACE.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’entrée du contrôle est ajouté à la `CDacl` de l’objet, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro ou plusieurs entrées ACE (entrées de contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE qui autorise l’accès à la `CDacl` objet.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) pour obtenir une description des indicateurs différents qui peuvent être définies dans le `AceFlags` paramètre.

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

Ajoute un ACE de refus (entrée de contrôle d’accès) à la `CDacl` objet.

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet `CSid`.

*AccessMask*<br/>
Spécifie le masque de droits d’accès doit être refusé pour spécifié `CSid` objet.

*AceFlags*<br/>
Un ensemble de bits indicateurs qui contrôlent l’héritage des ACE. La valeur par défaut est 0 dans la première forme de la méthode.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’entrée du contrôle est ajouté à la `CDacl` de l’objet, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro ou plusieurs entrées ACE (entrées de contrôle d’accès) qui identifient les utilisateurs et groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE qui refuse l’accès à la `CDacl` objet.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) pour obtenir une description des indicateurs différents qui peuvent être définies dans le `AceFlags` paramètre.

##  <a name="cdacl"></a>  CDacl::CDacl

Constructeur.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Un existant `ACL` structure (liste de contrôle d’accès).

### <a name="remarks"></a>Notes

Le `CDacl` objet peut être éventuellement créé à l’aide d’un existant `ACL` structure. Il est important de noter que seul un DACL (liste de contrôle d’accès discrétionnaire), et pas une liste SACL (liste de contrôle d’accès système), doit être passé comme paramètre. Dans les versions debug, en passant une liste SACL entraîne une assertion. Dans les versions release, en passant une liste SACL entraîne l’ACE (entrées de contrôle d’accès) dans la liste ACL doivent être ignorés, et aucune erreur ne se produira.

##  <a name="dtor"></a>  CDacl::~CDacl

Destructeur.

```
~CDacl () throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère les ressources acquises par l’objet, y compris tous les ACE (entrées de contrôle d’accès) à l’aide de [CDacl::RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>  CDacl::GetAceCount

Retourne le nombre d’entrées ACE (entrées de contrôle d’accès) dans le `CDacl` objet.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées ACE contenues dans le `CDacl` objet.

##  <a name="operator_eq"></a>  CDacl::operator =

Opérateur d'assignation.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
La liste ACL (liste de contrôle d’accès) pour affecter à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la mise à jour `CDacl` objet.

### <a name="remarks"></a>Notes

Vous devez vous assurer que vous passez une liste DACL (liste de contrôle d’accès discrétionnaire) uniquement à cette fonction. En passant une liste SACL (liste de contrôle d’accès système) à cette fonction provoque une assertion dans les versions debug mais ne génère aucune erreur dans les versions release.

##  <a name="removeace"></a>  CDacl::RemoveAce

Supprime un ACE spécifique (entrée de contrôle d’accès) de la `CDacl` objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

Supprime tous les ACE (entrées de contrôle d’accès) contenues dans le `CDacl` objet.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Notes

Supprime chaque `ACE` structure (entrée de contrôle d’accès) (le cas échéant) dans le `CDacl` objet.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[CAcl, classe](../../atl/reference/cacl-class.md)<br/>
[ACL](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
