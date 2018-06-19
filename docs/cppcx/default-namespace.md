---
title: par défaut d’espace de noms | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f4386d3636744a673a10dd9530fd3836fdb78e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086943"
---
# <a name="default-namespace"></a>espace de noms par défaut
Le `default` les types intégrés qui sont pris en charge par C + définit la portée espace de noms c++ / CX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace default;  
```  
  
### <a name="members"></a>Membres  
 Tous les types intégrés héritent des membres suivants.  
  
|||  
|-|-|  
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Détermine si l'objet spécifié est identique à l'objet actuel.|  
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Retourne le code de hachage de cette instance.|  
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Retourne une chaîne qui représente le type actuel.|  
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Retourne une chaîne qui représente le type actuel.|  
  
### <a name="built-in-types"></a>Types intégrés  
  
|Name|Description|  
|----------|-----------------|  
|`char16`|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|  
|`float32`|Nombre à virgule flottante IEEE 754 32 bits.|  
|`float64`|Nombre à virgule flottante IEEE 754 64 bits.|  
|`int16`|Entier signé 16 bits.|  
|`int32`|Entier signé 32 bits.|  
|`int64`|Entier signé 64 bits.|  
|`int8`|Valeur numérique signée 8 bits.|  
|`uint16`|Entier non signé 16 bits.|  
|`uint32`|Entier non signé 32 bits.|  
|`uint64`|Entier non signé 64 bits.|  
|`uint8`|Valeur numérique non signée 8 bits.|  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** vccorlib.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)