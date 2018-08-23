---
title: Platform::ValueType, classe | Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12766e81ddd90b257830b6bf5adefd2562781d9e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611045"
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
|[ValueType::ToString](#tostring)|Retourne une représentation sous forme de chaîne de l’objet. Héritée de [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Notes  
 La classe ValueType est utilisée pour construire des types valeur. ValueType est dérivée d’Object, qui a des membres de base. Toutefois, le compilateur détache ces membres de base des types valeur qui sont dérivés de la classe ValueType. Le compilateur réattache ces membres de base lorsqu’un type valeur est boxed.  
  
### <a name="requirements"></a>Configuration requise  
 **Minimum de client pris en charge :** Windows 8  
  
 **Minimum de serveur pris en charge :** Windows Server 2012  
  
 **Espace de noms :** Platform  
  
 **Métadonnées :** platform.winmd  

## <a name="tostring"></a> ValueType::ToString, méthode
Retourne une représentation sous forme de chaîne de l’objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Platform::String qui représente la valeur.  
    
## <a name="see-also"></a>Voir aussi  
 [Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)