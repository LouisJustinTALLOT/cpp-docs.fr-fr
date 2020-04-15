---
title: Classe CSacl
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
ms.openlocfilehash: 72b5c9fee3868286f9e4a0917f46aeb732349c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330994"
---
# <a name="csacl-class"></a>Classe CSacl

Cette classe est un emballage pour une structure SACL (liste d’accès système).

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
|[CSacl: :CSacl](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Ajoute une entrée de contrôle d’accès audit (ACE) à l’objet. `CSacl`|
|[CSacl::GetAceCount](#getacecount)|Retourne le nombre d’entrées de contrôle `CSacl` d’accès dans l’objet.|
|[CSacl::RemoveAce](#removeace)|Supprime un ACE spécifique (entrée de `CSacl` contrôle d’accès) de l’objet.|
|[CSacl::RemoveAllAces](#removeallaces)|Supprime toutes les AE contenues dans l’objet. `CSacl`|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSacl::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Une SACL contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité d’un contrôleur de domaine. Notez qu’un SACL génère des entrées de journal uniquement sur le contrôleur de domaine où la tentative d’accès s’est produite, pas sur tous les contrôleurs de domaine qui contient une réplique de l’objet.

Pour définir ou récupérer le SACL dans le descripteur de sécurité d’un objet, le privilège SE_SECURITY_NAME doit être activé dans le signe d’accès du thread demandé. Le groupe d’administrateurs a ce privilège accordé par défaut, et il peut être accordé à d’autres utilisateurs ou groupes. Le privilège accordé n’est pas tout ce qu’il faut : avant que l’opération définie par le privilège puisse être exécutée, le privilège doit être activé dans le jeton d’accès à la sécurité afin d’entrer en vigueur. Le modèle permet de ne pas activer les privilèges uniquement pour des opérations spécifiques du système, puis désactivés lorsqu’ils ne sont plus nécessaires. Voir [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl) pour des exemples d’SE_SECURITY_NAME habilitant.

Utilisez les méthodes de classe fournies pour ajouter, supprimer, créer et supprimer les ACE de l’objet. `SACL` Voir aussi [AtlGetSacl](security-global-functions.md#atlgetsacl) et [AtlSetSacl](security-global-functions.md#atlsetsacl).

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[Acic](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce

Ajoute une entrée de contrôle d’accès audit (ACE) à l’objet. `CSacl`

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
[L’objet CSid.](../../atl/reference/csid-class.md)

*AccessMask (en)*<br/>
Spécifie le masque des droits d’accès à auditer pour l’objet spécifié. `CSid`

*bSuccess*<br/>
Précise si les tentatives d’accès autorisées doivent être vérifiées. Définissez ce drapeau pour permettre l’audit; autrement, mettez-le à faux.

*bFailure (en)*<br/>
Précise si les tentatives d’accès refusées doivent être vérifiées. Définissez ce drapeau pour permettre l’audit; autrement, mettez-le à faux.

*AceFlags (AceFlags)*<br/>
Un ensemble de drapeaux bits qui contrôlent l’héritage ACE.

*pObjectType*<br/>
Type d'objet.

*pInheritedObjectType*<br/>
Le type d’objet hérité.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’ACE `CSacl` est ajouté à l’objet, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Un `CSacl` objet contient des entrées de contrôle d’accès (ACE) qui spécifient les types de tentatives d’accès qui génèrent des enregistrements d’audit dans le journal des événements de sécurité. Cette méthode ajoute un `CSacl` tel ACE à l’objet.

Voir [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) pour une description des différents drapeaux qui peuvent être placés dans le paramètre *AceFlags.*

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl

Constructeur.

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Une `ACL` structure existante (liste d’accès).

### <a name="remarks"></a>Notes

L’objet `CSacl` peut être créé `ACL` en option à l’aide d’une structure existante. Assurez-vous qu’il s’agit d’une liste de contrôle d’accès système (SACL) et non d’une liste discrétionnaire de contrôle de l’accès (DACL). Dans les constructions de débog, si un DACL est fourni une affirmation se produira. Dans la version construit toutes les entrées d’un DACL sont ignorés.

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl: :CSacl

Destructeur.

```
~CSacl() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources acquises par l’objet, y compris toutes les entrées de contrôle d’accès (ACE).

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount

Retourne le nombre d’entrées de contrôle `CSacl` d’accès dans l’objet.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’ACE `CSacl` contenus dans l’objet.

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::opérateur

Opérateur d'assignation.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
La `ACL` (liste d’accès-contrôle) à attribuer à l’objet existant.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CSacl` à l’objet mis à jour. Assurez-vous `ACL` que le paramètre est en fait une liste de contrôle d’accès système (SACL) et non une liste discrétionnaire de contrôle d’accès (DACL). Dans debug construit une affirmation se produira, `ACL` et dans la version construit le paramètre sera ignoré.

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::RemoveAce

Supprime un ACE spécifique (entrée de `CSacl` contrôle d’accès) de l’objet.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index à l’entrée ACE à supprimer.

### <a name="remarks"></a>Notes

Cette méthode est dérivée de [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::RemoveAllAces

Supprime toutes les entrées de contrôle d’accès `CSacl` (ACE) contenues dans l’objet.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Notes

Supprime chaque `ACE` structure (le cas `CSacl` échéant) dans l’objet.

## <a name="see-also"></a>Voir aussi

[Classe CAcl](../../atl/reference/cacl-class.md)<br/>
[listes de contrôle d'accès](/windows/win32/SecAuthZ/access-control-lists)<br/>
[As](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
