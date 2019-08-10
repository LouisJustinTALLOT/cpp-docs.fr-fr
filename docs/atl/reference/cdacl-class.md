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
ms.openlocfilehash: 2bc962407bac947f475368b43f5039bca3c1da1e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915812"
---
# <a name="cdacl-class"></a>CDacl, classe

Cette classe est un wrapper pour une structure DACL (liste de contrôle d’accès discrétionnaire).

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CDacl::AddAllowedAce](#addallowedace)|Ajoute une entrée du contrôle d’accès (ACE) autorisée à `CDacl` l’objet.|
|[CDacl::AddDeniedAce](#adddeniedace)|Ajoute une entrée du contrôle d' `CDacl` accès refusée à l’objet.|
|[CDacl::GetAceCount](#getacecount)|Retourne le nombre d’entrées du contrôle d’accès (ACE) dans `CDacl` l’objet.|
|[CDacl::RemoveAce](#removeace)|Supprime une entrée du contrôle d’accès spécifique de l' `CDacl` objet.|
|[CDacl::RemoveAllAces](#removeallaces)|Supprime toutes les ACE contenues dans l' `CDacl` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDacl:: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Le descripteur de sécurité d’un objet peut contenir une liste DACL. Une liste DACL contient zéro, une ou plusieurs entrées de contrôle d’accès (ACE) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Si une liste DACL est vide (autrement dit, elle ne contient aucune ACE), aucun accès n’est accordé explicitement, de sorte que l’accès est refusé implicitement. Toutefois, si le descripteur de sécurité d’un objet n’a pas de liste DACL, l’objet n’est pas protégé et tout le monde dispose d’un accès complet.

Pour récupérer la liste DACL d’un objet, vous devez être le propriétaire de l’objet ou avoir un accès READ_CONTROL à l’objet. Pour modifier la liste DACL d’un objet, vous devez avoir un accès WRITE_DAC à l’objet.

Utilisez les méthodes de classe fournies pour créer, ajouter, supprimer et supprimer des ACE de `CDacl` l’objet. Voir aussi [AtlGetDacl](security-global-functions.md#atlgetdacl) et [AtlSetDacl](security-global-functions.md#atlsetdacl).

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Configuration requise

**En-tête:** ATLSecurity. h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Ajoute une entrée du contrôle d’accès (ACE) autorisée à `CDacl` l’objet.

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
Objet [CSID](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Spécifie le masque de droits d’accès à autoriser pour l' `CSid` objet spécifié.

*AceFlags*<br/>
Jeu d’indicateurs de bits qui contrôlent l’héritage de l’entrée du contrôle d’accès.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’entrée du contrôle `CDacl` d’accès est ajoutée à l’objet, false en cas d’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro, une ou plusieurs entrées de contrôle d’accès (ACE, Access Control Entry) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Cette méthode ajoute une entrée du contrôle d’accès qui `CDacl` autorise l’accès à l’objet.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) pour obtenir une description des différents indicateurs qui peuvent être définis dans le `AceFlags` paramètre.

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

Ajoute une entrée de contrôle d’accès (ACE) refusée `CDacl` à l’objet.

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
Spécifie le masque de droits d’accès à refuser pour l' `CSid` objet spécifié.

*AceFlags*<br/>
Jeu d’indicateurs de bits qui contrôlent l’héritage de l’entrée du contrôle d’accès. La valeur par défaut est 0 dans la première forme de la méthode.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’entrée du contrôle `CDacl` d’accès est ajoutée à l’objet, false en cas d’échec.

### <a name="remarks"></a>Notes

Un `CDacl` objet contient zéro, une ou plusieurs entrées de contrôle d’accès (ACE, Access Control Entry) qui identifient les utilisateurs et les groupes qui peuvent accéder à l’objet. Cette méthode ajoute une entrée du contrôle d’accès qui refuse `CDacl` l’accès à l’objet.

Consultez [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-ace_header) pour obtenir une description des différents indicateurs qui peuvent être définis dans le `AceFlags` paramètre.

##  <a name="cdacl"></a>  CDacl::CDacl

Constructeur.

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Structure existante `ACL` (liste de contrôle d’accès).

### <a name="remarks"></a>Notes

L' `CDacl` objet peut éventuellement être créé à l’aide d' `ACL` une structure existante. Il est important de noter que seule une liste DACL (liste de contrôle d’accès discrétionnaire), et non une liste de contrôle d’accès système (SACL), doit être transmise en tant que paramètre. Dans les versions Debug, le passage d’une liste SACL entraîne une assertion. Dans les versions release, le passage d’une liste SACL entraîne l’ignorance des ACE (entrées de contrôle d’accès) dans la liste de contrôle d’accès et aucune erreur n’est générée.

##  <a name="dtor"></a>  CDacl::~CDacl

Destructeur.

```
~CDacl () throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet, y compris toutes les entrées de contrôle d’accès (ACE) à l’aide de [CDacl:: RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>  CDacl::GetAceCount

Retourne le nombre d’entrées du contrôle d’accès (ACE) dans `CDacl` l’objet.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées du même du `CDacl` contenu dans l’objet.

##  <a name="operator_eq"></a>  CDacl::operator =

Opérateur d'assignation.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Liste de contrôle d’accès (ACL) à assigner à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’objet `CDacl` mis à jour.

### <a name="remarks"></a>Notes

Vous devez vous assurer de ne transmettre qu’une liste DACL (liste de contrôle d’accès discrétionnaire) à cette fonction. Le passage d’une liste de contrôle d’accès système (SACL) à cette fonction provoque une assertion dans les versions Debug, mais n’entraîne aucune erreur dans les versions release.

##  <a name="removeace"></a>  CDacl::RemoveAce

Supprime une entrée du contrôle d’accès spécifique de l' `CDacl` objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::](../../atl/reference/catlarray-class.md#removeat)RemoveAt.

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

Supprime toutes les entrées du contrôle d’accès contenues dans l' `CDacl` objet.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Notes

Supprime chaque `ACE` structure (d’entrée de contrôle d’accès) (le cas échéant `CDacl` ) de l’objet.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[CAcl, classe](../../atl/reference/cacl-class.md)<br/>
[LCA](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[Roi](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
