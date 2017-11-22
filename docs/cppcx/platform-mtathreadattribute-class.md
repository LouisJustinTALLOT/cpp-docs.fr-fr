---
title: Platform::MTAThreadAttribute (classe) | Documents Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs: C++
helpviewer_keywords: Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 6c45256272f7d72dd1da6b6486f9358eaf062b8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute (classe)
Indique que le modèle de thread d'une application est un modèle MTA (MultiThreaded Apartment).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
public ref class MTAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[MTAThreadAttribute constructeur 1](#ctor) constructeur|Initialise une nouvelle instance de la classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
 L’attribut MTAThreadAttribute hérite [Platform::Object, classe](../cppcx/platform-object-class.md). MTAThreadAttribute surcharge ou possède également les membres suivants :  
  
|Nom|Description|  
|----------|-----------------|  
|[MTAThreadAttribute::Equals](#equals)|Détermine si l'objet spécifié est identique à l'objet actuel.|  
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|  
|[MTAThreadAttribute::ToString](#tostring)|Retourne une chaîne qui représente l'objet actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Platform`  
  
### <a name="requirements"></a>Spécifications  
 **Métadonnées :** platform.winmd  
  
 **Espace de noms :** Platform  



## <a name="ctor"></a>MTAThreadAttribute (constructeur)
Initialise une nouvelle instance de la classe MTAThreadAttribute.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:MTAThreadAttribute()  
```  
  


## <a name="equals"></a>MTAThreadAttribute::Equals
Détermine si l'objet spécifié est identique à l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Paramètres  
 obj  
 Objet à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets sont égaux ; sinon `false`.  
  


## <a name="gethashcode"></a>MTAThreadAttribute::GetHashCode
Retourne le code de hachage de cette instance.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Code de hachage de cette instance.  
  


## <a name="tostring"></a>MTAThreadAttribute::ToString
Retourne une chaîne qui représente l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne qui représente l'objet actuel.  
    
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)