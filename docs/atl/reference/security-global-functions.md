---
title: Fonctions globales de sécurité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- SIDs [C++], modifying SID objects
- ACL object global functions
- security IDs [C++]
ms.assetid: 6a584bfe-16b7-47f4-8439-9c789c41567a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9ad170706b72c9d236e095db0e2b6df00031ff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365052"
---
# <a name="security-global-functions"></a>Fonctions de sécurité Global
Ces fonctions prennent en charge la modification des objets de SID et la liste ACL.  
  
> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 **En-tête :** atlsecurity.h 

##  <a name="atlgetdacl"></a>  AtlGetDacl  
 Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlGetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CDacl* pDacl) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet pour lequel récupérer les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `pDacl`  
 Pointeur vers un objet de liste DACL qui contiendra les informations de sécurité récupérées.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, une erreur d’assertion se produit si le paramètre `hObject` ou `pDacl` n’est pas valide.  
  
##  <a name="atlsetdacl"></a>  AtlSetDacl  
 Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès discrétionnaire (DACL) d'un objet spécifique.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlSetDacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CDacl& rDacl,
    DWORD dwInheritanceFlowControl = 0) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet pour lequel définir les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `rDacl`  
 La liste DACL contenant les nouvelles informations de sécurité.  
  
 `dwInheritanceFlowControl`  
 Le contrôle de flux d’héritage. Cette valeur peut être 0 (valeur par défaut), PROTECTED_DACL_SECURITY_INFORMATION ou UNPROTECTED_DACL_SECURITY_INFORMATION.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, une erreur d’assertion se produit si `hObject` n’est pas valide, ou si `dwInheritanceFlowControl` n’est pas une des trois valeurs autorisées.  
### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlgetgroupsid"></a>  AtlGetGroupSid  
 Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de groupe d'un objet.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlGetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet à partir duquel récupérer les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `pSid`  
 Pointeur vers un `CSid` objet qui contient les nouvelles informations de sécurité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlsetgroupsid"></a>  AtlSetGroupSid  
 Appelez cette fonction pour définir l'identificateur de sécurité (SID) de groupe d'un objet.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlSetGroupSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet pour lequel définir les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `rSid`  
 Le `CSid` objet contenant les nouvelles informations de sécurité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlgetownersid"></a>  AtlGetOwnerSid  
 Appelez cette fonction pour récupérer l'identificateur de sécurité (SID) de propriétaire d'un objet.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlGetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSid* pSid) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet à partir duquel récupérer les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `pSid`  
 Pointeur vers un `CSid` objet qui contient les nouvelles informations de sécurité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlsetownersid"></a>  AtlSetOwnerSid  
 Appelez cette fonction pour définir l'identificateur de sécurité (SID) de propriétaire d'un objet.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlSetOwnerSid(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet pour lequel définir les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `rSid`  
 Le `CSid` objet contenant les nouvelles informations de sécurité.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlgetsacl"></a>  AtlGetSacl  
 Appelez cette fonction pour récupérer les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlGetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    CSacl* pSacl,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet à partir duquel récupérer les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 `pSacl`  
 Pointeur vers un objet de liste (SACL) qui contient les informations de sécurité récupéré.  
  
 `bRequestNeededPrivileges`  
 Si la valeur est true, la fonction tentera activer le privilège SE_SECURITY_NAME et restaurez-la à la fin.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Si `AtlGetSacl` doit être appelée plusieurs fois sur de nombreux objets différents, il sera plus efficace pour activer le privilège SE_SECURITY_NAME qu’une seule fois avant d’appeler la fonction, avec `bRequestNeededPrivileges` défini sur false.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlsetsacl"></a>  AtlSetSacl  
 Appelez cette fonction pour définir les informations relatives à la liste de contrôle d'accès système (SACL) d'un objet spécifique.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
```
inline bool AtlSetSacl(
    HANDLE hObject,
    SE_OBJECT_TYPE ObjectType,
    const CSacl& rSacl,
    DWORD dwInheritanceFlowControl = 0,
    bool bRequestNeededPrivileges = true) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `hObject`  
 Handle vers l’objet pour lequel définir les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le `hObject` paramètre.  
  
 *rSacl*  
 La liste SACL contenant les nouvelles informations de sécurité.  
  
 `dwInheritanceFlowControl`  
 Le contrôle de flux d’héritage. Cette valeur peut être 0 (valeur par défaut), PROTECTED_SACL_SECURITY_INFORMATION ou UNPROTECTED_SACL_SECURITY_INFORMATION.  
  
 `bRequestNeededPrivileges`  
 Si la valeur est true, la fonction tentera activer le privilège SE_SECURITY_NAME et restaurez-la à la fin.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, une erreur d’assertion se produit si `hObject` n’est pas valide, ou si `dwInheritanceFlowControl` n’est pas une des trois valeurs autorisées.  
  
 Si `AtlSetSacl` doit être appelée plusieurs fois sur de nombreux objets différents, il sera plus efficace pour activer le privilège SE_SECURITY_NAME qu’une seule fois avant d’appeler la fonction, avec `bRequestNeededPrivileges` défini sur false.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 

##  <a name="atlgetsecuritydescriptor"></a>  AtlGetSecurityDescriptor  
 Appelez cette fonction pour récupérer le descripteur de sécurité d'un objet donné.  
  
> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 *pszObjectName*  
 Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’objet à partir duquel récupérer les informations de sécurité.  
  
 `ObjectType`  
 Spécifie une valeur à partir de la [SE_OBJECT_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379593) énumération qui indique le type de l’objet identifié par le *pszObjectName* paramètre.  
  
 *pSecurityDescriptor*  
 Objet qui reçoit le descripteur de sécurité demandée.  
  
 *requestedInfo*  
 Un ensemble de [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bits indicateurs qui indiquent le type d’informations de sécurité à récupérer. Ce paramètre peut être une combinaison des valeurs suivantes.  
  
 `bRequestNeededPrivileges`  
 Si la valeur est true, la fonction tentera activer le privilège SE_SECURITY_NAME et restaurez-la à la fin.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true en cas de réussite, false en cas d'échec.  
  
### <a name="remarks"></a>Notes  
 Si `AtlGetSecurityDescriptor` doit être appelée plusieurs fois sur de nombreux objets différents, il sera plus efficace pour activer le privilège SE_SECURITY_NAME qu’une seule fois avant d’appeler la fonction, avec `bRequestNeededPrivileges` défini sur false.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsecurity.h 
   
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)
