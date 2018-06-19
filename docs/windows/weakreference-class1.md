---
title: WeakReference Class1 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a44b992138371ff33a9059990a5ec3e93689c679
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891644"
---
# <a name="weakreference-class1"></a>WeakReference Class1
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>Notes  
 Représente un *référence faible* qui peut être utilisé avec le Windows Runtime ou le COM classique. Une référence faible représente un objet qui peut être accessible ou non.  
  
 A `WeakReference` objet conserve un *référence forte*, qui est un pointeur vers un objet et un *nombre de référence forte*, qui est le nombre de copies de la référence forte qui ont été distribuées par la méthode Resolve(). Alors que le nombre de référence forte est différente de zéro, la référence forte est valide et l’objet est accessible. Lorsque le nombre de référence forte devient égal à zéro, la référence forte n’est pas valide et que l’objet n’est pas accessible.  
  
 Un objet WeakReference est généralement utilisé pour représenter un objet dont l’existence est contrôlée par un thread externe ou une application. Par exemple, construisez un objet WeakReference à partir d’une référence à un objet fichier. Pendant que le fichier est ouvert, la référence forte est valide, mais si le fichier est fermé, la référence forte devient non valide.  
  
 Les méthodes de WeakReference sont thread-safe.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[WeakReference::WeakReference, constructeur](../windows/weakreference-weakreference-constructor.md)|Initialise une nouvelle instance de la classe WeakReference.|  
|[WeakReference::~WeakReference, destructeur](../windows/weakreference-tilde-weakreference-destructor.md)|Désinitialise (détruit) l’instance actuelle de la classe WeakReference.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference, méthode](../windows/weakreference-decrementstrongreference-method.md)|Décrémente le fort décompte de références de l’objet WeakReference actuel.|  
|[WeakReference::IncrementStrongReference, méthode](../windows/weakreference-incrementstrongreference-method.md)|Incrémente le décompte de références fort de l’objet WeakReference actuel.|  
|[WeakReference::Resolve, méthode](../windows/weakreference-resolve-method.md)|Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.|  
|[WeakReference::SetUnknown, méthode](../windows/weakreference-setunknown-method.md)|Définit la référence forte de l’objet WeakReference actuel sur le pointeur d’interface spécifié.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `WeakReference`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)