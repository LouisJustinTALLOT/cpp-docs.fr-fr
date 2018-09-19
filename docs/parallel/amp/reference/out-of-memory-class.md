---
title: out_of_memory (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b57e27647f61b551f8ea5c2770290e1ae9627014
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070916"
---
# <a name="outofmemory-class"></a>out_of_memory (classe)
Exception levée lorsqu’une méthode échoue en raison d’un manque de mémoire système ou périphérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[out_of_memory, constructeur](#ctor)|Initialise une nouvelle instance de la classe `out_of_memory`.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** amprt.h  
  
 **Espace de noms :** Concurrency  
## <a name="ctor"></a> out_of_memory) 

 Initialise une nouvelle instance de la classe.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>Paramètres  
*_Message*<br/>
Description de l'erreur.  
  
### <a name="return-value"></a>Valeur de retour  
 Nouvelle instance de la classe `out_of_memory`.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
