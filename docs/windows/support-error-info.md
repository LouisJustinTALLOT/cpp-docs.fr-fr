---
title: support_error_info | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.support_error_info
dev_langs: C++
helpviewer_keywords: support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 308ab8752b6bd77693e40239d92cc62b6f42caf2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="supporterrorinfo"></a>support_error_info
Implémente la prise en charge du retour d’erreurs détaillées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ support_error_info(  
   error_interface=uuid  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **error_interface**  
 Identificateur de l’interface qui implémente **IErrorInfo**.  
  
## <a name="remarks"></a>Remarques  
 L’attribut C++ **support_error_info** implémente la prise en charge permettant de retourner au client les erreurs détaillées et contextuelles rencontrées par l’objet cible. Pour que l’objet prenne en charge les erreurs, les méthodes de l’interface **IErrorInfo** doivent être implémentées par l’objet. Pour plus d’informations, consultez [Prise en charge d’IDispatch et IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md).  
  
 Cet attribut ajoute la classe [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) comme classe de base à l’objet cible. Il en résulte une implémentation par défaut de **ISupportErrorInfo** qui peut être utilisée quand une seule interface génère des erreurs sur un objet.  
  
## <a name="example"></a>Exemple  
 Le code suivant ajoute la prise en charge par défaut de l’interface **ISupportErrorInfo** à l’objet `CMyClass` .  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**|  
|**Renouvelable**|Oui|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs COM](../windows/com-attributes.md)   
 [Attributs de classe](../windows/class-attributes.md)   
