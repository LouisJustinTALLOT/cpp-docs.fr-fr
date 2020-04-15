---
title: Classe CSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 926e4e0a795982479188d90ed866bf5e2584c187
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330968"
---
# <a name="csecuritydesc-class"></a>Classe CSecurityDesc

Cette classe est un `SECURITY_DESCRIPTOR` emballage pour la structure.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityDesc
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|Constructeur.|
|[CSecurityDesc::CSecurityDesc](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSecurityDesc::DeString](#fromstring)|Convertit un descripteur de sécurité de format de chaîne en un descripteur de sécurité fonctionnel valide.|
|[CSecurityDesc::GetControl](#getcontrol)|Récupère les informations de contrôle du descripteur de sécurité.|
|[CSecurityDesc::GetDacl](#getdacl)|Récupère les informations discrétionnaires de la liste d’accès-contrôle (DACL) du descripteur de sécurité.|
|[CSecurityDesc::GetGroup](#getgroup)|Récupère les informations du groupe principal du descripteur de sécurité.|
|[CSecurityDesc::GetOwner](#getowner)|Récupère l’informaton propriétaire du descripteur de sécurité.|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Retourne un pointeur à la `SECURITY_DESCRIPTOR` structure.|
|[CSecurityDesc::GetSacl](#getsacl)|Récupère les informations de la liste d’accès au système (SACL) du descripteur de sécurité.|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|Détermine si le DACL est configuré pour prendre en charge la propagation automatique.|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|Détermine si le descripteur de sécurité est configuré avec un DACL par défaut.|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|Détermine si le descripteur de sécurité contient un DACL.|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|Détermine si le DACL est configuré pour empêcher les modifications.|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|Détermine si l’identifiant de sécurité du descripteur de sécurité (SID) a été défini par défaut.|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|Détermine si le propriétaire du descripteur de sécurité SID a été défini par défaut.|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|Détermine si le SACL est configuré pour prendre en charge la propagation automatique.|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|Détermine si le descripteur de sécurité est configuré avec un SACL par défaut.|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|Détermine si le descripteur de sécurité contient un SACL.|
|[CSecurityDesc::IsSaclProté](#issaclprotected)|Détermine si le SACL est configuré pour éviter les modifications.|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|Détermine si le descripteur de sécurité est en format auto-relatif.|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|Appelez cette méthode pour convertir le descripteur de sécurité en format absolu.|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|Appelez cette méthode pour convertir le descripteur de sécurité en format auto-relatif.|
|[CSecurityDesc::SetControl](#setcontrol)|Définit les bits de contrôle d'un descripteur de sécurité.|
|[CSecurityDesc::SetDacl](#setdacl)|Définit les informations dans un DACL. Si un DACL est déjà présent dans le descripteur de sécurité, il est remplacé.|
|[CSecurityDesc::SetGroup](#setgroup)|Définit les informations de groupe primaires d’un descripteur de sécurité de format absolu, remplaçant toute information de groupe primaire déjà présente.|
|[CSecurityDesc::SetOwner](#setowner)|Définit les informations du propriétaire d’un descripteur de sécurité de format absolu, remplaçant toute information du propriétaire déjà présente.|
|[CSecurityDesc::SetSacl](#setsacl)|Définit l’information dans un SACL. Si un SACL est déjà présent dans le descripteur de sécurité, il est remplacé.|
|[CSecurityDesc::ToString](#tostring)|Convertit un descripteur de sécurité en format de chaîne.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSecurityDesc::l’opérateur const SECURITY_DESCRIPTOR](#operator_const_security_descriptor__star)|Retourne un pointeur à la `SECURITY_DESCRIPTOR` structure.|
|[CSecurityDesc::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

La `SECURITY_DESCRIPTOR` structure contient les informations de sécurité associées à un objet. Les applications utilisent cette structure pour définir et interroger l’état de sécurité d’un objet. Voir aussi [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Les applications ne `SECURITY_DESCRIPTOR` doivent pas modifier la structure directement, et devraient plutôt utiliser les méthodes de classe fournies.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a>CSecurityDesc::CSecurityDesc

Constructeur.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CSecurityDesc` L’objet `SECURITY_DESCRIPTOR` ou la structure `CSecurityDesc` à attribuer au nouvel objet.

### <a name="remarks"></a>Notes

L’objet `CSecurityDesc` peut être créé `SECURITY_DESCRIPTOR` en option `CSecurityDesc` à l’aide d’une structure ou d’un objet précédemment défini.

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a>CSecurityDesc::CSecurityDesc

Destructeur.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a>CSecurityDesc::DeString

Convertit un descripteur de sécurité de format de chaîne en un descripteur de sécurité fonctionnel valide.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne désilisée qui contient le [descripteur de sécurité de format de chaîne](/windows/win32/SecAuthZ/security-descriptor-string-format) à convertir.

### <a name="return-value"></a>Valeur de retour

Les retours sont vrais sur le succès. Jette une exception sur l’échec.

### <a name="remarks"></a>Notes

La chaîne peut être créée en utilisant [CSecurityDesc::ToString](#tostring). La conversion du descripteur de sécurité en chaîne facilite le stockage et la transmission.

Cette méthode appelle [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a>CSecurityDesc::GetControl

Récupère les informations de contrôle du descripteur de sécurité.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Paramètres

*psdc*<br/>
Pointeur `SECURITY_DESCRIPTOR_CONTROL` vers une structure qui reçoit les informations de contrôle du descripteur de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la méthode réussit, fausse si elle échoue.

### <a name="remarks"></a>Notes

Cette méthode appelle [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a>CSecurityDesc::GetDacl

Récupère les informations discrétionnaires de la liste d’accès-contrôle (DACL) du descripteur de sécurité.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDacl (en)*<br/>
Pointeur `CDacl` vers une structure dans laquelle stocker une copie du DACL du descripteur de sécurité. S’il existe un LCA discrétionnaire, la méthode fixe *pDacl* à l’adresse de l’ACL discrétionnaire du descripteur de sécurité. Si un ACL discrétionnaire n’existe pas, aucune valeur n’est stockée.

*pbPrésent*<br/>
Pointeur à une valeur qui indique la présence d’un ACL discrétionnaire dans le descripteur de sécurité spécifié. Si le descripteur de sécurité contient un LCA discrétionnaire, ce paramètre est concrétisateur. Si le descripteur de sécurité ne contient pas de LCA discrétionnaire, ce paramètre est mis à faux.

*pbDefaulted*<br/>
Pointeur d’un drapeau fixé à la valeur `SECURITY_DESCRIPTOR_CONTROL` du drapeau SE_DACL_DEFAULTED dans la structure si un ACL discrétionnaire existe pour le descripteur de sécurité. Si ce drapeau est vrai, le LCA discrétionnaire a été récupéré par un mécanisme par défaut; si elle est fausse, l’ACL discrétionnaire a été explicitement spécifiée par un utilisateur.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la méthode réussit, fausse si elle échoue.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a>CSecurityDesc::GetGroup

Récupère les informations du groupe principal du descripteur de sécurité.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid](../../atl/reference/csid-class.md) (identifiant de sécurité) qui reçoit une copie du groupe stocké dans le CDacl.

*pbDefaulted*<br/>
Pointeur vers un drapeau réglé à la valeur `SECURITY_DESCRIPTOR_CONTROL` du drapeau SE_GROUP_DEFAULTED dans la structure lorsque la méthode revient.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la méthode réussit, fausse si elle échoue.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a>CSecurityDesc::GetOwner

Récupère l’informaton propriétaire du descripteur de sécurité.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSid](../../atl/reference/csid-class.md) (identifiant de sécurité) qui reçoit une copie du groupe stocké dans le CDacl.

*pbDefaulted*<br/>
Pointeur vers un drapeau réglé à la valeur `SECURITY_DESCRIPTOR_CONTROL` du drapeau SE_OWNER_DEFAULTED dans la structure lorsque la méthode revient.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la méthode réussit, fausse si elle échoue.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a>CSecurityDesc::GetPSECURITY_DESCRIPTOR

Retourne un pointeur à la `SECURITY_DESCRIPTOR` structure.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la structure [SECURITY_DESCRIPTOR.](/windows/win32/api/winnt/ns-winnt-security_descriptor)

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a>CSecurityDesc::GetSacl

Récupère les informations de la liste d’accès au système (SACL) du descripteur de sécurité.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSacl (en)*<br/>
Pointeur `CSacl` vers une structure dans laquelle stocker une copie de la SACL du descripteur de sécurité. Si un système ACL existe, la méthode définit *pSacl* à l’adresse du système descripteur de sécurité ACL. Si un système ACL n’existe pas, aucune valeur n’est stockée.

*pbPrésent*<br/>
Pointeur à un indicateur de la méthode définit pour indiquer la présence d’un système ACL dans le descripteur de sécurité spécifié. Si le descripteur de sécurité contient un système ACL, ce paramètre est défini pour être vrai. Si le descripteur de sécurité ne contient pas de système ACL, ce paramètre est mis à faux.

*pbDefaulted*<br/>
Pointeur à un drapeau réglé à la valeur `SECURITY_DESCRIPTOR_CONTROL` du drapeau SE_SACL_DEFAULTED dans la structure si un système ACL existe pour le descripteur de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la méthode réussit, fausse si elle échoue.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a>CSecurityDesc::IsDaclAutoInherited

Détermine si la liste discrétionnaire de contrôle d’accès (DACL) est configurée pour prendre en charge la propagation automatique.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un DACL qui est mis en place pour soutenir la propagation automatique des entrées héréditaires de contrôle d’accès (ACE) aux objets existants pour enfants. Sinon, retourne False.

### <a name="remarks"></a>Notes

Le système définit ce bit quand il exécute l’algorithme d’héritage automatique pour l’objet et ses objets enfant existants.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a>CSecurityDesc::IsDaclDefaulted

Détermine si le descripteur de sécurité est configuré avec une liste discrétionnaire de contrôle d’accès par défaut (DACL).

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un DACL par défaut, faux autrement.

### <a name="remarks"></a>Notes

Ce drapeau peut affecter la façon dont le système traite le DACL, en ce qui concerne l’héritage d’entrée de contrôle d’accès (ACE). Par exemple, si le créateur d’un objet ne spécifie pas un DACL, l’objet reçoit le DACL par défaut du jeton d’accès du créateur. Le système ignore ce drapeau si le drapeau SE_DACL_PRESENT n’est pas fixé.

Ce drapeau est utilisé pour déterminer comment le DACL final sur l’objet doit être calculé et n’est pas stocké physiquement dans le contrôle descripteur de sécurité de l’objet titrable.

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetDacl.](#setdacl)

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a>CSecurityDesc::IsDaclPresent

Détermine si le descripteur de sécurité contient une liste discrétionnaire de contrôle d’accès (DACL).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un DACL, faux autrement.

### <a name="remarks"></a>Notes

Si ce drapeau n’est pas défini, ou si ce drapeau est défini et que le DACL est NULL, le descripteur de sécurité permet un accès complet à tout le monde.

Ce drapeau est utilisé pour contenir les informations de sécurité spécifiées par un appelant jusqu’à ce que le descripteur de sécurité soit associé à un objet titrable. Une fois que le descripteur de sécurité est associé à un objet titrable, le drapeau SE_DACL_PRESENT est toujours placé dans le contrôle du descripteur de sécurité.

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetDacl.](#setdacl)

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a>CSecurityDesc::IsDaclProtected

Détermine si la liste discrétionnaire de contrôle d’accès (DACL) est configurée pour prévenir les modifications.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le DACL est configuré pour empêcher le descripteur de sécurité d’être modifié par des entrées héréditaires de contrôle d’accès (ACE). Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetDacl.](#setdacl)

Cette méthode prend en charge la propagation automatique des ACI héréditaires.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a>CSecurityDesc::IsGroupDefaulted

Détermine si l’identifiant de sécurité du descripteur de sécurité (SID) a été défini par défaut.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Les rendements sont vrais si un mécanisme par défaut, plutôt que le fournisseur initial du descripteur de sécurité, a fourni le groupe sid du descripteur de sécurité. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetGroup.](#setgroup)

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a>CSecurityDesc::IsOwnerDefaulted

Détermine si l’identifiant de sécurité propriétaire du descripteur de sécurité (SID) a été défini par défaut.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Rendements vrais si un mécanisme par défaut, plutôt que le fournisseur original du descripteur de sécurité, a fourni le propriétaire du descripteur de sécurité SID. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetOwner.](#setowner)

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a>CSecurityDesc::IsSaclAutoInherited

Détermine si la liste de contrôle d’accès système (SACL) est configurée pour prendre en charge la propagation automatique.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un SACL qui est mis en place pour soutenir la propagation automatique des entrées héréditaires de contrôle d’accès (ACE) aux objets existants pour enfants. Sinon, retourne False.

### <a name="remarks"></a>Notes

Le système définit ce bit quand il exécute l’algorithme d’héritage automatique pour l’objet et ses objets enfant existants.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a>CSecurityDesc::IsSaclDefaulted

Détermine si le descripteur de sécurité est configuré avec une liste de contrôle d’accès par défaut du système (SACL).

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un SACL par défaut, faux autrement.

### <a name="remarks"></a>Notes

Ce drapeau peut affecter la façon dont le système traite le SACL, en ce qui concerne l’héritage d’entrée de contrôle d’accès (ACE). Le système ignore ce drapeau si le drapeau SE_SACL_PRESENT n’est pas fixé.

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetSacl.](#setsacl)

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a>CSecurityDesc::IsSaclPresent

Détermine si le descripteur de sécurité contient une liste de contrôle d’accès système (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité contient un SACL, faux autrement.

### <a name="remarks"></a>Notes

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetSacl.](#setsacl)

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a>CSecurityDesc::IsSaclProté

Détermine si la liste de contrôle d’accès système (SACL) est configurée pour éviter les modifications.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le SACL est configuré pour empêcher le descripteur de sécurité d’être modifié par des entrées de contrôle d’accès héréditaires (ACE). Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir ce drapeau, utilisez la méthode [CSecurityDesc::SetSacl.](#setsacl)

Cette méthode prend en charge la propagation automatique des ACI héréditaires.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a>CSecurityDesc::IsSelfRelative

Détermine si le descripteur de sécurité est en format auto-relatif.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le descripteur de sécurité est en format auto-relatif avec toutes les informations de sécurité dans un bloc de mémoire contigus. Retourne faux si le descripteur de sécurité est en format absolu. Pour plus d’informations, voir [Absolute and Self-Relative Security Descriptors](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a>CSecurityDesc::MakeAbsolute

Appelez cette méthode pour convertir le descripteur de sécurité en format absolu.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Valeur de retour

Revient vrai si la méthode réussit, faux sinon.

### <a name="remarks"></a>Notes

Un descripteur de sécurité en format absolu contient des indications sur les informations qu’il contient, plutôt que l’information elle-même. Un descripteur de sécurité en format auto-relatif contient les informations dans un bloc de mémoire contigus. Dans un descripteur de sécurité `SECURITY_DESCRIPTOR` auto-relatif, une structure démarre toujours l’information, mais les autres composants du descripteur de sécurité peuvent suivre la structure dans n’importe quel ordre. Au lieu d’utiliser des adresses mémoire, les composants du descripteur de sécurité auto-relatif sont identifiés par des décalages dès le début du descripteur de sécurité. Ce format est utile lorsqu’un descripteur de sécurité doit être stocké sur un disque ou transmis au moyen d’un protocole de communication. Pour plus d’informations, voir [Absolute and Self-Relative Security Descriptors](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a>CSecurityDesc::MakeSelfRelative

Appelez cette méthode pour convertir le descripteur de sécurité en format auto-relatif.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Valeur de retour

Revient vrai si la méthode réussit, faux sinon.

### <a name="remarks"></a>Notes

Un descripteur de sécurité en format absolu contient des indications sur les informations qu’il contient, plutôt que de contenir l’information elle-même. Un descripteur de sécurité en format auto-relatif contient les informations dans un bloc de mémoire contigus. Dans un descripteur de sécurité `SECURITY_DESCRIPTOR` auto-relatif, une structure démarre toujours l’information, mais les autres composants du descripteur de sécurité peuvent suivre la structure dans n’importe quel ordre. Au lieu d’utiliser des adresses mémoire, les composants du descripteur de sécurité sont identifiés par des décalages depuis le début du descripteur de sécurité. Ce format est utile lorsqu’un descripteur de sécurité doit être stocké sur un disque ou transmis au moyen d’un protocole de communication. Pour plus d’informations, voir [Absolute and Self-Relative Security Descriptors](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a>CSecurityDesc::opérateur

Opérateur d'assignation.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
La `SECURITY_DESCRIPTOR` structure `CSecurityDesc` ou l’objet à attribuer à l’objet. `CSecurityDesc`

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CSecurityDesc`

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a>CSecurityDesc::l’opérateur const SECURITY_DESCRIPTOR

Jette une valeur à un `SECURITY_DESCRIPTOR` pointeur de la structure.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a>CSecurityDesc::SetControl

Définit les bits de contrôle d'un descripteur de sécurité.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Paramètres

*ControlBitsOfInterest (en)*<br/>
Masque SECURITY_DESCRIPTOR_CONTROL qui indique les bits de contrôle à définir. Pour une liste des drapeaux qui peuvent être fixés, voir [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet (en anglais)*<br/>
Un masque SECURITY_DESCRIPTOR_CONTROL qui indique les nouvelles valeurs pour les bits de contrôle spécifiés par le masque *ControlBitsOfInterest.* Ce paramètre peut être une combinaison des drapeaux énumérés pour le paramètre *ControlBitsOfInterest.*

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a>CSecurityDesc::SetDacl

Définit l’information dans une liste discrétionnaire de contrôle d’accès (DACL). Si un DACL est déjà présent dans le descripteur de sécurité, il est remplacé.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Dacl Dacl*<br/>
Référence à `CDacl` un objet spécifiant le DACL pour le descripteur de sécurité. Ce paramètre ne doit pas être NULL. Pour définir un DACL NULL dans le descripteur de sécurité, la première forme de la méthode doit être utilisée avec *bPresent* réglé à faux.

*bPrésent*<br/>
Spécifie un drapeau indiquant la présence d’un DACL dans le descripteur de sécurité. Si ce paramètre est vrai, la méthode `SECURITY_DESCRIPTOR_CONTROL` définit le drapeau SE_DACL_PRESENT dans la structure et utilise les valeurs dans les paramètres *Dacl* et *bDefaulted.* Si elle est fausse, la méthode efface le drapeau SE_DACL_PRESENT, et *bDefaulted* est ignoré.

*bDefaulted*<br/>
Spécifie un drapeau indiquant la source du DACL. Si ce drapeau est vrai, le DACL a été récupéré par un mécanisme par défaut. En cas de faux, le DACL a été explicitement spécifié par un utilisateur. La méthode stocke cette valeur dans `SECURITY_DESCRIPTOR_CONTROL` le drapeau SE_DACL_DEFAULTED de la structure. Si ce paramètre n’est pas spécifié, le drapeau SE_DACL_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Il y a une différence importante entre un DACL vide et un DACL inexistant. Lorsqu’un DACL est vide, il ne contient aucune entrée de contrôle d’accès et aucun droit d’accès n’a été explicitement accordé. Par conséquent, l’accès à l’objet est implicitement refusé. Lorsqu’un objet n’a pas de DACL, d’autre part, aucune protection n’est assignée à l’objet, et toute demande d’accès est accordée.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a>CSecurityDesc::SetGroup

Définit les informations de groupe primaires d’un descripteur de sécurité de format absolu, remplaçant toute information de groupe primaire déjà présente.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Sid*<br/>
Référence à un objet [CSid](../../atl/reference/csid-class.md) pour le nouveau groupe principal du descripteur de sécurité. Ce paramètre ne doit pas être NULL. Un descripteur de sécurité peut être marqué comme n’ayant pas un DACL ou un SACL, mais il doit avoir un groupe et un propriétaire, même lui ce sont le SID NULL (qui est un SID intégré avec une signification particulière).

*bDefaulted*<br/>
Indique si les informations du groupe primaire provenaient d’un mécanisme par défaut. Si cette valeur est vraie, il s’agit d’informations par défaut, `SECURITY_DESCRIPTOR_CONTROL` et la méthode stocke cette valeur comme le drapeau SE_GROUP_DEFAULTED dans la structure. Si ce paramètre est nul, le drapeau SE_GROUP_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a>CSecurityDesc::SetOwner

Définit les informations du propriétaire d’un descripteur de sécurité de format absolu. Il remplace toute information de propriétaire déjà présente.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Sid*<br/>
[L’objet CSid](../../atl/reference/csid-class.md) pour le nouveau propriétaire principal du descripteur de sécurité. Ce paramètre ne doit pas être NULL.

*bDefaulted*<br/>
Indique si les informations du propriétaire proviennent d’un mécanisme par défaut. Si cette valeur est vraie, il s’agit d’informations par défaut. La méthode stocke cette valeur comme `SECURITY_DESCRIPTOR_CONTROL` le drapeau SE_OWNER_DEFAULTED dans la structure. Si ce paramètre est nul, le drapeau SE_OWNER_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a>CSecurityDesc::SetSacl

Définit l’information dans une liste de contrôle d’accès système (SACL). Si un SACL est déjà présent dans le descripteur de sécurité, il est remplacé.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Sacl*<br/>
Pointeur `CSacl` vers un objet spécifiant le SACL pour le descripteur de sécurité. Ce paramètre ne doit pas être NULL, et doit être un objet CSacl. Contrairement aux CADL, il n’y a pas de différence entre NULL et un SACL vide, car les objets SACL ne spécifient pas les droits d’accès, seulement l’information de vérification.

*bDefaulted*<br/>
Spécifie un drapeau indiquant la source de la SACL. Si ce drapeau est vrai, le SACL a été récupéré par un mécanisme par défaut. En cas de faux, le SACL a été explicitement spécifié par un utilisateur. La méthode stocke cette valeur dans le `SECURITY_DESCRIPTOR_CONTROL` drapeau SE_SACL_DEFAULTED de la structure. Si ce paramètre n’est pas spécifié, le drapeau SE_SACL_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydesctostring"></a><a name="tostring"></a>CSecurityDesc::ToString

Convertit un descripteur de sécurité en format de chaîne.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne non terminée qui recevra le [descripteur de sécurité de format de chaîne.](/windows/win32/SecAuthZ/security-descriptor-string-format)

*si*<br/>
Spécifie une combinaison de SECURITY_INFORMATION des drapeaux bits pour indiquer les composants du descripteur de sécurité à inclure dans la chaîne de sortie.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Une fois que le descripteur de sécurité est en format de chaîne, il peut plus facilement être stocké ou transmis. Utilisez `CSecurityDesc::FromString` la méthode pour convertir la chaîne en un descripteur de sécurité.

Le paramètre *si* peut contenir les indicateurs SECURITY_INFORMATION suivants :

|Value|Signification|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Inclure le propriétaire.|
|GROUP_SECURITY_INFORMATION|Inclure le groupe principal.|
|DACL_SECURITY_INFORMATION|Inclure le DACL.|
|SACL_SECURITY_INFORMATION|Inclure le SACL.|

Si le DACL est NULL et que le bit de contrôle SE_DACL_PRESENT est réglé dans le descripteur de sécurité d’entrée, la méthode échoue.

Si le DACL est NULL et que le bit de contrôle SE_DACL_PRESENT n’est pas réglé dans le descripteur de sécurité d’entrée, la chaîne descripteur de sécurité qui en résulte n’a pas de composant D : Voir [Security Descriptor String Format](/windows/win32/SecAuthZ/security-descriptor-string-format) pour plus de détails.

Cette méthode appelle [ConvertStringSecurityDescriptorToSecurityDescriptor](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
