---
title: Classe CDacl
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
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327148"
---
# <a name="cdacl-class"></a>Classe CDacl

Cette classe est un emballage pour une structure DACL (liste discrétionnaire d’accès-contrôle).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDacl : public CAcl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Constructeur.|
|[CDacl: : CDacl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Ajoute un ACE autorisé (entrée de `CDacl` contrôle d’accès) à l’objet.|
|[CDacl::AddDeniedAce](#adddeniedace)|Ajoute un ACE refusé `CDacl` à l’objet.|
|[CDacl::GetAceCount](#getacecount)|Retourne le nombre d’ACE (entrées de `CDacl` contrôle d’accès) dans l’objet.|
|[CDacl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de `CDacl` contrôle d’accès) de l’objet.|
|[CDacl::RemoveAllAces](#removeallaces)|Supprime toutes les AE contenues dans l’objet. `CDacl`|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDacl::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Le descripteur de sécurité d’un objet peut contenir un DACL. Un DACL contient zéro ou plusieurs AE (entrées de contrôle d’accès) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Si un DACL est vide (c’est-à-dire qu’il contient zéro ACE), aucun accès n’est explicitement accordé, de sorte que l’accès est implicitement refusé. Toutefois, si le descripteur de sécurité d’un objet n’a pas de DACL, l’objet n’est pas protégé et tout le monde a un accès complet.

Pour récupérer le DACL d’un objet, vous devez être le propriétaire de l’objet ou avoir READ_CONTROL accès à l’objet. Pour modifier le DACL d’un objet, vous devez avoir WRITE_DAC accès à l’objet.

Utilisez les méthodes de classe fournies pour créer, ajouter, supprimer et supprimer les ACE de l’objet. `CDacl` Voir aussi [AtlGetDacl](security-global-functions.md#atlgetdacl) et [AtlSetDacl](security-global-functions.md#atlsetdacl).

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[Acic](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce

Ajoute un ACE autorisé (entrée de `CDacl` contrôle d’accès) à l’objet.

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
Un objet [CSid.](../../atl/reference/csid-class.md)

*AccessMask (en)*<br/>
Spécifie le masque des droits `CSid` d’accès à permettre à l’objet spécifié.

*AceFlags (AceFlags)*<br/>
Un ensemble de drapeaux bits qui contrôlent l’héritage ACE.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’ACE `CDacl` est ajouté à l’objet, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro ou plusieurs AE (entrées de contrôle d’accès) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE `CDacl` qui permet l’accès à l’objet.

Voir [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour une description des différents drapeaux qui `AceFlags` peuvent être définis dans le paramètre.

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce

Ajoute un ACE refusé (entrée de `CDacl` contrôle d’accès) à l’objet.

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
Objet `CSid` .

*AccessMask (en)*<br/>
Spécifie le masque des droits d’accès à refuser pour l’objet spécifié. `CSid`

*AceFlags (AceFlags)*<br/>
Un ensemble de drapeaux bits qui contrôlent l’héritage ACE. Par défaut à 0 dans la première forme de la méthode.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’ACE `CDacl` est ajouté à l’objet, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro ou plusieurs AE (entrées de contrôle d’accès) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Cette méthode ajoute un ACE `CDacl` qui refuse l’accès à l’objet.

Voir [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour une description des différents drapeaux qui `AceFlags` peuvent être définis dans le paramètre.

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl

Constructeur.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Une `ACL` structure existante (liste d’accès).

### <a name="remarks"></a>Notes

L’objet `CDacl` peut être créé `ACL` en option à l’aide d’une structure existante. Il est important de noter que seul un DACL (liste discrétionnaire de contrôle d’accès), et non une SACL (liste de contrôle d’accès du système), devrait être adopté comme ce paramètre. Dans les constructions de débogé, l’adoption d’un SACL provoquera un ASSERT. Dans les versions, l’adoption d’un SACL fera en sorte que les ACE (entrées de contrôle d’accès) dans le LCA seront ignorés, et aucune erreur ne se produira.

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl: : CDacl

Destructeur.

```
~CDacl () throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet, y compris toutes les AE (entrées de contrôle d’accès) à l’aide [de CDacl::RemoveAllAces](#removeallaces).

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount

Retourne le nombre d’ACE (entrées de `CDacl` contrôle d’accès) dans l’objet.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’ACE `CDacl` contenus dans l’objet.

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::opérateur

Opérateur d'assignation.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
L’ACL (liste de contrôle d’accès) à attribuer à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CDacl` à l’objet mis à jour.

### <a name="remarks"></a>Notes

Vous devez vous assurer que vous ne passez qu’une DACL (liste discrétionnaire de contrôle d’accès) à cette fonction. L’adoption d’un SACL (liste de contrôle d’accès système) à cette fonction provoquera un ASSERT dans les constructions de débopathie, mais ne causera aucune erreur dans les versions.

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce

Supprime un ACE spécifique (entrée de `CDacl` contrôle d’accès) de l’objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::RemoveAllAces

Supprime toutes les AE (entrées de contrôle `CDacl` d’accès) contenues dans l’objet.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Notes

Supprime chaque `ACE` structure (entrée de contrôle d’accès) (le cas échéant) dans l’objet. `CDacl`

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[Classe CAcl](../../atl/reference/cacl-class.md)<br/>
[listes de contrôle d'accès](/windows/win32/SecAuthZ/access-control-lists)<br/>
[As](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
