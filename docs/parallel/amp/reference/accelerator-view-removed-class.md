---
title: accelerator_view_removed, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0426dd44cfcb8f655f3981802dfe23adcd436a0d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688152"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed, classe
Exception levée lorsqu’un appel de DirectX sous-jacent échoue car le mécanisme de détection et de récupération du délai d’attente de Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[accelerator_view_removed, constructeur](#ctor)|Initialise une nouvelle instance de la classe `accelerator_view_removed`.|  

### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|Retourne un code d’erreur HRESULT qui indique la cause de le `accelerator_view` la suppression de l’objet.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** amprt.h  
  
 **Espace de noms :** Concurrency  

## <a name="ctor"></a> accelerator_view_removed 

Initialise une nouvelle instance de la [accelerator_view_removed](accelerator-view-removed-class.md) classe.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>Paramètres  
 `_Message`  
 Description de l'erreur.  
  
 `_View_removed_reason`  
 Un code d’erreur HRESULT qui indique la cause de la suppression de la `accelerator_view` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Une nouvelle instance de la classe accelerator_view_removed.  
  
## <a name="get_view_removed_reason_method"></a> get_view_removed_reason 

Retourne un code d’erreur HRESULT qui indique la cause de le `accelerator_view` la suppression de l’objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
