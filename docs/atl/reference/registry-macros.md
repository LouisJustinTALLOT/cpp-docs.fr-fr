---
title: Macros de Registre | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed9b172217f1ca7ada7d8752151126b53055df37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365215"
---
# <a name="registry-macros"></a>Macros de Registre
Ces macros définissent des installations de bibliothèque et de Registre de type utile.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY À](#_atl_static_registry)|Indique que vous souhaitez que le code de l’inscription de votre objet dans l’objet pour éviter une dépendance sur ATL. DLL.|  
|[DECLARE_LIBID](#declare_libid)|Fournit un moyen de ATL obtenir le *libid* de la bibliothèque de types.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Permet d’éviter l’enregistrement ATL par défaut.|  
|[DECLARE_REGISTRY](#declare_registry)|Insère ou supprime l’entrée de l’objet principal dans le Registre système.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Spécifie les informations requises pour inscrire automatiquement le *appid*.|  
|[MACRO DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Recherche de la ressource nommée et exécute le script de Registre qu’il contient.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Recherche de la ressource identifiée par un numéro d’identification et exécute le script de Registre qu’il contient.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY À  
 Un symbole qui indique le code de l’inscription de votre objet dans l’objet pour éviter une dépendance sur ATL. DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Notes  
 Lorsque vous définissez **ATL_STATIC_REGISTRY**, vous devez utiliser le code suivant :  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 Fournit un moyen de ATL obtenir le *libid* de la bibliothèque de types.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Paramètres  
 *LIBID*  
 GUID de la bibliothèque de types.  
  
### <a name="remarks"></a>Notes  
 Utilisez `DECLARE_LIBID` dans un `CAtlModuleT`-classe dérivée.  
  
### <a name="example"></a>Exemple  
 Attributs non des projets générés par l’Assistant ATL aura un exemple d’utilisation de cette macro.  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 Utilisez `DECLARE_NO_REGISTRY` si vous souhaitez éviter toute inscription ATL par défaut pour la classe dans laquelle cette macro s’affiche.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 Passe à l’inscription de classe standard dans le Registre système ou retire le Registre système.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Paramètres  
 `class`  
 [in] Inclus pour la compatibilité descendante.  
  
 `pid`  
 [in] Un `LPCTSTR` qui est un identificateur de programme de la version spécifique.  
  
 *vpid*  
 [in] Un `LPCTSTR` qui est un identificateur de programme indépendant de la version.  
  
 *NID*  
 [in] A **UINT** qui est un index de la chaîne de ressource dans le Registre à utiliser en tant que la description du programme.  
  
 `flags`  
 [in] A `DWORD` contenant le programme de thread du modèle dans le Registre. Doit être une des valeurs suivantes : **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, ou **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Notes  
 L’inscription standard se compose des CLSID, ID de programme, ID de version indépendant du programme, chaîne de description, modèle de thread.  
  
 Lorsque vous créez un objet ou contrôler à l’aide de l’Assistant Ajout de classes ATL, l’Assistant implémente la prise en charge basée sur un script de Registre automatiquement et ajoute les [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro à vos fichiers. Si vous ne souhaitez pas de prise en charge basée sur un script de Registre, vous devez remplacer cette macro avec `DECLARE_REGISTRY`. `DECLARE_REGISTRY` insère uniquement les cinq clés de base décrites ci-dessus dans le Registre. Vous devez écrire manuellement le code pour insérer d’autres clés dans le Registre.  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 Spécifie les informations requises pour inscrire automatiquement le *appid*.  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>Paramètres  
 *RESID*  
 L’id de ressource du fichier .rgs qui contient des informations sur la *appid*.  
  
 *AppID*  
 GUID.  
  
### <a name="remarks"></a>Notes  
 Utilisez `DECLARE_REGISTRY_APPID_RESOURCEID` dans un `CAtlModuleT`-classe dérivée.  
  
### <a name="example"></a>Exemple  
 Classes ajoutées aux projets ATL avec l’Assistant code ajouter une classe aura un exemple d’utilisation de cette macro.  
  
##  <a name="declare_registry_resource"></a>  MACRO DECLARE_REGISTRY_RESOURCE  
 Obtient la ressource nommée contenant le fichier de Registre et exécute le script afin d’entrer des objets dans le Registre système ou de les supprimer à partir du Registre système.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Identificateur de votre ressource de chaîne.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous créez un objet ou contrôler à l’aide de l’Assistant Projet ATL, l’Assistant implémenter la prise en charge basée sur un script de Registre automatiquement et ajouter la [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) (macro), qui est similaire à `DECLARE_REGISTRY_RESOURCE`, à votre fichiers.  
  
 Vous pouvez lier statiquement avec le composant de Registre ATL (inscription) pour accéder au Registre optimisé. Pour lier statiquement au code bureau d’enregistrement, ajoutez la ligne suivante à votre fichier stdafx.h :  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si vous souhaitez ATL pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas le `DECLARE_REGISTRY_RESOURCE` ou `DECLARE_REGISTRY_RESOURCEID` (macro). Au lieu de cela, créez un tableau de **_ATL_REGMAP_ENTRIES** structures, où chaque entrée contient un espace réservé de variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cette opération ajoute toutes les valeurs de remplacement dans le **_ATL_REGMAP_ENTRIES** structures au mappage de remplacement du bureau d’enregistrement.  

  
 Pour plus d’informations sur les paramètres remplaçables et les scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 Identique à [macro DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) sauf qu’elle utilise un générées par l’Assistant **UINT** pour identifier la ressource, plutôt qu’un nom de chaîne.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Générées par l’Assistant l’identificateur de votre ressource.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous créez un objet ou contrôler à l’aide de l’Assistant Projet ATL, l’Assistant implémenter la prise en charge basée sur un script de Registre automatiquement et ajouter la `DECLARE_REGISTRY_RESOURCEID` macro à vos fichiers.  
  
 Vous pouvez lier statiquement avec le composant de Registre ATL (inscription) pour accéder au Registre optimisé. Pour lier statiquement au code bureau d’enregistrement, ajoutez la ligne suivante à votre fichier stdafx.h :  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Si vous souhaitez ATL pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas le `DECLARE_REGISTRY_RESOURCE` ou `DECLARE_REGISTRY_RESOURCEID` (macro). Au lieu de cela, créez un tableau de **_ATL_REGMAP_ENTRIES** structures, où chaque entrée contient un espace réservé de variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) ou [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), en passant le tableau. Cette opération ajoute toutes les valeurs de remplacement dans le **_ATL_REGMAP_ENTRIES** structures au mappage de remplacement du bureau d’enregistrement.  

  
 Pour plus d’informations sur les paramètres remplaçables et les scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)
