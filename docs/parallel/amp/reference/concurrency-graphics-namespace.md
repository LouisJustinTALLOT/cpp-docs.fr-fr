---
title: Concurrency::Graphics Namespace | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics
- amp_short_vectors/Concurrency::graphics
dev_langs:
- C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fd29b427307e336d560a2caf42e4fc5228e8071f
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics, espace de noms
L’espace de noms du graphique fournit des types et des fonctions conçues pour la programmation graphique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="namespaces"></a>Espaces de noms  
  
|Nom|Description|  
|----------|-----------------|  
|[Concurrency::Graphics::Direct3D Namespace](concurrency-graphics-direct3d-namespace.md)|Fournit des fonctions pour l’interopérabilité de Direct3D.|  
  
### <a name="typedefs"></a>Typedef  
  
|Nom|Description|  
|----------|-----------------|  
|`uint`|Le type d’élément de [uint_2, classe](uint-2-class.md), [uint_3, classe](uint-3-class.md), et [uint_4, classe](uint-4-class.md). Défini comme `typedef unsigned int uint;`.|  
  
### <a name="enumerations"></a>Énumérations  
  
|Nom|Description|  
|----------|-----------------|  
|[address_mode, énumération](concurrency-graphics-namespace-enums.md#address_mode).|Spécifie les modes d’adresse pris en charge pour l’échantillonnage de texture.|  
|[filter_mode, énumération](concurrency-graphics-namespace-enums.md#filter_mode)|Spécifie les modes de filtre pris en charge pour l’échantillonnage de texture.|  
  
### <a name="classes"></a>Classes  
  
|Nom|Description|  
|----------|-----------------|  
|[texture, classe](texture-class.md)|Une texture est un agrégat sur une accelerator_view dans le domaine de l’extension de données. Il est une collection de variables, un pour chaque élément dans un domaine de l’étendue. Chaque variable contient une valeur correspondant à un type primitif C++ (unsigned int, int, float, double) ou normales de type scalaire, ou unorm (défini dans concurrency::graphics) ou types de vecteurs courts éligibles définis dans concurrency::graphics.|  
|[writeonly_texture_view, classe](writeonly-texture-view-class.md)|Un writeonly_texture_view fournit un accès writeonly une texture.|  
|[double_2, classe](double-2-class.md)|Représente un vecteur court de 2 `double` valeurs.|  
|[double_3, classe](double-3-class.md)|Représente un vecteur court 3 `double` valeurs.|  
|[double_4, classe](double-4-class.md)|Représente un vecteur court de 4 `double` valeurs.|  
|[float_2, classe](float-2-class.md)|Représente un vecteur court de 2 `float` valeurs.|  
|[float_3, classe](float-3-class.md)|Représente un vecteur court 3 `float` valeurs.|  
|[float_4, classe](float-4-class.md)|Représente un vecteur court de 4 `float` valeurs.|  
|[int_2, classe](int-2-class.md)|Représente un vecteur court de 2 `int` valeurs.|  
|[int_3, classe](int-3-class.md)|Représente un vecteur court 3 `int` valeurs.|  
|[int_4, classe](int-4-class.md)|Représente un vecteur court de 4 `int` valeurs.|  
|[norm_2, classe](norm-2-class.md)|Représente un vecteur court de 2 `norm` valeurs.|  
|[norm_3, classe](norm-3-class.md)|Représente un vecteur court 3 `norm` valeurs.|  
|[norm_4, classe](norm-4-class.md)|Représente un vecteur court de 4 `norm` valeurs.|  
|[uint_2, classe](uint-2-class.md)|Représente un vecteur court de 2 `uint` valeurs.|  
|[uint_3, classe](uint-3-class.md)|Représente un vecteur court 3 `uint` valeurs.|  
|[uint_4, classe](uint-4-class.md)|Représente un vecteur court de 4 `uint` valeurs.|  
|[unorm_2, classe](unorm-2-class.md)|Représente un vecteur court de 2 `unorm` valeurs.|  
|[unorm_3, classe](unorm-3-class.md)|Représente un vecteur court 3 `unorm` valeurs.|  
|[unorm_4, classe](unorm-4-class.md)|Représente un vecteur court de 4 `unorm` valeurs.|  
|[Sampler, classe](sampler-class.md)|Représente la configuration de l’échantillon utilisée pour l’échantillonnage de texture.|  
|[Structure de short_vector](short-vector-structure.md)|Fournit une implémentation de base d’un vecteur court de valeurs.|  
|[Structure de short_vector_traits](short-vector-traits-structure.md)|Offre pour la récupération de la longueur et le type d’un vecteur court.|  
|[texture_view, classe](texture-view-class.md)|Fournit l’accès en lecture et écriture à une texture.|  
  
### <a name="functions"></a>Fonctions  
  
|Nom|Description|  
|----------|-----------------|  
|[Copy (fonction)](concurrency-graphics-namespace-functions.md#copy)|Surchargé. Copie le contenu de la texture source dans la mémoire tampon hôte de destination.|  
|[copy_async, fonction](concurrency-graphics-namespace-functions.md#copy_async)|Surchargé. Copie le contenu de la texture de la source de façon asynchrone dans la mémoire tampon hôte de destination.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_graphics.h  
  
 **Espace de noms :** Concurrency  
  
## <a name="see-also"></a>Voir aussi  
 [Accès concurrentiel Namespace (C++ AMP)](concurrency-namespace-cpp-amp.md)

