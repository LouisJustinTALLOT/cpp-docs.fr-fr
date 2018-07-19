---
title: _com_ptr_t, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb343431a52df9fae32bb17f3303738c04385cf5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942685"
---
# <a name="comptrt-class"></a>_com_ptr_t, classe
**Section spécifique à Microsoft**  
  
 Un objet `_com_ptr_t` encapsule un pointeur d'interface COM et est appelé un pointeur « intelligent ». Cette classe de modèle gère l’allocation des ressources et la désallocation via des appels de fonction à la `IUnknown` fonctions membres : `QueryInterface`, `AddRef`, et `Release`.  
  
 Un pointeur intelligent est généralement référencé par la définition de typedef fournie par la macro _COM_SMARTPTR_TYPEDEF. Cette macro accepte un nom d'interface et l'IID et déclare une spécialisation de `_com_ptr_t` avec le nom de l'interface plus un suffixe `Ptr`. Exemple :  
  
```cpp 
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 déclare le `_com_ptr_t` spécialisation `IMyInterfacePtr`.  
  
 Un ensemble de [modèles de fonction](../cpp/relational-function-templates.md), pas les membres de ce modèle de classe, les comparaisons de prise en charge avec un pointeur intelligent sur le côté droit de l’opérateur de comparaison.  
  
### <a name="construction"></a>Construction  
  
|||  
|-|-|  
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Construit un objet `_com_ptr_t`.|  
  
### <a name="low-level-operations"></a>Opérations de bas niveau  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|Appelle le `AddRef` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|  
|[Attacher](../cpp/com-ptr-t-attach.md)|Encapsule un pointeur d'interface brut du type de ce pointeur intelligent.|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crée une nouvelle instance d’un objet doté d’un `CLSID` ou `ProgID`.|  
|[Détacher](../cpp/com-ptr-t-detach.md)|Extrait et retourne le pointeur d'interface encapsulé.|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|S’attache à une instance existante d’un objet doté d’un `CLSID` ou `ProgID`.|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Retourne le pointeur d'interface encapsulé.|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Appelle le `QueryInterface` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|  
|[Version release](../cpp/com-ptr-t-release.md)|Appelle le `Release` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[opérateur =](../cpp/com-ptr-t-operator-equal.md)|Assigne une nouvelle valeur à un objet `_com_ptr_t` existant.|  
|[les opérateurs ==, ! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Comparer l’objet pointeur intelligent vers un autre pointeur intelligent, le pointeur d’interface brut, ou NULL.|  
|[Extracteurs](../cpp/com-ptr-t-extractors.md)|Récupérez le pointeur d'interface COM encapsulé.|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<comip.h >  
  
 **Lib :** comsuppw.lib ou comsuppwd.lib (voir [/Zc : wchar_t (wchar_t est un Type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)  
  
## <a name="see-also"></a>Voir aussi  
 [Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)