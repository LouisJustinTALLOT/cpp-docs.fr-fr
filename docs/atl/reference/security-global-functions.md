---
title: Fonctions globales de sécurité
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::AtlGetDacl
- atlsecurity/ATL::AtlSetDacl
- atlsecurity/ATL::AtlGetGroupSid
- atlsecurity/ATL::AtlSetGroupSid
- atlsecurity/ATL::AtlGetOwnerSid
- atlsecurity/ATL::AtlSetOwnerSid
- atlsecurity/ATL::AtlGetSacl
- atlsecurity/ATL::AtlSetSacl
- atlsecurity/ATL::AtlGetSecurityDescriptor
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
ms.openlocfilehash: 682d44aa80f5d6de521223dfd67db2813cb6738c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326032"
---
# <a name="security-global-functions"></a>Fonctions globales de sécurité

Ces fonctions fournissent un support pour modifier les objets SID et ACL.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlGetDacl](#atlgetdacl)|Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.|
|[AtlSetDacl](#atlsetdacl)|Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.|
|[AtlGetGroupSid](#atlgetgroupsid)|Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de groupe d'un objet.|
|[AtlSetGroupSid](#atlsetgroupsid)|Appelez cette fonction pour définir l'identificateur de sécurité (SID) de groupe d'un objet.|
|[AtlGetOwnerSid](#atlgetownersid)|Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de propriétaire d'un objet.|
|[AtlSetOwnerSid](#atlsetownersid)|Appelez cette fonction pour définir l'identificateur de sécurité (SID) de propriétaire d'un objet.|
|[AtlGetSacl](#atlgetsacl)|Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.|
|[AtlSetSacl](#atlsetsacl)|Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.|
|[AtlGetSecurityDescriptor](#atlgetsecuritydescriptor)|Appelez cette fonction pour récupérer le descripteur de sécurité d'un objet donné.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a>AtlGetDacl (en)

Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Portez-le à l’objet pour lequel récupérer les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*pDacl (en)*<br/>
Pointeur vers un objet DACL qui contiendra les informations de sécurité récupérées.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si *hObject* ou *pDacl* est invalide.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a>AtlSetDacl

Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet pour lequel définir les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*rDacl rDacl*<br/>
Le DACL contenant les nouvelles informations de sécurité.

*dwInheritanceFlowControl*<br/>
Le contrôle du flux d’héritage. Cette valeur peut être de 0 (par défaut), PROTECTED_DACL_SECURITY_INFORMATION ou UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si *hObject* est invalide, ou si *dwInheritanceFlowControl* n’est pas l’une des trois valeurs autorisées.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a>AtlGetGroupSid (en anglais)

Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de groupe d'un objet.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet à partir duquel récupérer les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*pSid*<br/>
Pointeur `CSid` vers un objet qui contiendra les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a>AtlSetGroupSid (en anglais)

Appelez cette fonction pour définir l'identificateur de sécurité (SID) de groupe d'un objet.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet pour lequel définir les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*rSid*<br/>
L’objet `CSid` contenant les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a>AtlGetOwnerSid

Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de propriétaire d'un objet.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet à partir duquel récupérer les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*pSid*<br/>
Pointeur `CSid` vers un objet qui contiendra les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a>AtlSetOwnerSid

Appelez cette fonction pour définir l'identificateur de sécurité (SID) de propriétaire d'un objet.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet pour lequel définir les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*rSid*<br/>
L’objet `CSid` contenant les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a>AtlGetSacl (en)

Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Manipulez l’objet à partir duquel récupérer les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*pSacl (en)*<br/>
Pointeur vers un objet SACL qui contiendra les informations de sécurité récupérées.

*bRequestNeededPrivileges (en)*<br/>
Si c’est vrai, la fonction tentera de permettre le privilège SE_SECURITY_NAME, et de le restaurer à l’achèvement.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Si `AtlGetSacl` l’on veut être appelé plusieurs fois sur de nombreux objets différents, il sera plus efficace pour permettre au privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* mis à faux.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a>AtlSetSacl (atlSetSacl)

Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*hObject*<br/>
Gérer l’objet pour lequel définir les informations de sécurité.

*Objecttype*<br/>
Specifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject.*

*rSacl (en)*<br/>
La SACL contenant les nouvelles informations de sécurité.

*dwInheritanceFlowControl*<br/>
Le contrôle du flux d’héritage. Cette valeur peut être de 0 (par défaut), PROTECTED_SACL_SECURITY_INFORMATION ou UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges (en)*<br/>
Si c’est vrai, la fonction tentera de permettre le privilège SE_SECURITY_NAME, et de le restaurer à l’achèvement.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si *hObject* est invalide, ou si *dwInheritanceFlowControl* n’est pas l’une des trois valeurs autorisées.

Si `AtlSetSacl` l’on veut être appelé plusieurs fois sur de nombreux objets différents, il sera plus efficace pour permettre au privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* mis à faux.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a>AtlGetSecurityDescriptor

Appelez cette fonction pour récupérer le descripteur de sécurité d'un objet donné.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
inline bool AtlGetSecurityDescriptor(
    LPCTSTR pszObjectName,
    SE_OBJECT_TYPE ObjectType,
    CSecurityDesc* pSecurityDescriptor,
    SECURITY_INFORMATION requestedInfo = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION,
bool bRequestNeededPrivileges = true) throw(...);
```

### <a name="parameters"></a>Paramètres

*pszObjectName*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom de l’objet à partir duquel récupérer les informations de sécurité.

*Objecttype*<br/>
Spécifie une valeur du [recensement SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *pszObjectName.*

*pSecurityDescriptor*<br/>
L’objet qui reçoit le descripteur de sécurité demandé.

*demandéInfo*<br/>
Un ensemble de [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) a mordu des drapeaux qui indiquent le type d’informations de sécurité à récupérer. Ce paramètre peut être une combinaison des valeurs suivantes.

*bRequestNeededPrivileges (en)*<br/>
Si c’est vrai, la fonction tentera de permettre le privilège SE_SECURITY_NAME, et de le restaurer à l’achèvement.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Si `AtlGetSecurityDescriptor` l’on veut être appelé plusieurs fois sur de nombreux objets différents, il sera plus efficace pour permettre au privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* mis à faux.

### <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
