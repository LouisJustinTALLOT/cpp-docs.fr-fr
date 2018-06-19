---
title: ArgTraits (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
dev_langs:
- C++
helpviewer_keywords:
- ArgTraits structure
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 162fbdea86aef81582902340102d54777e3f861b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858040"
---
# <a name="argtraits-structure"></a>ArgTraits (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TMemberFunction>  
struct ArgTraits;  
template<typename TDelegateInterface>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TMemberFunction`  
 Paramètre de nom de type pour une ArgTraits (structure) qui ne peut pas correspondre à n’importe quelle signature de méthode Invoke.  
  
 `TDelegateInterface`  
 Une interface de délégué.  
  
 `TArg1`  
 Le type du premier argument de la méthode Invoke.  
  
 `TArg2`  
 Le type du second argument de la méthode Invoke.  
  
 `TArg3`  
 Le type du troisième argument de la méthode Invoke.  
  
 `TArg4`  
 Le type du quatrième argument de la méthode Invoke.  
  
 `TArg5`  
 Type du cinquième argument de la méthode Invoke.  
  
 `TArg6`  
 Type du sixième argument de la méthode Invoke.  
  
 `TArg7`  
 Type du septième argument de la méthode Invoke.  
  
 `TArg8`  
 Type du huitième argument de la méthode Invoke.  
  
 `TArg9`  
 Type du neuvième argument de la méthode Invoke.  
  
## <a name="remarks"></a>Notes  
 Le `ArgTraits` structure déclare un délégué spécifié interface et une fonction membre anonyme qui a un nombre spécifié de paramètres.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`Arg1Type`|Le typedef pour TArg1.|  
|`Arg2Type`|Le typedef pour TArg2.|  
|`Arg3Type`|Le typedef pour TArg3.|  
|`Arg4Type`|Le typedef pour TArg4.|  
|`Arg5Type`|Le typedef pour TArg5.|  
|`Arg6Type`|Le typedef pour TArg6.|  
|`Arg7Type`|Le typedef pour TArg7.|  
|`Arg8Type`|Le typedef pour TArg8.|  
|`Arg9Type`|Le typedef pour TArg9.|  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[ArgTraits::args, constante](../windows/argtraits-args-constant.md)|Conserve le décompte du nombre de paramètres dans la méthode Invoke d’une interface de délégué.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `ArgTraits`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)