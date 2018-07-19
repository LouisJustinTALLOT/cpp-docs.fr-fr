---
title: _com_error::_com_error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942853"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Section spécifique à Microsoft**  
  
 Construit un objet `_com_error`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ressources humaines*  
 Informations HRESULT.  
  
 *perrinfo*  
 Objet `IErrorInfo`.  
  
 `bool fAddRef=false`  
 Provoque le constructeur à appeler AddRef sur une valeur non null `IErrorInfo` interface. Cela permet un décompte de références correct dans le cas fréquent où la propriété de l'interface est passée dans l'objet `_com_error`, comme suit :  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Si vous ne souhaitez pas que votre code pour transférer la propriété à la `_com_error` objet et le `AddRef` est requis pour décaler la `Release` dans le `_com_error` destructeur, construisez l’objet comme suit :  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *qui*  
 Objet `_com_error` existant.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur crée un nouvel objet étant donné un HRESULT et facultatifs `IErrorInfo` objet. Le deuxième constructeur crée une copie d'un objet `_com_error` existant.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)