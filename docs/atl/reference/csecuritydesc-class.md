---
description: 'En savoir plus sur : classe CSecurityDesc'
title: CSecurityDesc, classe
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
ms.openlocfilehash: 66a2229aa4819059a353baf8b3802bb1263da2e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140775"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc, classe

Cette classe est un wrapper pour la `SECURITY_DESCRIPTOR` structure.

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
|[CSecurityDesc :: CSecurityDesc](#csecuritydesc)|Constructeur.|
|[CSecurityDesc :: ~ CSecurityDesc](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSecurityDesc :: FromString](#fromstring)|Convertit un descripteur de sécurité au format chaîne en un descripteur de sécurité valide et fonctionnel.|
|[CSecurityDesc :: GetControl](#getcontrol)|Récupère les informations de contrôle du descripteur de sécurité.|
|[CSecurityDesc :: GetDacl,](#getdacl)|Récupère des informations de liste de contrôle d’accès discrétionnaire (DACL) à partir du descripteur de sécurité.|
|[CSecurityDesc :: GetGroup](#getgroup)|Récupère les informations de groupe principal à partir du descripteur de sécurité.|
|[CSecurityDesc :: GetOwner](#getowner)|Récupère les information du propriétaire à partir du descripteur de sécurité.|
|[CSecurityDesc :: GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|Retourne un pointeur vers la `SECURITY_DESCRIPTOR` structure.|
|[CSecurityDesc :: GetSacl](#getsacl)|Récupère des informations de la liste de contrôle d’accès système (SACL) à partir du descripteur de sécurité.|
|[CSecurityDesc :: IsDaclAutoInherited](#isdaclautoinherited)|Détermine si la liste DACL est configurée pour prendre en charge la propagation automatique.|
|[CSecurityDesc :: IsDaclDefaulted](#isdacldefaulted)|Détermine si le descripteur de sécurité est configuré avec une liste DACL par défaut.|
|[CSecurityDesc :: IsDaclPresent](#isdaclpresent)|Détermine si le descripteur de sécurité contient une liste DACL.|
|[CSecurityDesc :: IsDaclProtected](#isdaclprotected)|Détermine si la liste DACL est configurée pour empêcher les modifications.|
|[CSecurityDesc :: IsGroupDefaulted](#isgroupdefaulted)|Détermine si l’identificateur de sécurité (SID) de groupe du descripteur de sécurité a été défini par défaut.|
|[CSecurityDesc :: IsOwnerDefaulted](#isownerdefaulted)|Détermine si le SID du propriétaire du descripteur de sécurité a été défini par défaut.|
|[CSecurityDesc :: IsSaclAutoInherited](#issaclautoinherited)|Détermine si la liste SACL est configurée pour prendre en charge la propagation automatique.|
|[CSecurityDesc :: IsSaclDefaulted](#issacldefaulted)|Détermine si le descripteur de sécurité est configuré avec une liste SACL par défaut.|
|[CSecurityDesc :: IsSaclPresent](#issaclpresent)|Détermine si le descripteur de sécurité contient une liste SACL.|
|[CSecurityDesc :: IsSaclProtected](#issaclprotected)|Détermine si la liste SACL est configurée pour empêcher les modifications.|
|[CSecurityDesc :: IsSelfRelative](#isselfrelative)|Détermine si le descripteur de sécurité est au format auto-relatif.|
|[CSecurityDesc :: MakeAbsolute](#makeabsolute)|Appelez cette méthode pour convertir le descripteur de sécurité au format absolu.|
|[CSecurityDesc :: MakeSelfRelative](#makeselfrelative)|Appelez cette méthode pour convertir le descripteur de sécurité au format auto-relatif.|
|[CSecurityDesc :: SetControl](#setcontrol)|Définit les bits de contrôle d'un descripteur de sécurité.|
|[CSecurityDesc :: SetDacl,](#setdacl)|Définit des informations dans une liste DACL. Si une liste DACL est déjà présente dans le descripteur de sécurité, elle est remplacée.|
|[CSecurityDesc :: SetGroup](#setgroup)|Définit les informations de groupe principal d’un descripteur de sécurité de format absolu, en remplaçant toutes les informations de groupe principal déjà présentes.|
|[CSecurityDesc :: SetOwner](#setowner)|Définit les informations de propriétaire d’un descripteur de sécurité de format absolu, en remplaçant toutes les informations de propriétaire déjà présentes.|
|[CSecurityDesc :: SetSacl](#setsacl)|Définit des informations dans une liste SACL. Si une liste SACL est déjà présente dans le descripteur de sécurité, elle est remplacée.|
|[CSecurityDesc :: ToString](#tostring)|Convertit un descripteur de sécurité en un format de chaîne.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSecurityDesc :: Operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|Retourne un pointeur vers la `SECURITY_DESCRIPTOR` structure.|
|[CSecurityDesc :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

La `SECURITY_DESCRIPTOR` structure contient les informations de sécurité associées à un objet. Les applications utilisent cette structure pour définir et interroger l’état de sécurité d’un objet. Voir aussi [AtlGetSecurityDescriptor](security-global-functions.md#atlgetsecuritydescriptor).

Les applications ne doivent pas modifier la `SECURITY_DESCRIPTOR` structure directement, et doivent plutôt utiliser les méthodes de classe fournies.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="csecuritydesccsecuritydesc"></a><a name="csecuritydesc"></a> CSecurityDesc :: CSecurityDesc

Constructeur.

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CSecurityDesc`Objet ou `SECURITY_DESCRIPTOR` structure à assigner au nouvel `CSecurityDesc` objet.

### <a name="remarks"></a>Notes

L' `CSecurityDesc` objet peut éventuellement être créé à l’aide d’une `SECURITY_DESCRIPTOR` structure ou d’un objet défini précédemment `CSecurityDesc` .

## <a name="csecuritydesccsecuritydesc"></a><a name="dtor"></a> CSecurityDesc :: ~ CSecurityDesc

Destructeur.

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées.

## <a name="csecuritydescfromstring"></a><a name="fromstring"></a> CSecurityDesc :: FromString

Convertit un descripteur de sécurité au format chaîne en un descripteur de sécurité valide et fonctionnel.

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le [descripteur de sécurité au format chaîne](/windows/win32/SecAuthZ/security-descriptor-string-format) à convertir.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite. Lève une exception en cas d’échec.

### <a name="remarks"></a>Notes

La chaîne peut être créée à l’aide de [CSecurityDesc :: ToString](#tostring). La conversion du descripteur de sécurité en chaîne facilite son stockage et sa transmission.

Cette méthode appelle [convertstringsecuritydescriptortosecuritydescriptor a](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="csecuritydescgetcontrol"></a><a name="getcontrol"></a> CSecurityDesc :: GetControl

Récupère les informations de contrôle du descripteur de sécurité.

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>Paramètres

*psdc*<br/>
Pointeur vers une `SECURITY_DESCRIPTOR_CONTROL` structure qui reçoit les informations de contrôle du descripteur de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode réussit, false en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [GetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol).

## <a name="csecuritydescgetdacl"></a><a name="getdacl"></a> CSecurityDesc :: GetDacl,

Récupère des informations de liste de contrôle d’accès discrétionnaire (DACL) à partir du descripteur de sécurité.

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pDacl*<br/>
Pointeur vers une `CDacl` structure dans laquelle stocker une copie de la liste DACL du descripteur de sécurité. Si une liste de contrôle d’accès discrétionnaire existe, la méthode définit *pDacl* sur l’adresse de la liste de contrôle d’accès discrétionnaire du descripteur de sécurité. S’il n’existe pas de liste de contrôle d’accès discrétionnaire, aucune valeur n’est stockée.

*pbPresent*<br/>
Pointeur vers une valeur qui indique la présence d’une liste de contrôle d’accès discrétionnaire dans le descripteur de sécurité spécifié. Si le descripteur de sécurité contient une liste de contrôle d’accès discrétionnaire, ce paramètre a la valeur true. Si le descripteur de sécurité ne contient pas de liste de contrôle d’accès discrétionnaire, ce paramètre est défini sur false.

*pbDefaulted*<br/>
Pointeur vers un indicateur défini sur la valeur de l’indicateur SE_DACL_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure si une liste de contrôle d’accès discrétionnaire existe pour le descripteur de sécurité. Si cet indicateur a la valeur true, la liste de contrôle d’accès discrétionnaire a été récupérée par un mécanisme par défaut. Si la valeur est false, l’ACL discrétionnaire a été explicitement spécifiée par un utilisateur.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode réussit, false en cas d’échec.

## <a name="csecuritydescgetgroup"></a><a name="getgroup"></a> CSecurityDesc :: GetGroup

Récupère les informations de groupe principal à partir du descripteur de sécurité.

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSID](../../atl/reference/csid-class.md) (identificateur de sécurité) qui reçoit une copie du groupe stocké dans le CDacl.

*pbDefaulted*<br/>
Pointeur vers un indicateur défini sur la valeur de l’indicateur SE_GROUP_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure lorsque la méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode réussit, false en cas d’échec.

## <a name="csecuritydescgetowner"></a><a name="getowner"></a> CSecurityDesc :: GetOwner

Récupère les information du propriétaire à partir du descripteur de sécurité.

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSid*<br/>
Pointeur vers un [CSID](../../atl/reference/csid-class.md) (identificateur de sécurité) qui reçoit une copie du groupe stocké dans le CDacl.

*pbDefaulted*<br/>
Pointeur vers un indicateur défini sur la valeur de l’indicateur SE_OWNER_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure lorsque la méthode est retournée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode réussit, false en cas d’échec.

## <a name="csecuritydescgetpsecurity_descriptor"></a><a name="getpsecurity_descriptor"></a> CSecurityDesc :: GetPSECURITY_DESCRIPTOR

Retourne un pointeur vers la `SECURITY_DESCRIPTOR` structure.

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la structure [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) .

## <a name="csecuritydescgetsacl"></a><a name="getsacl"></a> CSecurityDesc :: GetSacl

Récupère des informations de la liste de contrôle d’accès système (SACL) à partir du descripteur de sécurité.

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pSacl*<br/>
Pointeur vers une `CSacl` structure dans laquelle stocker une copie de la liste SACL du descripteur de sécurité. Si une liste de contrôle d’accès système existe, la méthode définit *pSacl* sur l’adresse de la liste de contrôle d’accès système du descripteur de sécurité. Si aucune liste de contrôle d’accès système n’existe, aucune valeur n’est stockée.

*pbPresent*<br/>
Pointeur vers un indicateur que la méthode définit pour indiquer la présence d’une liste de contrôle d’accès système dans le descripteur de sécurité spécifié. Si le descripteur de sécurité contient une liste de contrôle d’accès système, ce paramètre est défini sur true. Si le descripteur de sécurité ne contient pas de liste de contrôle d’accès système, ce paramètre est défini sur false.

*pbDefaulted*<br/>
Pointeur vers un indicateur défini sur la valeur de l’indicateur SE_SACL_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure si une liste de contrôle d’accès système existe pour le descripteur de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode réussit, false en cas d’échec.

## <a name="csecuritydescisdaclautoinherited"></a><a name="isdaclautoinherited"></a> CSecurityDesc :: IsDaclAutoInherited

Détermine si la liste de contrôle d’accès discrétionnaire (DACL) est configurée pour prendre en charge la propagation automatique.

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une liste DACL qui est configurée pour prendre en charge la propagation automatique des entrées de contrôle d’accès (ACE) pouvant être héritées aux objets enfants existants. Sinon, retourne False.

### <a name="remarks"></a>Notes

Le système définit ce bit lorsqu’il exécute l’algorithme d’héritage automatique pour l’objet et ses objets enfants existants.

## <a name="csecuritydescisdacldefaulted"></a><a name="isdacldefaulted"></a> CSecurityDesc :: IsDaclDefaulted

Détermine si le descripteur de sécurité est configuré avec une liste de contrôle d’accès discrétionnaire (DACL) par défaut.

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une DACL par défaut ; sinon, false.

### <a name="remarks"></a>Notes

Cet indicateur peut affecter la façon dont le système traite la liste DACL, en ce qui concerne l’héritage de l’entrée de contrôle d’accès (ACE). Par exemple, si le créateur d’un objet ne spécifie pas de liste DACL, l’objet reçoit la DACL par défaut à partir du jeton d’accès du créateur. Le système ignore cet indicateur si l’indicateur SE_DACL_PRESENT n’est pas défini.

Cet indicateur est utilisé pour déterminer comment la liste DACL finale sur l’objet doit être calculée et qu’elle n’est pas stockée physiquement dans le contrôle de descripteur de sécurité de l’objet sécurisable.

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetDacl,](#setdacl) .

## <a name="csecuritydescisdaclpresent"></a><a name="isdaclpresent"></a> CSecurityDesc :: IsDaclPresent

Détermine si le descripteur de sécurité contient une liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List).

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une liste DACL, false dans le cas contraire.

### <a name="remarks"></a>Notes

Si cet indicateur n’est pas défini, ou si cet indicateur est défini et que la liste DACL est NULL, le descripteur de sécurité autorise un accès complet à tout le monde.

Cet indicateur est utilisé pour stocker les informations de sécurité spécifiées par un appelant jusqu’à ce que le descripteur de sécurité soit associé à un objet sécurisable. Une fois que le descripteur de sécurité est associé à un objet sécurisable, l’indicateur SE_DACL_PRESENT est toujours défini dans le contrôle descripteur de sécurité.

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetDacl,](#setdacl) .

## <a name="csecuritydescisdaclprotected"></a><a name="isdaclprotected"></a> CSecurityDesc :: IsDaclProtected

Détermine si la liste de contrôle d’accès discrétionnaire (DACL) est configurée pour empêcher les modifications.

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la liste DACL est configurée pour empêcher la modification du descripteur de sécurité par des entrées de contrôle d’accès (ACE) pouvant être héritées. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetDacl,](#setdacl) .

Cette méthode prend en charge la propagation automatique des ACE pouvant être héritées.

## <a name="csecuritydescisgroupdefaulted"></a><a name="isgroupdefaulted"></a> CSecurityDesc :: IsGroupDefaulted

Détermine si l’identificateur de sécurité (SID) de groupe du descripteur de sécurité a été défini par défaut.

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si un mécanisme par défaut, plutôt que le fournisseur d’origine du descripteur de sécurité, a fourni le SID du groupe du descripteur de sécurité. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetGroup](#setgroup) .

## <a name="csecuritydescisownerdefaulted"></a><a name="isownerdefaulted"></a> CSecurityDesc :: IsOwnerDefaulted

Détermine si l’identificateur de sécurité (SID) du propriétaire du descripteur de sécurité a été défini par défaut.

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si un mécanisme par défaut, plutôt que le fournisseur d’origine du descripteur de sécurité, a fourni le SID du propriétaire du descripteur de sécurité. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetOwner](#setowner) .

## <a name="csecuritydescissaclautoinherited"></a><a name="issaclautoinherited"></a> CSecurityDesc :: IsSaclAutoInherited

Détermine si la liste de contrôle d’accès système (SACL) est configurée pour prendre en charge la propagation automatique.

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une liste SACL qui est configurée pour prendre en charge la propagation automatique des entrées de contrôle d’accès (ACE) pouvant être héritées aux objets enfants existants. Sinon, retourne False.

### <a name="remarks"></a>Notes

Le système définit ce bit lorsqu’il exécute l’algorithme d’héritage automatique pour l’objet et ses objets enfants existants.

## <a name="csecuritydescissacldefaulted"></a><a name="issacldefaulted"></a> CSecurityDesc :: IsSaclDefaulted

Détermine si le descripteur de sécurité est configuré avec une liste de contrôle d’accès système (SACL) par défaut.

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une liste SACL par défaut, false dans le cas contraire.

### <a name="remarks"></a>Notes

Cet indicateur peut affecter la façon dont le système traite la liste SACL, en ce qui concerne l’héritage de l’entrée de contrôle d’accès (ACE). Le système ignore cet indicateur si l’indicateur SE_SACL_PRESENT n’est pas défini.

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetSacl](#setsacl) .

## <a name="csecuritydescissaclpresent"></a><a name="issaclpresent"></a> CSecurityDesc :: IsSaclPresent

Détermine si le descripteur de sécurité contient une liste de contrôle d’accès système (SACL).

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité contient une liste SACL, false dans le cas contraire.

### <a name="remarks"></a>Notes

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetSacl](#setsacl) .

## <a name="csecuritydescissaclprotected"></a><a name="issaclprotected"></a> CSecurityDesc :: IsSaclProtected

Détermine si la liste de contrôle d’accès système (SACL) est configurée pour empêcher les modifications.

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la liste SACL est configurée pour empêcher la modification du descripteur de sécurité par des entrées de contrôle d’accès (ACE) pouvant être héritées. Sinon, retourne False.

### <a name="remarks"></a>Notes

Pour définir cet indicateur, utilisez la méthode [CSecurityDesc :: SetSacl](#setsacl) .

Cette méthode prend en charge la propagation automatique des ACE pouvant être héritées.

## <a name="csecuritydescisselfrelative"></a><a name="isselfrelative"></a> CSecurityDesc :: IsSelfRelative

Détermine si le descripteur de sécurité est au format auto-relatif.

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le descripteur de sécurité est au format auto-relatif avec toutes les informations de sécurité dans un bloc de mémoire contigu. Retourne la valeur false si le descripteur de sécurité est au format absolu. Pour plus d’informations, consultez [descripteurs de sécurité absolus et Self-Relative](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeabsolute"></a><a name="makeabsolute"></a> CSecurityDesc :: MakeAbsolute

Appelez cette méthode pour convertir le descripteur de sécurité au format absolu.

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode est réussie ; sinon, false.

### <a name="remarks"></a>Notes

Un descripteur de sécurité au format absolu contient des pointeurs vers les informations qu’il contient, plutôt que les informations lui-même. Un descripteur de sécurité au format auto-relatif contient les informations dans un bloc de mémoire contigu. Dans un descripteur de sécurité auto-relatif, une `SECURITY_DESCRIPTOR` structure démarre toujours les informations, mais les autres composants du descripteur de sécurité peuvent suivre la structure dans n’importe quel ordre. Au lieu d’utiliser des adresses mémoire, les composants du descripteur de sécurité auto-relatif sont identifiés par des décalages à partir du début du descripteur de sécurité. Ce format est utile lorsqu’un descripteur de sécurité doit être stocké sur un disque ou transmis au moyen d’un protocole de communication. Pour plus d’informations, consultez [descripteurs de sécurité absolus et Self-Relative](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescmakeselfrelative"></a><a name="makeselfrelative"></a> CSecurityDesc :: MakeSelfRelative

Appelez cette méthode pour convertir le descripteur de sécurité au format auto-relatif.

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la méthode est réussie ; sinon, false.

### <a name="remarks"></a>Notes

Un descripteur de sécurité au format absolu contient des pointeurs vers les informations qu’il contient, au lieu de contenir les informations lui-même. Un descripteur de sécurité au format auto-relatif contient les informations dans un bloc de mémoire contigu. Dans un descripteur de sécurité auto-relatif, une `SECURITY_DESCRIPTOR` structure démarre toujours les informations, mais les autres composants du descripteur de sécurité peuvent suivre la structure dans n’importe quel ordre. Au lieu d’utiliser des adresses mémoire, les composants du descripteur de sécurité sont identifiés par des décalages à partir du début du descripteur de sécurité. Ce format est utile lorsqu’un descripteur de sécurité doit être stocké sur un disque ou transmis au moyen d’un protocole de communication. Pour plus d’informations, consultez [descripteurs de sécurité absolus et Self-Relative](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors).

## <a name="csecuritydescoperator-"></a><a name="operator_eq"></a> CSecurityDesc :: Operator =

Opérateur d'assignation.

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`SECURITY_DESCRIPTOR`Structure ou `CSecurityDesc` objet à assigner à l' `CSecurityDesc` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’objet mis à jour `CSecurityDesc` .

## <a name="csecuritydescoperator-const-security_descriptor-"></a><a name="operator_const_security_descriptor__star"></a> CSecurityDesc :: Operator const SECURITY_DESCRIPTOR *

Convertit une valeur en pointeur vers la `SECURITY_DESCRIPTOR` structure.

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

## <a name="csecuritydescsetcontrol"></a><a name="setcontrol"></a> CSecurityDesc :: SetControl

Définit les bits de contrôle d'un descripteur de sécurité.

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>Paramètres

*ControlBitsOfInterest*<br/>
Masque SECURITY_DESCRIPTOR_CONTROL qui indique les bits de contrôle à définir. Pour obtenir la liste des indicateurs qui peuvent être définis, consultez [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

*ControlBitsToSet*<br/>
Masque SECURITY_DESCRIPTOR_CONTROL qui indique les nouvelles valeurs pour les bits de contrôle spécifiés par le masque *ControlBitsOfInterest* . Ce paramètre peut être une combinaison des indicateurs listés pour le paramètre *ControlBitsOfInterest* .

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [SetSecurityDescriptorControl](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol).

## <a name="csecuritydescsetdacl"></a><a name="setdacl"></a> CSecurityDesc :: SetDacl,

Définit les informations dans une liste de contrôle d’accès discrétionnaire (DACL, Discretionary Access Control List). Si une liste DACL est déjà présente dans le descripteur de sécurité, elle est remplacée.

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*DACL*<br/>
Référence à un `CDacl` objet spécifiant la liste DACL pour le descripteur de sécurité. Ce paramètre ne doit pas avoir la valeur NULL. Pour définir une liste DACL NULL dans le descripteur de sécurité, la première forme de la méthode doit être utilisée avec *bPresent* défini sur false.

*bPresent*<br/>
Spécifie un indicateur qui spécifie la présence d’une liste DACL dans le descripteur de sécurité. Si ce paramètre a la valeur true, la méthode définit l’indicateur SE_DACL_PRESENT dans la `SECURITY_DESCRIPTOR_CONTROL` structure et utilise les valeurs des paramètres *DACL* et *bDefaulted* . Si la valeur est false, la méthode efface l’indicateur SE_DACL_PRESENT et *bDefaulted* est ignoré.

*bDefaulted*<br/>
Spécifie un indicateur qui spécifie la source de la liste DACL. Si cet indicateur a la valeur true, la liste DACL a été récupérée par un mécanisme par défaut. Si la valeur est false, la liste DACL a été explicitement spécifiée par un utilisateur. La méthode stocke cette valeur dans l’indicateur SE_DACL_DEFAULTED de la `SECURITY_DESCRIPTOR_CONTROL` structure. Si ce paramètre n’est pas spécifié, l’indicateur de SE_DACL_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Il existe une différence importante entre une liste DACL vide et une liste DACL inexistante. Quand une liste DACL est vide, elle ne contient aucune entrée de contrôle d’accès et aucun droit d’accès n’a été accordé explicitement. Par conséquent, l’accès à l’objet est refusé implicitement. En revanche, lorsqu’un objet n’a pas de liste DACL, aucune protection n’est assignée à l’objet et toute demande d’accès est accordée.

## <a name="csecuritydescsetgroup"></a><a name="setgroup"></a> CSecurityDesc :: SetGroup

Définit les informations de groupe principal d’un descripteur de sécurité de format absolu, en remplaçant toutes les informations de groupe principal déjà présentes.

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Sid*<br/>
Référence à un objet [CSID](../../atl/reference/csid-class.md) pour le nouveau groupe principal du descripteur de sécurité. Ce paramètre ne doit pas avoir la valeur NULL. Un descripteur de sécurité peut être marqué comme n’ayant pas de liste DACL ou SACL, mais il doit avoir un groupe et un propriétaire, même s’il s’agit du SID NULL (qui est un SID intégré avec une signification particulière).

*bDefaulted*<br/>
Indique si les informations de groupe principal ont été dérivées d’un mécanisme par défaut. Si cette valeur est true, il s’agit d’informations par défaut, et la méthode stocke cette valeur en tant qu’indicateur de SE_GROUP_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure. Si ce paramètre est égal à zéro, l’indicateur de SE_GROUP_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydescsetowner"></a><a name="setowner"></a> CSecurityDesc :: SetOwner

Définit les informations de propriétaire d’un descripteur de sécurité de format absolu. Il remplace toutes les informations de propriétaire déjà présentes.

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*Sid*<br/>
Objet [CSID](../../atl/reference/csid-class.md) pour le nouveau propriétaire principal du descripteur de sécurité. Ce paramètre ne doit pas avoir la valeur NULL.

*bDefaulted*<br/>
Indique si les informations de propriétaire sont dérivées d’un mécanisme par défaut. Si cette valeur est true, il s’agit des informations par défaut. La méthode stocke cette valeur en tant qu’indicateur de SE_OWNER_DEFAULTED dans la `SECURITY_DESCRIPTOR_CONTROL` structure. Si ce paramètre est égal à zéro, l’indicateur de SE_OWNER_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydescsetsacl"></a><a name="setsacl"></a> CSecurityDesc :: SetSacl

Définit les informations dans une liste de contrôle d’accès système (SACL). Si une liste SACL est déjà présente dans le descripteur de sécurité, elle est remplacée.

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*SACL*<br/>
Pointeur vers un `CSacl` objet spécifiant la liste SACL pour le descripteur de sécurité. Ce paramètre ne doit pas avoir la valeur NULL et doit être un objet CSacl. Contrairement aux DACL, il n’existe aucune différence entre la valeur NULL et une liste SACL vide, car les objets SACL ne spécifient pas de droits d’accès, mais uniquement des informations d’audit.

*bDefaulted*<br/>
Spécifie un indicateur qui spécifie la source de la liste SACL. Si cet indicateur a la valeur true, la liste SACL a été récupérée par un mécanisme par défaut. Si la valeur est false, la liste SACL a été explicitement spécifiée par un utilisateur. La méthode stocke cette valeur dans l’indicateur SE_SACL_DEFAULTED de la `SECURITY_DESCRIPTOR_CONTROL` structure. Si ce paramètre n’est pas spécifié, l’indicateur de SE_SACL_DEFAULTED est effacé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

## <a name="csecuritydesctostring"></a><a name="tostring"></a> CSecurityDesc :: ToString

Convertit un descripteur de sécurité en un format de chaîne.

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>Paramètres

*pstr*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui recevra le [descripteur de sécurité au format chaîne](/windows/win32/SecAuthZ/security-descriptor-string-format).

*si*<br/>
Spécifie une combinaison d’indicateurs de bits SECURITY_INFORMATION pour indiquer les composants du descripteur de sécurité à inclure dans la chaîne de sortie.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Une fois que le descripteur de sécurité est au format chaîne, il peut être plus facilement stocké ou transmis. Utilisez la `CSecurityDesc::FromString` méthode pour reconvertir la chaîne en descripteur de sécurité.

Le paramètre *si* peut contenir les indicateurs de SECURITY_INFORMATION suivants :

|Valeur|Signification|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|Incluez le propriétaire.|
|GROUP_SECURITY_INFORMATION|Incluez le groupe principal.|
|DACL_SECURITY_INFORMATION|Incluez la liste DACL.|
|SACL_SECURITY_INFORMATION|Incluez la liste SACL.|

Si la liste DACL est NULL et que le bit de contrôle SE_DACL_PRESENT est défini dans le descripteur de sécurité d’entrée, la méthode échoue.

Si la liste DACL est NULL et que le bit de contrôle SE_DACL_PRESENT n’est pas défini dans le descripteur de sécurité d’entrée, la chaîne du descripteur de sécurité résultant n’a pas de composant D :. Pour plus d’informations, consultez [format de chaîne de descripteur de sécurité](/windows/win32/SecAuthZ/security-descriptor-string-format) .

Cette méthode appelle [convertstringsecuritydescriptortosecuritydescriptor a](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw).

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
