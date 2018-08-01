---
title: _com_ptr_t::GetActiveObject | Microsoft Docs
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
ms.openlocfilehash: 392460cde35096bc1c61db4d7e6bd2143932838d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403993"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Section spécifique à Microsoft**  
  
 S’attache à une instance existante d’un objet doté d’un `CLSID` ou `ProgID`.  
  
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
 *rclsid*  
 Le `CLSID` d’un objet.  
  
 *clsidString*  
 Une chaîne Unicode qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.  
  
 *clsidStringA*  
 Chaîne multioctet, à l’aide de la page de codes ANSI, qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.  
  
## <a name="remarks"></a>Notes  
 Ces fonctions membres appellent **GetActiveObject** pour récupérer un pointeur vers un objet en cours d’exécution qui a été inscrit avec OLE et ensuite les requêtes de ce pointeur intelligent type d’interface. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.  
  
-   **GetActiveObject (**`rclsid`**)** s’attache à une instance existante d’un objet doté d’un `CLSID`.  
  
-   **GetActiveObject (**`clsidString`**)** s’attache à une instance existante d’un objet doté d’une chaîne Unicode qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.  
  
-   **GetActiveObject (**`clsidStringA`**)** s’attache à une instance existante d’un objet doté d’une chaîne de caractères multioctets qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`. Appels [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072), ce qui suppose que la chaîne est dans la page de codes ANSI plutôt que dans une page de codes OEM.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_ptr_t, classe](../cpp/com-ptr-t-class.md)