---
description: 'En savoir plus sur : classe CSacl'
title: CSacl, classe
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: 504276d22da963b9e8ec407e88ca73d63dd71541
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140853"
---
# <a name="csacl-class"></a>CSacl, classe

Cette classe est un wrapper pour une structure SACL (liste de contrôle d’accès système).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSacl : public CAcl
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|Constructeur.|
|[CSacl :: ~ CSacl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Ajoute une entrée de contrôle d’accès (ACE, Access Control Entry) à l' `CSacl` objet.|
|[CSacl::GetAceCount](#getacecount)|Retourne le nombre d’entrées de contrôle d’accès (ACE) dans l' `CSacl` objet.|
|[CSacl::RemoveAce](#removeace)|Supprime une entrée du contrôle d’accès spécifique de l' `CSacl` objet.|
|[CSacl::RemoveAllAces](#removeallaces)|Supprime toutes les ACE contenues dans l' `CSacl` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSacl :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Une liste SACL contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité d’un contrôleur de domaine. Notez qu’une liste SACL génère des entrées de journal uniquement sur le contrôleur de domaine où la tentative d’accès a eu lieu, et non sur chaque contrôleur de domaine contenant un réplica de l’objet.

Pour définir ou récupérer la liste SACL dans le descripteur de sécurité d’un objet, le privilège de SE_SECURITY_NAME doit être activé dans le jeton d’accès du thread demandeur. Ce privilège est accordé par défaut au groupe administrateurs et il peut être accordé à d’autres utilisateurs ou groupes. Le privilège accordé n’est pas tout ce qui est nécessaire : avant que l’opération définie par le privilège puisse être effectuée, le privilège doit être activé dans le jeton d’accès de sécurité pour prendre effet. Le modèle permet d’activer des privilèges uniquement pour des opérations système spécifiques, puis de les désactiver lorsqu’ils ne sont plus nécessaires. Pour obtenir des exemples d’activation de SE_SECURITY_NAME, consultez [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl) .

Utilisez les méthodes de classe fournies pour ajouter, supprimer, créer et supprimer des ACE de l' `SACL` objet. Voir aussi [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl).

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="csacladdauditace"></a><a name="addauditace"></a> CSacl::AddAuditAce

Ajoute une entrée de contrôle d’accès (ACE, Access Control Entry) à l' `CSacl` objet.

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Spécifie le masque de droits d’accès à auditer pour l' `CSid` objet spécifié.

*bSuccess*<br/>
Spécifie si les tentatives d’accès autorisées doivent être auditées. Affectez à cet indicateur la valeur true pour activer l’audit. Sinon, affectez-lui la valeur false.

*bFailure*<br/>
Spécifie si les tentatives d’accès refusées doivent être auditées. Affectez à cet indicateur la valeur true pour activer l’audit. Sinon, affectez-lui la valeur false.

*AceFlags*<br/>
Jeu d’indicateurs de bits qui contrôlent l’héritage de l’entrée du contrôle d’accès.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Type d’objet hérité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’entrée du contrôle d’accès est ajoutée à l' `CSacl` objet, false en cas d’échec.

### <a name="remarks"></a>Notes

Un `CSacl` objet contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité. Cette méthode ajoute une telle entrée de contrôle d’accès à l' `CSacl` objet.

Consultez [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour obtenir une description des différents indicateurs qui peuvent être définis dans le paramètre *AceFlags* .

## <a name="csaclcsacl"></a><a name="csacl"></a> CSacl::CSacl

Constructeur.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Structure existante `ACL` (liste de contrôle d’accès).

### <a name="remarks"></a>Notes

L' `CSacl` objet peut éventuellement être créé à l’aide d’une `ACL` structure existante. Assurez-vous que ce paramètre est une liste de contrôle d’accès système (SACL) et non une liste de contrôle d’accès discrétionnaire (DACL). Dans les versions Debug, si une liste DACL est fournie, une assertion se produit. Dans les versions release, toutes les entrées d’une liste DACL sont ignorées.

## <a name="csaclcsacl"></a><a name="dtor"></a> CSacl :: ~ CSacl

Destructeur.

```
~CSacl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet, y compris toutes les entrées de contrôle d’accès (ACE).

## <a name="csaclgetacecount"></a><a name="getacecount"></a> CSacl::GetAceCount

Retourne le nombre d’entrées de contrôle d’accès (ACE) dans l' `CSacl` objet.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’entrées du même du contenu dans l' `CSacl` objet.

## <a name="csacloperator-"></a><a name="operator_eq"></a> CSacl :: Operator =

Opérateur d'assignation.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`ACL`(Liste de contrôle d’accès) à assigner à l’objet existant.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’objet mis à jour `CSacl` . Assurez-vous que le `ACL` paramètre est en fait une liste de contrôle d’accès système (SACL) et non une liste de contrôle d’accès discrétionnaire (DACL). Dans les versions Debug, une assertion se produira, et dans les versions release, le `ACL` paramètre sera ignoré.

## <a name="csaclremoveace"></a><a name="removeace"></a> CSacl::RemoveAce

Supprime une entrée du contrôle d’accès spécifique de l' `CSacl` objet.

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray :: RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a> CSacl::RemoveAllAces

Supprime toutes les entrées du contrôle d’accès contenues dans l' `CSacl` objet.

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Notes

Supprime chaque `ACE` structure (le cas échéant) dans l' `CSacl` objet.

## <a name="see-also"></a>Voir aussi

[CAcl, classe](../../atl/reference/cacl-class.md)<br/>
[listes de contrôle d'accès](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Roi](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
