---
title: unorm, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e235930b73c4e9c2bc110d142ad734669f9c6ccc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695679"
---
# <a name="unorm-class"></a>unorm, classe
Représente un nombre unorm. Chaque élément est flottante point nombre dans la plage [0.0f, 1.0f].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class unorm;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[unorm, constructeur](#ctor)|Surchargé. Constructeur par défaut. Initialiser à 0.0f.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|unorm::operator--||  
|unorm::operator float|Opérateur de conversion. Convertir le nombre d’unorm flottante valeur du point.|  
|unorm::operator * =||  
|/ = unorm::operator||  
|unorm::operator ++||  
|unorm::operator +=||  
|unorm::operator =||  
|unorm::operator =||  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `unorm`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_short_vectors.h  
  
 **Namespace :** Concurrency::graphics  
  
##  <a name="ctor"></a> unorm 

 Constructeur par défaut. Initialiser à 0.0f.  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Paramètres  
 `_V`  
 La valeur utilisée pour initialiser.  
  
 `_Other`  
 L’objet de la norme utilisée pour initialiser.  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)
