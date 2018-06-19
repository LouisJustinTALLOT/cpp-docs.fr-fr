---
title: extracteurs _variant_t | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
dev_langs:
- C++
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65049a473f62e728fcb4d74b581a08c0f1723fc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423316"
---
# <a name="variantt-extractors"></a>Extracteurs _variant_t
**Section spécifique à Microsoft**  
  
 Extraire des données d’encapsulé **VARIANT** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator short( ) const;   
operator long( ) const;   
operator float( ) const;   
operator double( ) const;   
operator CY( ) const;   
operator _bstr_t( ) const;   
operator IDispatch*( ) const;   
operator bool( ) const;   
operator IUnknown*( ) const;   
operator DECIMAL( ) const;   
operator BYTE( ) const;  
operator VARIANT() const throw();  
operator char() const;  
operator unsigned short() const;  
operator unsigned long() const;  
operator int() const;  
operator unsigned int() const;  
operator __int64() const;  
operator unsigned __int64() const;  
```  
  
## <a name="remarks"></a>Notes  
 Extrait des données brutes d’un encapsulé **variante**. Si le **VARIANT** n’est pas déjà le type approprié, **VariantChangeType** est utilisé pour effectuer une conversion, et une erreur est générée en cas d’échec :  
  
-   **operator short ()** extrait un **court** valeur entière.  
  
-   **operator long ()** extrait un **long** valeur entière.  
  
-   **operator float ()** extrait un **float** valeur numérique.  
  
-   **operator double ()** extrait un **double** valeur entière.  
  
-   **operator CY ()** extrait un **CY** objet.  
  
-   **operator bool ()** extrait un `bool` valeur.  
  
-   **operator DECIMAL ()** extrait un **décimal** valeur.  
  
-   **operator BYTE ()** extrait un **octets** valeur.  
  
-   **operator _bstr_t ()** extrait une chaîne, qui est encapsulée dans un `_bstr_t` objet.  
  
-   **opérateur IDispatch\*()** extrait un pointeur dispinterface un encapsulé **variante**. `AddRef` est appelé sur le pointeur résultant, il vous appartient donc d’appeler **version** pour le libérer.  
  
-   **opérateur IUnknown\*()** extrait un pointeur d’interface COM à partir d’un élément encapsulé **variante**. `AddRef` est appelé sur le pointeur résultant, il vous appartient donc d’appeler **version** pour le libérer.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_variant_t, classe](../cpp/variant-t-class.md)
