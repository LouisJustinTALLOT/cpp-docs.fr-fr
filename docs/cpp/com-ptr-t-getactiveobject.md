---
title: _com_ptr_t::GetActiveObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca25ca31475d2870e62d00676e7bf3717c10fa3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414742"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Section spécifique à Microsoft**  
  
 Joint à une instance existante d’un objet avec un **CLSID** ou **ProgID**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rclsid`  
 Le **CLSID** d’un objet.  
  
 `clsidString`  
 Une chaîne Unicode qui contient un **CLSID** (en commençant par «**{**») ou un **ProgID**.  
  
 `clsidStringA`  
 Chaîne multioctet, à l’aide de la page de codes ANSI, qui contient un **CLSID** (en commençant par «**{**») ou un **ProgID**.  
  
## <a name="remarks"></a>Notes  
 Ces fonctions membres appellent `GetActiveObject` pour récupérer un pointeur vers un objet en cours d'exécution qui a été inscrit avec OLE, puis des requêtes pour le type d'interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. **Version** est appelé pour décrémenter le décompte de références du pointeur précédemment encapsulé. Cette routine retourne l'objet `HRESULT` pour indiquer un succès ou un échec.  
  
-   **GetActiveObject (**`rclsid`**)** joint à une instance existante d’un objet avec un **CLSID**.      
  
-   **GetActiveObject (**`clsidString`**)** joint à une instance existante d’un objet avec une chaîne Unicode qui contient un **CLSID** (en commençant par «**{**») ou un **ProgID**.      
  
-   **GetActiveObject (**`clsidStringA`**)** joint à une instance existante d’un objet avec une chaîne de caractères multioctets qui contient un **CLSID** (en commençant par «**{}** ») ou un **ProgID**.     Appels [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), qui suppose que la chaîne figure dans la page de codes ANSI plutôt que sur une page de codes OEM.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_ptr_t, classe](../cpp/com-ptr-t-class.md)