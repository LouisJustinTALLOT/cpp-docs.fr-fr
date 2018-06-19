---
title: Interfacetraits::fillarraywithiid, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6e32b2e40ba9dc2b8085f8edc99beb899e90ace
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877488"
---
# <a name="interfacetraitsfillarraywithiid-method"></a>InterfaceTraits::FillArrayWithIid, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 Pointeur vers un champ qui contient une valeur d’index de base zéro.  
  
 `iids`  
 Tableau d’ID d’interface.  
  
## <a name="remarks"></a>Notes  
 Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.  
  
 Contraire à celui de cette API, un seul groupe est modifié ; pas l’intégralité du tableau.  
  
 Pour plus d’informations sur `Base`, consultez la section Typedefs publics dans [interfacetraits, Structure](../windows/interfacetraits-structure.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)