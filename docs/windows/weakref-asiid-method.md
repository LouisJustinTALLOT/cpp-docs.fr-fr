---
title: Weakref::asiid, méthode | Documents Microsoft
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
ms.openlocfilehash: 69108681b181d0b2fce20f9e30a009b6b93c2180
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891296"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID, méthode
Définit le paramètre de pointeur ComPtr spécifié pour qu’il représente l’ID d’interface spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 ID d’interface.  
  
 `ptr`  
 Quand cette opération est terminée, objet qui représente le paramètre `riid`.  
  
## <a name="return-value"></a>Valeur de retour  
  
-   S_OK si cette opération réussit ; dans le cas contraire, un HRESULT qui indique la raison pour laquelle l’opération a échoué, et `ptr` prend la valeur `nullptr`.  
  
-   S_OK si cette opération réussit, mais que l’objet WeakRef actif a déjà été libéré. Le paramètre `ptr` prend la valeur `nullptr`.  
  
-   S_OK si cette opération réussit, mais que l’objet WeakRef actif n’est pas dérivé du paramètre `riid`. Le paramètre `ptr` prend la valeur `nullptr`. (Pour plus d’informations, consultez la section Notes.)  
  
## <a name="remarks"></a>Notes  
 Une erreur est générée si le paramètre `riid` n’est pas dérivé d’IInspectable. Cette erreur remplace la valeur de retour.  
  
 Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle (non illustré ici, mais déclaré dans le fichier d’en-tête) est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../cpp/auto-cpp.md) .  
  
 À compter du Kit de développement logiciel SDK Windows 10, cette méthode n’affecte pas la valeur `nullptr` à l’instance WeakRef si la référence faible n’a pas pu être obtenue. Vous devez donc éviter le code de vérification des erreurs qui vérifie si WeakRef est `nullptr`. Au lieu de cela, vérifiez `ptr` pour `nullptr`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)