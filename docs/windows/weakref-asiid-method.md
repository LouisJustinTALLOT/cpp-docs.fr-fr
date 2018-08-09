---
title: Weakref::asiid, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e5ff6510463a6fed06534236612feb460919e37
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643483"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID, méthode
Définit le texte spécifié `ComPtr` paramètre de pointeur pour représenter l’ID de l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *riid*  
 ID d’interface.  
  
 *ptr*  
 Lorsque cette opération se termine, un objet qui représente le paramètre *riid*.  
  
## <a name="return-value"></a>Valeur de retour  
  
-   S_OK si cette opération réussit ; Sinon, un HRESULT qui indique la raison pour laquelle l’opération a échoué, et *ptr* a la valeur **nullptr**.  
  
-   S_OK si cette opération réussit, mais actuel **WeakRef** l’objet a déjà été libéré. Paramètre *ptr* a la valeur **nullptr**.  
  
-   S_OK si cette opération réussit, mais actuel **WeakRef** objet n’est pas dérivé de paramètre *riid*. Paramètre *ptr* a la valeur **nullptr**. (Pour plus d’informations, consultez la section Notes.)  
  
## <a name="remarks"></a>Notes  
 Une erreur est émise si le paramètre *riid* n’est pas dérivé `IInspectable`. Cette erreur remplace la valeur de retour.  
  
 Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle (non illustré ici, mais déclaré dans le fichier d’en-tête) est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../cpp/auto-cpp.md) .  
  
 À compter dans le SDK Windows 10, cette méthode n’affecte pas la **WeakRef** l’instance à **nullptr** si la référence faible n’a pas pu être obtenue, vous devez donc éviter le code de vérification des erreurs qui vérifie le **WeakRef** pour **nullptr**. Au lieu de cela, vérifiez *ptr* pour **nullptr**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)