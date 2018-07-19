---
title: _bstr_t::Copy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d23f204e7e8a545fbee7ab516495ed711d7984a9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943684"
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Section spécifique à Microsoft**  
  
 Construit une copie du `BSTR` encapsulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BSTR copy( bool fCopy = true ) const;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *fCopy*  
 Si la valeur est TRUE, `copy` retourne une copie de la relation contenant-contenu `BSTR`, sinon `copy` retourne le BSTR réel.  
  
## <a name="remarks"></a>Notes  
 Retourne une copie nouvellement allouée de l'objet `BSTR` encapsulé.  
  
## <a name="example"></a>Exemple  
  
```cpp 
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_bstr_t, classe](../cpp/bstr-t-class.md)