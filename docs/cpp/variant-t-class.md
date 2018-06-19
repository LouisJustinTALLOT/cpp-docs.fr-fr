---
title: _variant_t (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebe850e4b0d0d9fd352df0e60c4ea0737b9fd8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422977"
---
# <a name="variantt-class"></a>_variant_t (classe)
**Section spécifique à Microsoft**  
  
 A `_variant_t` objet encapsule le `VARIANT` type de données. La classe gère l’allocation des ressources et la désallocation et effectue des appels de fonction à **VariantInit** et **VariantClear** selon le cas.  
  
### <a name="construction"></a>Construction  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|Construit un objet `_variant_t`.|  
  
### <a name="operations"></a>Opérations  
  
|||  
|-|-|  
|[Attacher](../cpp/variant-t-attach.md)|Attache un **VARIANT** de l’objet dans le `_variant_t` objet.|  
|[Effacer](../cpp/variant-t-clear.md)|Efface encapsulé **VARIANT** objet.|  
|[ChangeType](../cpp/variant-t-changetype.md)|Modifie le type de la `_variant_t` objet au **VARTYPE**.|  
|[Détacher](../cpp/variant-t-detach.md)|Détache encapsulé **VARIANT** objet à partir de ce `_variant_t` objet.|  
|[setString](../cpp/variant-t-setstring.md)|Assigne une chaîne à cet objet `_variant_t`.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur =](../cpp/variant-t-operator-equal.md)|Assigne une nouvelle valeur à un objet `_variant_t` existant.|  
|[opérateur ==, ! =](../cpp/variant-t-relational-operators.md)|Comparez deux objets `_variant_t` pour déterminer leur égalité ou inégalité.|  
|[Extracteurs](../cpp/variant-t-extractors.md)|Extraire des données d’encapsulé **VARIANT** objet.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<comutil.h >  
  
 **Lib :** comsuppw.lib ou comsuppwd.lib (consultez [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)  
  
## <a name="see-also"></a>Voir aussi  
 [Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)