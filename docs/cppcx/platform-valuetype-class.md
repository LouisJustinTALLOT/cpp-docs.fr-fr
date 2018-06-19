---
title: Platform::ValueType (classe) | Documents Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1994aa6445c67bae138a51f1d3eebb2a54f9b17d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088204"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType (classe)
Classe de base pour les instances de types de valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Méthodes publiques  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Retourne une représentation sous forme de chaîne de l’objet. Hérité de [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Notes  
 La classe ValueType est utilisée pour construire des types valeur. ValueType est dérivée d’Object, qui a des membres de base. Toutefois, le compilateur détache ces membres de base des types valeur qui sont dérivés de la classe ValueType. Le compilateur réattache ces membres de base lorsqu’un type valeur est boxed.  
  
### <a name="requirements"></a>Spécifications  
 **Minimum pris en charge le client :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  

## <a name="tostring"></a> ValueType::ToString (méthode)
Retourne une représentation sous forme de chaîne de l’objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Platform::String qui représente la valeur.  
    
## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)