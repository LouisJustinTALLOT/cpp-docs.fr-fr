---
title: raw_native_types | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5baa3204b14da53f6a6a3232874e0ac7de0fd91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849793"
---
# <a name="rawnativetypes"></a>raw_native_types
**Spécifique à C++**  
  
 Désactive l'utilisation des classes de prise en charge COM dans les fonctions wrapper de haut niveau et force l'utilisation de types de données de bas niveau à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, les méthodes de gestion des erreurs de haut niveau utilisent les classes de prise en charge COM [_bstr_t](../cpp/bstr-t-class.md) et [_variant_t](../cpp/variant-t-class.md) à la place de la `BSTR` et **VARIANT** des types de données et pointeurs d’interface COM bruts. Ces classes encapsulent les détails de l'allocation et de la libération du stockage de mémoire pour ces types de données, et simplifient considérablement le casting de type et les opérations de conversion.  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)