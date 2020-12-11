---
description: 'En savoir plus sur : fonctions globales de sécurité'
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
ms.openlocfilehash: 10a3a3f358eba3aa1715bd375221f6ec35a56fcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157787"
---
# <a name="security-global-functions"></a>Fonctions globales de sécurité

Ces fonctions assurent la prise en charge de la modification des objets SID et ACL.

> [!IMPORTANT]
> Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|Nom|Description|
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

**En-tête :** ATLSecurity. h

## <a name="atlgetdacl"></a><a name="atlgetdacl"></a> AtlGetDacl

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
Handle de l’objet pour lequel les informations de sécurité doivent être récupérées.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*pDacl*<br/>
Pointeur vers un objet DACL qui contient les informations de sécurité récupérées.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *hObject* ou *pDacl* n’est pas valide.

## <a name="atlsetdacl"></a><a name="atlsetdacl"></a> AtlSetDacl

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
Handle de l’objet pour lequel des informations de sécurité doivent être définies.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*rDacl*<br/>
Liste DACL contenant les nouvelles informations de sécurité.

*dwInheritanceFlowControl*<br/>
Contrôle de la répartition de l’héritage. Cette valeur peut être 0 (valeur par défaut), PROTECTED_DACL_SECURITY_INFORMATION ou UNPROTECTED_DACL_SECURITY_INFORMATION.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *hObject* n’est pas valide ou si *dwInheritanceFlowControl* n’est pas l’une des trois valeurs autorisées.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlgetgroupsid"></a><a name="atlgetgroupsid"></a> AtlGetGroupSid

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
Handle vers l’objet à partir duquel récupérer les informations de sécurité.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*pSid*<br/>
Pointeur vers un `CSid` objet qui contiendra les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlsetgroupsid"></a><a name="atlsetgroupsid"></a> AtlSetGroupSid

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
Handle de l’objet pour lequel des informations de sécurité doivent être définies.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*rSid*<br/>
`CSid`Objet contenant les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlgetownersid"></a><a name="atlgetownersid"></a> AtlGetOwnerSid

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
Handle vers l’objet à partir duquel récupérer les informations de sécurité.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*pSid*<br/>
Pointeur vers un `CSid` objet qui contiendra les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlsetownersid"></a><a name="atlsetownersid"></a> AtlSetOwnerSid

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
Handle de l’objet pour lequel des informations de sécurité doivent être définies.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*rSid*<br/>
`CSid`Objet contenant les nouvelles informations de sécurité.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlgetsacl"></a><a name="atlgetsacl"></a> AtlGetSacl

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
Handle vers l’objet à partir duquel récupérer les informations de sécurité.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*pSacl*<br/>
Pointeur vers un objet SACL qui contient les informations de sécurité récupérées.

*bRequestNeededPrivileges*<br/>
Si la valeur est true, la fonction tente d’activer le privilège SE_SECURITY_NAME et la restaure à l’achèvement.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Si `AtlGetSacl` doit être appelé plusieurs fois sur de nombreux objets différents, il est plus efficace d’activer le privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* défini sur false.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlsetsacl"></a><a name="atlsetsacl"></a> AtlSetSacl

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
Handle de l’objet pour lequel des informations de sécurité doivent être définies.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *hObject* .

*rSacl*<br/>
La liste SACL contenant les nouvelles informations de sécurité.

*dwInheritanceFlowControl*<br/>
Contrôle de la répartition de l’héritage. Cette valeur peut être 0 (valeur par défaut), PROTECTED_SACL_SECURITY_INFORMATION ou UNPROTECTED_SACL_SECURITY_INFORMATION.

*bRequestNeededPrivileges*<br/>
Si la valeur est true, la fonction tente d’activer le privilège SE_SECURITY_NAME et la restaure à l’achèvement.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *hObject* n’est pas valide ou si *dwInheritanceFlowControl* n’est pas l’une des trois valeurs autorisées.

Si `AtlSetSacl` doit être appelé plusieurs fois sur de nombreux objets différents, il est plus efficace d’activer le privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* défini sur false.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="atlgetsecuritydescriptor"></a><a name="atlgetsecuritydescriptor"></a> AtlGetSecurityDescriptor

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
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de l’objet à partir duquel récupérer les informations de sécurité.

*ObjectType*<br/>
Spécifie une valeur de l’énumération [SE_OBJECT_TYPE](/windows/win32/api/accctrl/ne-accctrl-se_object_type) qui indique le type d’objet identifié par le paramètre *pszObjectName* .

*pSecurityDescriptor*<br/>
Objet qui reçoit le descripteur de sécurité demandé.

*requestedInfo*<br/>
Ensemble d' [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) indicateurs de bits qui indiquent le type d’informations de sécurité à récupérer. Ce paramètre peut être une combinaison des valeurs suivantes.

*bRequestNeededPrivileges*<br/>
Si la valeur est true, la fonction tente d’activer le privilège SE_SECURITY_NAME et la restaure à l’achèvement.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Si `AtlGetSecurityDescriptor` doit être appelé plusieurs fois sur de nombreux objets différents, il est plus efficace d’activer le privilège SE_SECURITY_NAME une fois avant d’appeler la fonction, avec *bRequestNeededPrivileges* défini sur false.

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
