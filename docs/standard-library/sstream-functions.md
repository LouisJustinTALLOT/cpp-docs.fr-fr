---
title: '&lt;sstream&gt;, fonctions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bbc38cb453c010f7d395372a5eb9f121cd6e3dc8
ms.lasthandoff: 02/24/2017

---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt;, fonctions
||  
|-|  
|[swap](#sstream_swap)|  
  
##  <a name="a-namesstreamswapa--swap"></a><a name="sstream_swap"></a>  swap  
 Échange les valeurs entre deux objets `sstream`.  
  
```  
template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,  
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,  
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,  
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>  
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,  
    basic_stringstream<Elem, Tr, Alloc>& right);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|` left`|Référence à un objet `sstream`.|  
|` right`|Référence à un objet `sstream`.|  
  
### <a name="remarks"></a>Notes  
 La fonction de modèle exécute ` left``.swap(`` right``)`.  
  
## <a name="see-also"></a>Voir aussi  
 [\<sstream>](../standard-library/sstream.md)


